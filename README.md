<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5, user-scalable=yes" />
    <title>مدرستي - نظام إدارة المدارس</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet" />
    <style>
        /* ===== RESET & VARIABLES ===== */
        :root {
            --primary: #6C63FF;
            --primary-dark: #4F46E5;
            --primary-light: #a78bfa;
            --secondary: #f7971e;
            --success: #06d6a0;
            --danger: #ff6b6b;
            --gray-100: #f8f9fe;
            --gray-200: #eef2f7;
            --gray-300: #d0d4e0;
            --gray-400: #b0b0c8;
            --gray-500: #7a7a9a;
            --gray-600: #4a4a6a;
            --gray-700: #2a2a4a;
            --gray-800: #1a1a2e;
            --shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
            --shadow-hover: 0 8px 35px rgba(0, 0, 0, 0.1);
            --radius: 16px;
            --radius-sm: 10px;
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            --font-base: clamp(14px, 1.2vw, 18px);
            --font-sm: clamp(12px, 1vw, 14px);
            --font-lg: clamp(18px, 2vw, 26px);
            --font-xl: clamp(24px, 3vw, 36px);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Tajawal', sans-serif;
            background: #f4f7fc;
            color: var(--gray-800);
            display: flex;
            min-height: 100vh;
            overflow-x: hidden;
            font-size: var(--font-base);
        }

        /* ===== SCROLLBAR ===== */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: var(--gray-200);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--primary);
            border-radius: 10px;
        }

        /* ===== REMOVE NUMBER ARROWS ===== */
        input[type=number]::-webkit-inner-spin-button,
        input[type=number]::-webkit-outer-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }
        input[type=number] {
            -moz-appearance: textfield;
        }

        /* ===== GLOBAL INPUTS ===== */
        input,
        select,
        textarea {
            border: 2px solid var(--gray-300) !important;
            border-radius: var(--radius-sm) !important;
            padding: 10px 14px !important;
            font-family: 'Tajawal', sans-serif;
            font-size: var(--font-base) !important;
            width: 100%;
            transition: var(--transition);
            background: #fff;
            color: var(--gray-800);
        }
        input:focus,
        select:focus,
        textarea:focus {
            border-color: var(--primary) !important;
            outline: none;
            box-shadow: 0 0 0 4px rgba(108, 99, 255, 0.12) !important;
        }
        input[type="date"] {
            min-width: 130px;
        }
        textarea {
            resize: vertical;
            min-height: 60px;
        }

        /* ===== SIDEBAR (Responsive) ===== */
        .sidebar {
            width: 280px;
            min-height: 100vh;
            background: linear-gradient(180deg, #0f0c29, #1a1a3e, #24243e);
            color: #fff;
            padding: 20px 12px 20px 0;
            display: flex;
            flex-direction: column;
            position: sticky;
            top: 0;
            height: 100vh;
            overflow-y: auto;
            box-shadow: 4px 0 25px rgba(0, 0, 0, 0.2);
            z-index: 100;
            transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1);
            flex-shrink: 0;
        }
        .sidebar-brand {
            padding: 0 16px 16px 16px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .sidebar-brand .brand-icon {
            width: 44px;
            height: 44px;
            min-width: 44px;
            background: linear-gradient(135deg, #f7971e, #ffd200);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            color: var(--gray-800);
            box-shadow: 0 4px 12px rgba(255, 210, 0, 0.3);
        }
        .sidebar-brand .brand-text h2 {
            font-size: clamp(18px, 2vw, 24px);
            font-weight: 900;
            background: linear-gradient(to right, #ffd200, #f7971e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
        }
        .sidebar-brand .brand-text small {
            font-size: var(--font-sm);
            color: rgba(255, 255, 255, 0.4);
            -webkit-text-fill-color: rgba(255, 255, 255, 0.4);
        }
        .sidebar-nav {
            flex: 1;
            padding: 0 4px;
        }
        .sidebar-nav .nav-label {
            font-size: var(--font-sm);
            text-transform: uppercase;
            letter-spacing: 1px;
            color: rgba(255, 255, 255, 0.2);
            padding: 0 14px;
            margin: 16px 0 6px 0;
            font-weight: 700;
        }
        .sidebar-nav .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 14px;
            margin: 2px 0;
            border-radius: var(--radius-sm);
            color: rgba(255, 255, 255, 0.6);
            font-size: clamp(13px, 1.1vw, 16px);
            font-weight: 500;
            transition: var(--transition);
            cursor: pointer;
            border: none;
            background: transparent;
            width: 100%;
            text-align: right;
        }
        .sidebar-nav .nav-item i {
            width: 20px;
            font-size: 16px;
            text-align: center;
            color: rgba(255, 255, 255, 0.3);
            transition: var(--transition);
        }
        .sidebar-nav .nav-item:hover {
            background: rgba(255, 255, 255, 0.06);
            color: #fff;
        }
        .sidebar-nav .nav-item:hover i {
            color: #ffd200;
        }
        .sidebar-nav .nav-item.active {
            background: rgba(108, 99, 255, 0.25);
            color: #fff;
            box-shadow: inset 3px 0 0 var(--primary);
        }
        .sidebar-nav .nav-item.active i {
            color: #ffd200;
        }
        .sidebar-nav .nav-item .badge {
            margin-right: auto;
            background: linear-gradient(135deg, #f7971e, #ffd200);
            color: var(--gray-800);
            font-size: var(--font-sm);
            font-weight: 800;
            padding: 0 10px;
            border-radius: 20px;
            letter-spacing: 0.3px;
        }
        .sidebar-footer {
            padding: 12px 14px 0 14px;
            border-top: 1px solid rgba(255, 255, 255, 0.06);
            margin-top: 6px;
        }
        .sidebar-footer .nav-item {
            color: rgba(255, 255, 255, 0.4);
        }
        .sidebar-footer .nav-item:hover {
            color: var(--danger);
            background: rgba(255, 107, 107, 0.1);
        }
        .sidebar-footer .nav-item:hover i {
            color: var(--danger);
        }
        .logout-btn {
            background: linear-gradient(135deg, #ff6b6b, #dc2626) !important;
            color: #fff !important;
            border-radius: 30px !important;
            margin-top: 8px !important;
            padding: 12px 18px !important;
            font-weight: 700 !important;
            box-shadow: 0 4px 15px rgba(255, 107, 107, 0.25);
        }
        .logout-btn:hover {
            transform: scale(1.02);
            box-shadow: 0 6px 25px rgba(255, 107, 107, 0.4) !important;
        }
        .logout-btn i {
            color: #fff !important;
        }

        /* ===== MAIN CONTENT ===== */
        .main-content {
            flex: 1;
            padding: clamp(16px, 2.5vw, 35px);
            min-width: 0;
            width: 100%;
        }

        /* ===== TOP HEADER ===== */
        .top-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: clamp(20px, 3vw, 35px);
        }
        .top-header .page-title h1 {
            font-size: var(--font-xl);
            font-weight: 900;
            color: var(--gray-800);
        }
        .top-header .page-title h1 span {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .top-header .page-title p {
            font-size: var(--font-base);
            color: var(--gray-500);
            font-weight: 400;
            margin-top: 2px;
        }
        .top-header .header-actions {
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }
        .top-header .datetime {
            display: flex;
            align-items: center;
            gap: 10px;
            background: #fff;
            padding: 6px 16px 6px 12px;
            border-radius: 30px;
            box-shadow: var(--shadow);
            border: 1px solid var(--gray-200);
            font-size: var(--font-sm);
            font-weight: 500;
            color: var(--gray-700);
        }
        .top-header .datetime i {
            color: var(--primary);
            font-size: 14px;
        }
        .top-header .datetime .time {
            font-weight: 700;
            color: var(--gray-800);
        }
        .top-header .datetime .date {
            color: var(--gray-500);
        }
        .top-header .header-actions .user-avatar {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-weight: 800;
            font-size: 18px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(108, 99, 255, 0.3);
            transition: var(--transition);
            flex-shrink: 0;
        }
        .top-header .header-actions .user-avatar:hover {
            transform: scale(1.05);
        }
        .menu-toggle {
            display: none;
            background: none;
            border: none;
            font-size: 28px;
            color: var(--gray-800);
            cursor: pointer;
            padding: 4px 10px;
            border-radius: var(--radius-sm);
            transition: var(--transition);
            flex-shrink: 0;
        }
        .menu-toggle:hover {
            background: rgba(108, 99, 255, 0.08);
            color: var(--primary);
        }
        .sidebar-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.4);
            z-index: 98;
            backdrop-filter: blur(4px);
        }
        .sidebar-overlay.active {
            display: block;
        }

        /* ===== PAGE SYSTEM ===== */
        .page-container {
            display: block;
        }
        .page {
            display: none;
            animation: fadeUp 0.35s ease forwards;
        }
        .page.active-page {
            display: block;
        }
        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(16px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ===== STATS CARDS ===== */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(min(160px, 100%), 1fr));
            gap: clamp(14px, 2vw, 22px);
            margin-bottom: clamp(25px, 3vw, 40px);
        }
        .stat-card {
            background: #fff;
            border-radius: var(--radius);
            padding: clamp(16px, 1.8vw, 24px);
            box-shadow: var(--shadow);
            border: 1px solid rgba(0, 0, 0, 0.02);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
        }
        .stat-card:nth-child(1)::before {
            background: linear-gradient(90deg, var(--primary), var(--primary-light));
        }
        .stat-card:nth-child(2)::before {
            background: linear-gradient(90deg, #f7971e, #ffd200);
        }
        .stat-card:nth-child(3)::before {
            background: linear-gradient(90deg, var(--success), #48c9b0);
        }
        .stat-card:nth-child(4)::before {
            background: linear-gradient(90deg, var(--danger), #ff8a8a);
        }
        .stat-card:nth-child(5)::before {
            background: linear-gradient(90deg, #4D96FF, #6fc3ff);
        }
        .stat-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-hover);
        }
        .stat-card .stat-top {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
        }
        .stat-card .stat-icon {
            width: 44px;
            height: 44px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            color: #fff;
            flex-shrink: 0;
        }
        .stat-card:nth-child(1) .stat-icon {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
        }
        .stat-card:nth-child(2) .stat-icon {
            background: linear-gradient(135deg, #f7971e, #ffd200);
            color: var(--gray-800);
        }
        .stat-card:nth-child(3) .stat-icon {
            background: linear-gradient(135deg, var(--success), #059669);
        }
        .stat-card:nth-child(4) .stat-icon {
            background: linear-gradient(135deg, var(--danger), #dc2626);
        }
        .stat-card:nth-child(5) .stat-icon {
            background: linear-gradient(135deg, #4D96FF, #2563eb);
        }
        .stat-card .stat-number {
            font-size: clamp(24px, 3vw, 36px);
            font-weight: 900;
            margin-top: 8px;
            color: var(--gray-800);
        }
        .stat-card .stat-label {
            font-size: var(--font-sm);
            color: var(--gray-500);
            font-weight: 500;
            margin-top: 2px;
        }

        /* ===== TABLE CARD ===== */
        .table-card {
            background: #fff;
            border-radius: var(--radius);
            padding: clamp(16px, 2vw, 26px);
            box-shadow: var(--shadow);
            border: 1px solid rgba(0, 0, 0, 0.02);
            margin-bottom: clamp(20px, 2.5vw, 30px);
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }
        .table-card h3 {
            font-size: var(--font-lg);
            font-weight: 900;
            color: var(--gray-800);
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .table-card h3 i {
            font-size: clamp(18px, 1.8vw, 24px);
        }
        .table-card .toolbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 14px;
        }
        .table-card table {
            width: 100%;
            border-collapse: collapse;
            font-size: var(--font-sm);
            min-width: 480px;
        }
        .table-card table th {
            text-align: right;
            padding: 10px 8px;
            font-weight: 700;
            color: var(--gray-600);
            font-size: var(--font-sm);
            letter-spacing: 0.3px;
            border-bottom: 2px solid var(--gray-300);
            white-space: nowrap;
        }
        .table-card table td {
            padding: 10px 8px;
            border-bottom: 1px solid var(--gray-200);
            color: var(--gray-700);
            word-break: break-word;
        }
        .table-card table tr:last-child td {
            border-bottom: none;
        }
        .table-card table tr:hover td {
            background: var(--gray-100);
        }

        /* ===== BUTTONS ===== */
        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: #fff;
            border: none;
            padding: 8px 18px;
            border-radius: 30px;
            font-family: 'Tajawal', sans-serif;
            font-weight: 600;
            font-size: var(--font-sm);
            cursor: pointer;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            gap: 6px;
            white-space: nowrap;
        }
        .btn-primary:hover {
            transform: scale(1.03);
            box-shadow: 0 6px 20px rgba(108, 99, 255, 0.3);
        }
        .btn-primary.danger {
            background: linear-gradient(135deg, var(--danger), #dc2626);
        }
        .btn-primary.danger:hover {
            box-shadow: 0 6px 20px rgba(255, 107, 107, 0.3);
        }
        .btn-primary.success {
            background: linear-gradient(135deg, var(--success), #059669);
        }
        .btn-primary.success:hover {
            box-shadow: 0 6px 20px rgba(6, 214, 160, 0.3);
        }
        .btn-primary.warning {
            background: linear-gradient(135deg, #f7971e, #e65100);
        }
        .btn-primary.warning:hover {
            box-shadow: 0 6px 20px rgba(247, 151, 30, 0.3);
        }
        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
            padding: 8px 18px;
            border-radius: 30px;
            font-family: 'Tajawal', sans-serif;
            font-weight: 600;
            font-size: var(--font-sm);
            cursor: pointer;
            transition: var(--transition);
        }
        .btn-outline:hover {
            background: var(--primary);
            color: #fff;
        }
        .btn-sm {
            padding: 4px 12px;
            font-size: var(--font-sm);
        }

        /* ===== BADGES ===== */
        .badge-status {
            font-size: var(--font-sm);
            font-weight: 700;
            padding: 2px 12px;
            border-radius: 20px;
            display: inline-block;
        }
        .badge-status.active {
            background: #e8f5e9;
            color: #2e7d32;
        }
        .badge-status.inactive {
            background: #ffebee;
            color: #c62828;
        }
        .badge-status.pending {
            background: #fff3e0;
            color: #e65100;
        }

        /* ===== MODAL ===== */
        .modal-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(6px);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 16px;
        }
        .modal-overlay.open {
            display: flex;
        }
        .modal {
            background: #fff;
            border-radius: var(--radius);
            padding: clamp(20px, 3vw, 35px);
            max-width: 600px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
            animation: fadeUp 0.3s ease;
        }
        .modal h2 {
            font-size: var(--font-lg);
            font-weight: 900;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .modal .form-group {
            margin-bottom: 14px;
        }
        .modal .form-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 4px;
            font-size: var(--font-base);
            color: var(--gray-700);
        }
        .modal .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 14px;
        }
        .modal .modal-actions {
            display: flex;
            gap: 10px;
            margin-top: 18px;
            justify-content: flex-end;
            flex-wrap: wrap;
        }

        /* ===== GRADES TABLE ===== */
        .grade-input {
            width: 50px;
            padding: 4px 2px !important;
            border: 2px solid var(--gray-300) !important;
            border-radius: 6px !important;
            font-size: var(--font-sm) !important;
            font-weight: 700;
            text-align: center;
            background: var(--gray-100);
        }
        .grade-input:focus {
            border-color: var(--primary) !important;
        }
        .grade-total {
            font-weight: 900;
            font-size: clamp(16px, 1.4vw, 20px);
            color: var(--gray-800);
            background: #eef2ff;
            padding: 2px 8px;
            border-radius: 6px;
            display: inline-block;
            min-width: 36px;
        }
        .grade-total.fail {
            color: #dc2626;
            text-decoration: underline wavy #dc2626 2px;
            background: #ffebee;
        }
        .grade-total.pass-high {
            color: #059669;
            background: #e8f5e9;
        }
        .grade-total.pass-mid {
            color: #e65100;
            background: #fff3e0;
        }
        .grades-table-wrap {
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }
        .grades-table-wrap table {
            min-width: 600px;
            border-collapse: collapse;
            width: 100%;
            border: 2px solid var(--gray-300);
        }
        .grades-table-wrap table th {
            background: var(--primary);
            color: #fff;
            border: 2px solid var(--primary-dark);
            padding: 8px 4px;
            text-align: center;
            font-size: var(--font-sm);
            font-weight: 800;
        }
        .grades-table-wrap table td {
            padding: 6px 4px;
            text-align: center;
            border: 2px solid var(--gray-300);
            font-size: var(--font-sm);
        }
        .grades-table-wrap .sub-header th {
            background: var(--primary-dark);
            color: #fff;
            font-size: var(--font-sm);
        }
        .grades-table-wrap .subject-divider {
            border-bottom: 4px solid #f59e0b !important;
        }

        /* ===== ATTENDANCE ===== */
        .attendance-btn {
            padding: 4px 10px;
            border-radius: 20px;
            border: none;
            font-family: 'Tajawal', sans-serif;
            font-weight: 700;
            font-size: var(--font-sm);
            cursor: pointer;
            transition: var(--transition);
            margin: 2px;
        }
        .attendance-btn.present {
            background: #e8f5e9;
            color: #2e7d32;
        }
        .attendance-btn.present:hover {
            background: #2e7d32;
            color: #fff;
        }
        .attendance-btn.absent {
            background: #ffebee;
            color: #c62828;
        }
        .attendance-btn.absent:hover {
            background: #c62828;
            color: #fff;
        }
        .attendance-btn.late {
            background: #fff3e0;
            color: #e65100;
        }
        .attendance-btn.late:hover {
            background: #e65100;
            color: #fff;
        }
        .attendance-btn.leave {
            background: #e3f2fd;
            color: #0d47a1;
        }
        .attendance-btn.leave:hover {
            background: #0d47a1;
            color: #fff;
        }
        .attendance-btn.active-status {
            box-shadow: 0 0 0 2px var(--gray-800);
            transform: scale(1.05);
        }
        .whatsapp-btn {
            background: #25D366;
            color: #fff;
            border: none;
            padding: 3px 10px;
            border-radius: 20px;
            font-size: var(--font-sm);
            cursor: pointer;
            transition: var(--transition);
        }
        .whatsapp-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 12px rgba(37, 211, 102, 0.3);
        }

        /* ===== CALENDAR ===== */
        .calendar {
            direction: ltr;
        }
        .calendar .cal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
            font-weight: 700;
            font-size: var(--font-base);
            color: var(--gray-800);
        }
        .calendar .cal-header button {
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
            color: var(--primary);
            transition: var(--transition);
            padding: 0 8px;
        }
        .calendar .cal-header button:hover {
            transform: scale(1.15);
        }
        .calendar .cal-weekdays {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            text-align: center;
            font-weight: 700;
            color: var(--gray-500);
            font-size: var(--font-sm);
            margin-bottom: 6px;
        }
        .calendar .cal-days {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 4px;
        }
        .calendar .cal-day {
            aspect-ratio: 1 / 1;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 12px;
            font-weight: 600;
            font-size: clamp(14px, 1.2vw, 18px);
            color: var(--gray-800);
            background: var(--gray-100);
            cursor: pointer;
            transition: var(--transition);
            border: 2px solid transparent;
            min-width: 30px;
            min-height: 30px;
        }
        .calendar .cal-day:hover {
            background: #dbeafe;
            transform: scale(1.05);
            border-color: var(--primary-light);
        }
        .calendar .cal-day.today {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: #fff;
            border-color: var(--primary-dark);
            font-weight: 900;
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(108, 99, 255, 0.3);
        }
        .calendar .cal-day.other-month {
            color: var(--gray-400);
            background: #f8fafc;
        }
        .calendar .cal-day-weekend {
            color: var(--danger);
            background: #fee2e2;
            border-color: #fca5a5;
        }

        /* ===== CHARTS ===== */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(min(280px, 100%), 1fr));
            gap: clamp(16px, 2vw, 25px);
            margin-bottom: clamp(20px, 3vw, 35px);
        }
        .dashboard-grid .card {
            background: #fff;
            border-radius: var(--radius);
            padding: clamp(16px, 2vw, 26px);
            box-shadow: var(--shadow);
            border: 1px solid rgba(0, 0, 0, 0.02);
            transition: var(--transition);
        }
        .dashboard-grid .card:hover {
            box-shadow: var(--shadow-hover);
        }
        .dashboard-grid .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 14px;
            border-right: 6px solid var(--primary);
            padding-right: 12px;
            border-radius: 0 6px 6px 0;
            background: linear-gradient(to right, transparent 95%, #eef2ff);
        }
        .dashboard-grid .card-header h3 {
            font-size: var(--font-base);
            font-weight: 800;
            color: var(--gray-800);
        }
        .chart-bars {
            display: flex;
            align-items: flex-end;
            justify-content: space-around;
            height: 120px;
            gap: 6px;
            padding-top: 8px;
        }
        .chart-bar-wrapper {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            flex: 1;
        }
        .chart-bar {
            width: 100%;
            max-width: 36px;
            border-radius: 4px 4px 2px 2px;
            min-height: 8px;
            transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        .chart-bar-label {
            font-size: var(--font-sm);
            font-weight: 600;
            color: var(--gray-500);
        }
        .chart-bar-value {
            font-size: var(--font-sm);
            font-weight: 700;
            color: var(--gray-800);
            background: var(--gray-100);
            padding: 0 6px;
            border-radius: 8px;
        }
        .chart-colors-1 {
            background: linear-gradient(180deg, var(--primary), var(--primary-light));
        }
        .chart-colors-2 {
            background: linear-gradient(180deg, #f7971e, #ffd200);
        }
        .chart-colors-3 {
            background: linear-gradient(180deg, var(--success), #48c9b0);
        }
        .chart-colors-4 {
            background: linear-gradient(180deg, var(--danger), #ff8a8a);
        }
        .chart-colors-5 {
            background: linear-gradient(180deg, #4D96FF, #6fc3ff);
        }
        .chart-colors-6 {
            background: linear-gradient(180deg, #a855f7, #c084fc);
        }
        .chart-colors-7 {
            background: linear-gradient(180deg, #f472b6, #f9a8d4);
        }

        /* ===== LEVEL CHART ===== */
        .level-chart {
            display: flex;
            flex-direction: column;
            gap: 8px;
            padding: 4px 0;
        }
        .level-row {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .level-label {
            min-width: 50px;
            font-weight: 700;
            font-size: var(--font-sm);
            color: var(--gray-700);
        }
        .level-bar-track {
            flex: 1;
            height: 24px;
            background: var(--gray-200);
            border-radius: 12px;
            overflow: hidden;
            position: relative;
        }
        .level-bar-fill {
            height: 100%;
            border-radius: 12px;
            transition: width 1s cubic-bezier(0.34, 1.56, 0.64, 1);
            width: 0%;
            display: flex;
            align-items: center;
            justify-content: flex-end;
            padding-right: 8px;
            font-weight: 700;
            font-size: var(--font-sm);
            color: #fff;
            text-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
        }
        .level-bar-fill.excellent {
            background: linear-gradient(90deg, #059669, #34d399);
        }
        .level-bar-fill.good {
            background: linear-gradient(90deg, #2563eb, #60a5fa);
        }
        .level-bar-fill.average {
            background: linear-gradient(90deg, #f7971e, #fbbf24);
        }
        .level-bar-fill.weak {
            background: linear-gradient(90deg, #dc2626, #f87171);
        }
        .level-count {
            font-weight: 700;
            font-size: var(--font-sm);
            color: var(--gray-700);
            min-width: 30px;
            text-align: center;
        }

        /* ===== SCHEDULE ===== */
        .schedule-table {
            width: 100%;
            border-collapse: collapse;
            font-size: var(--font-sm);
            min-width: 480px;
        }
        .schedule-table th {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: #fff;
            padding: 10px 6px;
            text-align: center;
            font-weight: 800;
            font-size: var(--font-sm);
            border: 2px solid var(--primary-dark);
        }
        .schedule-table td {
            padding: 8px 4px;
            text-align: center;
            border: 2px solid var(--gray-300);
            font-size: var(--font-sm);
        }
        .schedule-table .period-label {
            font-weight: 700;
            color: var(--gray-700);
            background: var(--gray-100);
        }
        .schedule-table .empty-cell {
            color: var(--gray-400);
        }
        .schedule-table .subject-cell {
            font-weight: 600;
            background: #f0f4ff;
        }
        .schedule-table .day-header {
            background: linear-gradient(135deg, #f7971e, #ffd200);
            color: var(--gray-800);
            font-weight: 900;
            font-size: var(--font-base);
            border-color: #e6b800;
        }
        .schedule-table .day-header.weekend {
            background: linear-gradient(135deg, var(--danger), #dc2626);
            color: #fff;
        }
        .schedule-filter {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            align-items: center;
            margin-bottom: 14px;
        }
        .schedule-filter select {
            padding: 8px 12px;
            border: 2px solid var(--gray-300) !important;
            border-radius: var(--radius-sm) !important;
            font-family: 'Tajawal', sans-serif;
            font-size: var(--font-sm);
            background: #fff;
            min-width: 120px;
        }

        /* ===== FILTER ROW ===== */
        .filter-row {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            align-items: center;
            margin-bottom: 14px;
        }
        .filter-row select,
        .filter-row input {
            padding: 8px 12px;
            border: 2px solid var(--gray-300) !important;
            border-radius: var(--radius-sm) !important;
            font-family: 'Tajawal', sans-serif;
            font-size: var(--font-sm);
            background: #fff;
            min-width: 120px;
        }

        /* ===== ATTENDANCE SEARCH ===== */
        .attendance-search {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            align-items: center;
            margin-bottom: 14px;
            padding: 12px 14px;
            background: var(--gray-100);
            border-radius: var(--radius);
            border: 2px solid var(--gray-200);
        }
        .attendance-search input,
        .attendance-search select {
            padding: 8px 12px;
            border: 2px solid var(--gray-300) !important;
            border-radius: var(--radius-sm) !important;
            font-family: 'Tajawal', sans-serif;
            font-size: var(--font-sm);
            background: #fff;
            min-width: 120px;
        }
        .attendance-search .search-label {
            font-weight: 600;
            color: var(--gray-600);
            font-size: var(--font-sm);
            display: flex;
            align-items: center;
            gap: 4px;
        }

        /* ===== ATTENDANCE SUMMARY ===== */
        .attendance-summary {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(70px, 1fr));
            gap: 8px;
            margin-bottom: 14px;
            padding: 10px 12px;
            background: #fff;
            border-radius: var(--radius);
            border: 2px solid var(--gray-200);
        }
        .attendance-summary .stat-box {
            text-align: center;
            padding: 4px;
        }
        .attendance-summary .stat-box .num {
            font-size: clamp(18px, 2vw, 26px);
            font-weight: 900;
        }
        .attendance-summary .stat-box .label {
            font-size: var(--font-sm);
            color: var(--gray-500);
            font-weight: 500;
        }
        .attendance-summary .stat-box.present-box .num {
            color: #2e7d32;
        }
        .attendance-summary .stat-box.absent-box .num {
            color: #c62828;
        }
        .attendance-summary .stat-box.late-box .num {
            color: #e65100;
        }
        .attendance-summary .stat-box.leave-box .num {
            color: #0d47a1;
        }
        .attendance-summary .stat-box.total-box .num {
            color: var(--gray-800);
        }
        .attendance-summary .stat-box.pct-box .num {
            color: var(--primary);
        }
        .day-status-badge {
            font-size: var(--font-sm);
            font-weight: 700;
            padding: 1px 6px;
            border-radius: 10px;
            display: inline-block;
            min-width: 24px;
        }
        .day-status-badge.present {
            background: #e8f5e9;
            color: #2e7d32;
        }
        .day-status-badge.absent {
            background: #ffebee;
            color: #c62828;
        }
        .day-status-badge.late {
            background: #fff3e0;
            color: #e65100;
        }
        .day-status-badge.leave {
            background: #e3f2fd;
            color: #0d47a1;
        }

        /* ===== ABSENCE TRACKING ===== */
        .absence-warning {
            background: #fff3cd;
            border: 2px solid #ffc107;
            border-radius: var(--radius-sm);
            padding: 10px 14px;
            margin: 8px 0;
            color: #856404;
            font-weight: 600;
            font-size: var(--font-sm);
        }
        .absence-warning.danger {
            background: #f8d7da;
            border-color: #dc3545;
            color: #721c24;
        }
        .absence-limit-set {
            display: flex;
            gap: 10px;
            align-items: center;
            flex-wrap: wrap;
            margin-bottom: 12px;
            font-size: var(--font-sm);
        }
        .absence-limit-set input {
            width: 70px;
            padding: 6px 8px !important;
            text-align: center;
        }
        .absence-warn-badge {
            display: inline-block;
            background: #dc3545;
            color: #fff;
            border-radius: 50%;
            padding: 0 6px;
            font-size: 10px;
            font-weight: 800;
            margin-right: 4px;
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0%,
            100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.15);
            }
        }
        .absence-exceed {
            background: #f8d7da !important;
            border: 2px solid #dc3545 !important;
        }

        /* ===== TAB NAV ===== */
        .tab-nav {
            display: flex;
            gap: 6px;
            margin-bottom: 14px;
            flex-wrap: wrap;
            border-bottom: 2px solid var(--gray-200);
            padding-bottom: 6px;
        }
        .tab-nav .tab-btn {
            padding: 6px 16px;
            border: none;
            background: transparent;
            font-family: 'Tajawal', sans-serif;
            font-weight: 600;
            font-size: var(--font-sm);
            color: var(--gray-500);
            cursor: pointer;
            border-radius: 30px;
            transition: var(--transition);
        }
        .tab-nav .tab-btn:hover {
            background: var(--gray-100);
            color: var(--primary);
        }
        .tab-nav .tab-btn.active {
            background: var(--primary);
            color: #fff;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }

        /* ===== SETTINGS ===== */
        .settings-card {
            max-width: 500px;
            margin: 0 auto;
        }
        .settings-card .form-group {
            margin-bottom: 16px;
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 1024px) {
            .dashboard-grid {
                grid-template-columns: repeat(auto-fit, minmax(min(240px, 100%), 1fr));
            }
        }

        @media (max-width: 768px) {
            .sidebar {
                position: fixed;
                transform: translateX(100%);
                width: 280px;
                z-index: 99;
                box-shadow: 0 0 40px rgba(0, 0, 0, 0.3);
                padding: 16px 8px 16px 0;
            }
            .sidebar.open {
                transform: translateX(0);
            }
            .menu-toggle {
                display: block;
            }
            .sidebar-overlay.active {
                display: block;
            }
            .top-header .page-title h1 {
                font-size: var(--font-lg);
            }
            .top-header .datetime .date {
                display: none;
            }
            .stats-grid {
                grid-template-columns: repeat(auto-fit, minmax(min(140px, 100%), 1fr));
                gap: 10px;
            }
            .stat-card {
                padding: 14px 16px;
            }
            .stat-card .stat-number {
                font-size: clamp(20px, 4vw, 28px);
            }
            .modal .form-row {
                grid-template-columns: 1fr;
            }
            .grades-table-wrap table {
                min-width: 480px;
            }
            .table-card table {
                min-width: 400px;
            }
            .schedule-table {
                min-width: 400px;
            }
        }

        @media (max-width: 480px) {
            .main-content {
                padding: 12px 10px;
            }
            .top-header {
                flex-direction: column;
                align-items: stretch;
                gap: 8px;
            }
            .top-header .header-actions {
                justify-content: space-between;
            }
            .top-header .datetime .time {
                font-size: var(--font-sm);
            }
            .stats-grid {
                grid-template-columns: 1fr 1fr;
                gap: 8px;
            }
            .stat-card {
                padding: 12px 14px;
            }
            .stat-card .stat-number {
                font-size: 20px;
            }
            .stat-card .stat-icon {
                width: 36px;
                height: 36px;
                font-size: 16px;
            }
            .table-card {
                padding: 12px 10px;
            }
            .table-card .toolbar {
                flex-direction: column;
                align-items: stretch;
            }
            .btn-primary {
                width: 100%;
                justify-content: center;
                padding: 10px 16px;
            }
            .filter-row {
                flex-direction: column;
            }
            .filter-row select,
            .filter-row input {
                width: 100%;
            }
            .attendance-search {
                flex-direction: column;
            }
            .attendance-search input,
            .attendance-search select {
                width: 100%;
            }
            .modal {
                padding: 16px;
            }
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            .calendar .cal-day {
                font-size: var(--font-sm);
                min-width: 28px;
                min-height: 28px;
            }
            .schedule-filter {
                flex-direction: column;
                align-items: stretch;
            }
            .schedule-filter select {
                width: 100%;
            }
            .absence-limit-set {
                flex-direction: column;
                align-items: stretch;
            }
            .absence-limit-set input {
                width: 100%;
            }
            .attendance-summary {
                grid-template-columns: repeat(3, 1fr);
            }
            .grades-table-wrap table th,
            .grades-table-wrap table td {
                font-size: 11px;
                padding: 4px 2px;
            }
            .grade-input {
                width: 40px;
                font-size: 12px !important;
                padding: 2px !important;
            }
        }

        @media (max-width: 380px) {
            .stats-grid {
                grid-template-columns: 1fr 1fr;
                gap: 6px;
            }
            .stat-card .stat-number {
                font-size: 17px;
            }
            .stat-card .stat-label {
                font-size: 10px;
            }
            .stat-card .stat-icon {
                width: 30px;
                height: 30px;
                font-size: 14px;
            }
        }

        /* ===== TOAST ===== */
        .toast {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--gray-800);
            color: #fff;
            padding: 10px 24px;
            border-radius: 50px;
            font-size: var(--font-sm);
            font-weight: 500;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
            opacity: 0;
            transition: opacity 0.3s ease, transform 0.3s ease;
            z-index: 9999;
            pointer-events: none;
            direction: rtl;
            text-align: center;
            max-width: 90%;
        }
        .toast.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }
        .toast.success {
            background: #059669;
        }
        .toast.error {
            background: #dc2626;
        }

        /* ===== LOGIN SCREEN ===== */
        .login-screen {
            display: none;
            position: fixed;
            inset: 0;
            background: linear-gradient(135deg, #0f0c29, #1a1a3e, #24243e);
            z-index: 9999;
            justify-content: center;
            align-items: center;
            padding: 16px;
        }
        .login-screen.active {
            display: flex;
        }
        .login-box {
            background: #fff;
            border-radius: 30px;
            padding: clamp(30px, 5vw, 50px);
            max-width: 420px;
            width: 100%;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            text-align: center;
        }
        .login-box .login-icon {
            font-size: clamp(50px, 8vw, 70px);
            color: var(--primary);
            margin-bottom: 12px;
        }
        .login-box h2 {
            font-size: var(--font-xl);
            font-weight: 900;
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .login-box p {
            color: var(--gray-500);
            font-size: var(--font-base);
            margin-bottom: 20px;
        }
        .login-box .form-group {
            margin-bottom: 16px;
            text-align: right;
        }
        .login-box .form-group label {
            display: block;
            font-weight: 600;
            font-size: var(--font-sm);
            color: var(--gray-700);
            margin-bottom: 4px;
        }
        .login-box .form-group input {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid var(--gray-300) !important;
            border-radius: var(--radius-sm) !important;
            font-family: 'Tajawal', sans-serif;
            font-size: var(--font-base);
            transition: var(--transition);
            background: var(--gray-100);
        }
        .login-box .form-group input:focus {
            border-color: var(--primary) !important;
            box-shadow: 0 0 0 4px rgba(108, 99, 255, 0.1);
        }
        .login-box .login-help {
            font-size: var(--font-sm);
            color: var(--gray-500);
            margin-top: -6px;
            margin-bottom: 16px;
            cursor: pointer;
            transition: var(--transition);
        }
        .login-box .login-help:hover {
            color: var(--primary);
            text-decoration: underline;
        }
        .login-box .btn-primary {
            width: 100%;
            padding: 14px;
            font-size: var(--font-base);
            border-radius: 30px;
            justify-content: center;
        }

        /* ===== EMPTY STATE ===== */
        .empty-state {
            text-align: center;
            padding: 30px 16px;
            color: var(--gray-500);
        }
        .empty-state i {
            font-size: 48px;
            color: var(--gray-300);
            margin-bottom: 8px;
        }

        /* ===== YEAR BADGE ===== */
        .year-badge {
            background: rgba(108, 99, 255, 0.1);
            padding: 2px 14px;
            border-radius: 30px;
            font-size: var(--font-sm);
            font-weight: 700;
            color: var(--primary);
            border: 1px solid rgba(108, 99, 255, 0.15);
            display: inline-block;
            white-space: nowrap;
        }

        /* ===== SECTION LIST (Stages) ===== */
        .section-list {
            list-style: none;
            padding: 0;
            margin: 6px 0;
        }
        .section-list li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 6px 10px;
            background: var(--gray-100);
            margin: 4px 0;
            border-radius: var(--radius-sm);
            border: 1px solid var(--gray-200);
            font-size: var(--font-sm);
        }
        .section-list li .remove-section {
            color: var(--danger);
            cursor: pointer;
            font-size: 14px;
            border: none;
            background: none;
            padding: 0 4px;
        }
        .section-list li .remove-section:hover {
            color: #b91c1c;
        }
        .add-section-row {
            display: flex;
            gap: 6px;
            align-items: center;
            margin-top: 6px;
            flex-wrap: wrap;
        }
        .add-section-row input {
            flex: 1;
            min-width: 80px;
        }
        .add-section-row button {
            padding: 6px 14px;
            font-size: var(--font-sm);
        }

        /* ===== SUBJECT INPUT WRAPPER ===== */
        .subject-input-wrapper {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }
        .subject-input-wrapper .or-divider {
            text-align: center;
            color: var(--gray-400);
            font-weight: 700;
            font-size: var(--font-sm);
            position: relative;
        }
        .subject-input-wrapper .or-divider::before,
        .subject-input-wrapper .or-divider::after {
            content: '';
            position: absolute;
            top: 50%;
            width: 30%;
            height: 2px;
            background: var(--gray-200);
        }
        .subject-input-wrapper .or-divider::before {
            right: 0;
        }
        .subject-input-wrapper .or-divider::after {
            left: 0;
        }
    </style>
</head>
<body>

    <!-- ===== TOAST ===== -->
    <div class="toast" id="toast"></div>

    <!-- ===== LOGIN SCREEN ===== -->
    <div class="login-screen active" id="loginScreen">
        <div class="login-box">
            <div class="login-icon"><i class="fas fa-graduation-cap"></i></div>
            <h2>مدرستي</h2>
            <p>نظام إدارة المدارس المتكامل</p>
            <div class="form-group">
                <label>اسم المستخدم</label>
                <input type="text" id="loginUser" value="admin" />
            </div>
            <div class="form-group">
                <label>كلمة المرور</label>
                <input type="password" id="loginPass" value="123" />
            </div>
            <div class="login-help" onclick="showDefaultCredentials()">
                <i class="fas fa-info-circle"></i> نسيت كلمة المرور؟ (القيم الافتراضية: admin / 123)
            </div>
            <button class="btn-primary" onclick="login()"><i class="fas fa-sign-in-alt"></i> دخول</button>
        </div>
    </div>

    <!-- ===== SIDEBAR OVERLAY ===== -->
    <div class="sidebar-overlay" id="sidebarOverlay"></div>

    <!-- ===== SIDEBAR ===== -->
    <aside class="sidebar" id="sidebar">
        <div class="sidebar-brand">
            <div class="brand-icon"><i class="fas fa-graduation-cap"></i></div>
            <div class="brand-text">
                <h2>مدرستي</h2>
                <small>نظام إدارة المدارس</small>
            </div>
        </div>
        <nav class="sidebar-nav">
            <div class="nav-label">القائمة الرئيسية</div>
            <button class="nav-item active" data-page="dashboard"><i class="fas fa-th-large"></i><span>لوحة التحكم</span></button>
            <button class="nav-item" data-page="stages"><i class="fas fa-layer-group"></i><span>المراحل والشعب</span><span class="badge" id="stageBadge">0</span></button>
            <button class="nav-item" data-page="students"><i class="fas fa-user-graduate"></i><span>الطلاب</span><span class="badge" id="studentBadge">0</span></button>
            <button class="nav-item" data-page="teachers"><i class="fas fa-chalkboard-teacher"></i><span>المدرسين</span><span class="badge" id="teacherBadge">0</span></button>
            <button class="nav-item" data-page="subjects"><i class="fas fa-book-open"></i><span>المواد</span><span class="badge" id="subjectBadge">0</span></button>
            <button class="nav-item" data-page="parents"><i class="fas fa-user-friends"></i><span>أولياء الأمور</span></button>
            <div class="nav-label">السجلات</div>
            <button class="nav-item" data-page="grades"><i class="fas fa-pencil-alt"></i><span>سجلات الدرجات</span></button>
            <button class="nav-item" data-page="attendance"><i class="fas fa-calendar-check"></i><span>الحضور</span></button>
            <button class="nav-item" data-page="schedule"><i class="fas fa-table"></i><span>جدول الدروس</span></button>
            <div class="nav-label">الإعدادات</div>
            <button class="nav-item" data-page="settings"><i class="fas fa-cog"></i><span>الإعدادات</span></button>
        </nav>
        <div class="sidebar-footer">
            <button class="nav-item logout-btn" onclick="logout()"><i class="fas fa-sign-out-alt"></i><span>خروج</span></button>
        </div>
    </aside>

    <!-- ===== MAIN ===== -->
    <main class="main-content" id="mainContent">

        <!-- ===== TOP HEADER ===== -->
        <header class="top-header">
            <div class="page-title">
                <div style="display:flex;align-items:center;gap:10px;flex-wrap:wrap;">
                    <button class="menu-toggle" id="menuToggle"><i class="fas fa-bars"></i></button>
                    <h1>مرحباً بك في <span>مدرستي</span></h1>
                    <span class="year-badge"><i class="far fa-calendar-alt" style="margin-left:4px;"></i>2026-2027</span>
                </div>
                <p id="pageSubtitle">نظام إدارة المدارس المتكامل – لوحة التحكم الرئيسية</p>
            </div>
            <div class="header-actions">
                <div class="datetime">
                    <i class="fas fa-clock"></i>
                    <span class="time" id="currentTime">03:48 PM</span>
                    <span class="date" id="currentDate">01/09/2026</span>
                </div>
                <div class="user-avatar" id="userAvatar">أ</div>
            </div>
        </header>

        <!-- ===== PAGE CONTAINER ===== -->
        <div class="page-container">

            <!-- ===== DASHBOARD ===== -->
            <div class="page active-page" id="page-dashboard">
                <section class="stats-grid" id="statsGrid">
                    <div class="stat-card"><div class="stat-top"><div class="stat-icon"><i class="fas fa-layer-group"></i></div></div><div class="stat-number" id="dashStages">0</div><div class="stat-label">المراحل والشعب</div></div>
                    <div class="stat-card"><div class="stat-top"><div class="stat-icon"><i class="fas fa-user-graduate"></i></div></div><div class="stat-number" id="dashStudents">0</div><div class="stat-label">الطلاب</div></div>
                    <div class="stat-card"><div class="stat-top"><div class="stat-icon"><i class="fas fa-chalkboard-teacher"></i></div></div><div class="stat-number" id="dashTeachers">0</div><div class="stat-label">المدرسين</div></div>
                    <div class="stat-card"><div class="stat-top"><div class="stat-icon"><i class="fas fa-book-open"></i></div></div><div class="stat-number" id="dashSubjects">0</div><div class="stat-label">المواد</div></div>
                    <div class="stat-card"><div class="stat-top"><div class="stat-icon"><i class="fas fa-user-friends"></i></div></div><div class="stat-number" id="dashParents">0</div><div class="stat-label">أولياء الأمور</div></div>
                </section>

                <div class="dashboard-grid">
                    <!-- Calendar -->
                    <div class="card">
                        <div class="card-header"><h3><i class="fas fa-calendar-alt" style="color:var(--primary);margin-left:8px;"></i>التقويم</h3></div>
                        <div class="calendar" id="calendar"></div>
                    </div>
                    <!-- Student Distribution -->
                    <div class="card">
                        <div class="card-header"><h3><i class="fas fa-chart-bar" style="color:#f7971e;margin-left:8px;"></i>توزيع الطلاب حسب المرحلة</h3></div>
                        <div class="chart-bars" id="dashChart"></div>
                        <div style="text-align:center;margin-top:6px;font-size:var(--font-sm);color:var(--gray-500);">عدد الطلاب في كل مرحلة</div>
                    </div>
                    <!-- Level Chart -->
                    <div class="card">
                        <div class="card-header"><h3><i class="fas fa-signal" style="color:var(--success);margin-left:8px;"></i>مستوى الطلاب</h3></div>
                        <div class="level-chart" id="levelChart">
                            <div class="level-row"><span class="level-label">ممتاز</span><div class="level-bar-track"><div class="level-bar-fill excellent" id="levelExcellent" style="width:0%;">0</div></div><span class="level-count" id="levelExcellentCount">0</span></div>
                            <div class="level-row"><span class="level-label">جيد جداً</span><div class="level-bar-track"><div class="level-bar-fill good" id="levelGood" style="width:0%;">0</div></div><span class="level-count" id="levelGoodCount">0</span></div>
                            <div class="level-row"><span class="level-label">متوسط</span><div class="level-bar-track"><div class="level-bar-fill average" id="levelAverage" style="width:0%;">0</div></div><span class="level-count" id="levelAverageCount">0</span></div>
                            <div class="level-row"><span class="level-label">ضعيف</span><div class="level-bar-track"><div class="level-bar-fill weak" id="levelWeak" style="width:0%;">0</div></div><span class="level-count" id="levelWeakCount">0</span></div>
                        </div>
                        <div style="text-align:center;margin-top:6px;font-size:var(--font-sm);color:var(--gray-500);">توزيع الطلاب حسب الأداء (متوسط الدرجات)</div>
                    </div>
                </div>

                <div style="background:#fff;border-radius:var(--radius);padding:clamp(16px,2vw,26px);box-shadow:var(--shadow);border:1px solid rgba(0,0,0,0.02);">
                    <h3 style="margin-bottom:8px;font-size:var(--font-base);font-weight:800;"><i class="fas fa-info-circle" style="color:var(--primary);margin-left:8px;"></i>نظرة عامة</h3>
                    <p style="color:var(--gray-500);font-size:var(--font-base);">يمكنك إدارة جميع جوانب المدرسة من خلال القائمة الجانبية. استخدم التقويم لمتابعة الأيام الهامة.</p>
                </div>
            </div>

            <!-- ===== STAGES ===== -->
            <div class="page" id="page-stages">
                <div class="table-card">
                    <div class="toolbar">
                        <h3><i class="fas fa-layer-group" style="color:var(--primary);margin-left:8px;"></i>المراحل والشعب</h3>
                        <button class="btn-primary" onclick="openStageModal()"><i class="fas fa-plus"></i> إضافة مرحلة</button>
                    </div>
                    <div id="stagesContainer"><div class="empty-state"><i class="fas fa-layer-group"></i><p>لا توجد مراحل. قم بإضافة مرحلة جديدة</p></div></div>
                </div>
            </div>

            <!-- ===== STUDENTS ===== -->
            <div class="page" id="page-students">
                <div class="table-card">
                    <div class="toolbar">
                        <h3><i class="fas fa-user-graduate" style="color:#f7971e;margin-left:8px;"></i>الطلاب</h3>
                        <button class="btn-primary" onclick="openStudentModal()"><i class="fas fa-plus"></i> إضافة طالب</button>
                    </div>
                    <div class="filter-row">
                        <select id="studentStageFilter" onchange="updateStudentSections();renderStudents()"><option value="">جميع المراحل</option></select>
                        <select id="studentSectionFilter" onchange="renderStudents()"><option value="">جميع الشعب</option></select>
                    </div>
                    <div id="studentsContainer"><div class="empty-state"><i class="fas fa-user-graduate"></i><p>لا يوجد طلاب. قم بإضافة طالب جديد</p></div></div>
                </div>
            </div>

            <!-- ===== TEACHERS ===== -->
            <div class="page" id="page-teachers">
                <div class="table-card">
                    <div class="toolbar">
                        <h3><i class="fas fa-chalkboard-teacher" style="color:var(--success);margin-left:8px;"></i>المدرسين</h3>
                        <button class="btn-primary" onclick="openTeacherModal()"><i class="fas fa-plus"></i> إضافة مدرس</button>
                    </div>
                    <div id="teachersContainer"><div class="empty-state"><i class="fas fa-chalkboard-teacher"></i><p>لا يوجد مدرسين. قم بإضافة مدرس جديد</p></div></div>
                </div>
            </div>

            <!-- ===== SUBJECTS ===== -->
            <div class="page" id="page-subjects">
                <div class="table-card">
                    <div class="toolbar">
                        <h3><i class="fas fa-book-open" style="color:var(--danger);margin-left:8px;"></i>المواد</h3>
                        <button class="btn-primary" onclick="openSubjectModal()"><i class="fas fa-plus"></i> إضافة مادة</button>
                    </div>
                    <div id="subjectsContainer"><div class="empty-state"><i class="fas fa-book-open"></i><p>لا توجد مواد. قم بإضافة مادة جديدة</p></div></div>
                </div>
            </div>

            <!-- ===== PARENTS ===== -->
            <div class="page" id="page-parents">
                <div class="table-card">
                    <div class="toolbar">
                        <h3><i class="fas fa-user-friends" style="color:#4D96FF;margin-left:8px;"></i>أولياء الأمور</h3>
                        <button class="btn-primary" onclick="openParentModal()"><i class="fas fa-plus"></i> إضافة ولي أمر</button>
                    </div>
                    <div id="parentsContainer"><div class="empty-state"><i class="fas fa-user-friends"></i><p>لا يوجد أولياء أمور. قم بإضافة ولي أمر جديد</p></div></div>
                </div>
            </div>

            <!-- ===== GRADES ===== -->
            <div class="page" id="page-grades">
                <div class="table-card">
                    <h3><i class="fas fa-pencil-alt" style="color:var(--primary);margin-left:8px;"></i>سجلات الدرجات</h3>
                    <div class="filter-row">
                        <select id="gradeStageFilter" onchange="updateGradeSections();renderGrades();"><option value="">اختر المرحلة</option></select>
                        <select id="gradeSectionFilter" onchange="renderGrades();"><option value="">اختر الشعبة</option></select>
                        <input type="text" id="gradeSearchInput" placeholder="بحث عن طالب..." oninput="renderGrades()" />
                        <button class="btn-primary success" onclick="saveAllGrades()"><i class="fas fa-save"></i> حفظ</button>
                        <button class="btn-primary" onclick="addGradeSubject()"><i class="fas fa-plus"></i> إضافة مادة</button>
                        <button class="btn-primary danger" onclick="removeGradeSubject()"><i class="fas fa-minus"></i> حذف مادة</button>
                    </div>
                    <div id="gradesContainer"><div class="empty-state"><i class="fas fa-pencil-alt"></i><p>اختر المرحلة والشعبة لعرض سجل الدرجات</p></div></div>
                </div>
            </div>

            <!-- ===== ATTENDANCE ===== -->
            <div class="page" id="page-attendance">
                <div class="table-card">
                    <h3><i class="fas fa-calendar-check" style="color:#4D96FF;margin-left:8px;"></i>سجل الحضور</h3>
                    <div class="tab-nav">
                        <button class="tab-btn active" data-tab="attendance-daily">يومي</button>
                        <button class="tab-btn" data-tab="attendance-weekly">أسبوعي</button>
                        <button class="tab-btn" data-tab="attendance-monthly">شهري</button>
                        <button class="tab-btn" data-tab="attendance-yearly">سنوي</button>
                    </div>
                    <div class="attendance-search">
                        <span class="search-label"><i class="fas fa-search"></i> بحث:</span>
                        <select id="attendanceStageFilter" onchange="updateAttendanceSections();renderAttendance()"><option value="">المرحلة</option></select>
                        <select id="attendanceSectionFilter" onchange="renderAttendance()"><option value="">الشعبة</option></select>
                        <input type="text" id="attendanceSearchInput" placeholder="اسم الطالب..." oninput="renderAttendance()" />
                        <input type="date" id="attendanceDate" onchange="renderAttendance()" />
                        <button class="btn-primary" onclick="markAllPresent()"><i class="fas fa-check"></i> تحديد الكل حاضر</button>
                        <button class="btn-primary success" onclick="saveAttendance()"><i class="fas fa-save"></i> حفظ</button>
                    </div>
                    <div class="absence-limit-set">
                        <label><i class="fas fa-exclamation-triangle" style="color:var(--danger);"></i> الحد الأقصى للغياب:</label>
                        <input type="number" id="absenceLimitInput" value="5" min="1" max="30" onchange="saveAbsenceLimit();renderAttendance();" />
                        <span class="limit-note">أيام (عند التجاوز يظهر إشعار)</span>
                        <button class="btn-primary warning btn-sm" onclick="applyAbsenceLimit()"><i class="fas fa-sync"></i> تطبيق</button>
                    </div>
                    <div id="attendanceSummary" class="attendance-summary"></div>
                    <div class="tab-content active" id="attendance-daily">
                        <div id="attendanceDailyContainer"><div class="empty-state"><i class="fas fa-calendar-check"></i><p>اختر المرحلة والشعبة والتاريخ</p></div></div>
                    </div>
                    <div class="tab-content" id="attendance-weekly">
                        <div id="attendanceWeeklyContainer"><div class="empty-state"><i class="fas fa-calendar-week"></i><p>اختر المرحلة والشعبة لعرض التقرير الأسبوعي</p></div></div>
                    </div>
                    <div class="tab-content" id="attendance-monthly">
                        <div id="attendanceMonthlyContainer"><div class="empty-state"><i class="fas fa-calendar-alt"></i><p>اختر المرحلة والشعبة لعرض التقرير الشهري</p></div></div>
                    </div>
                    <div class="tab-content" id="attendance-yearly">
                        <div id="attendanceYearlyContainer"><div class="empty-state"><i class="fas fa-calendar"></i><p>اختر المرحلة والشعبة لعرض التقرير السنوي</p></div></div>
                    </div>
                </div>
            </div>

            <!-- ===== SCHEDULE ===== -->
            <div class="page" id="page-schedule">
                <div class="table-card">
                    <h3><i class="fas fa-table" style="color:var(--primary);margin-left:8px;"></i>جدول الدروس الأسبوعي</h3>
                    <div class="schedule-filter">
                        <select id="scheduleStageFilter" onchange="updateScheduleSubjects();renderSchedule();"><option value="">اختر المرحلة</option></select>
                        <select id="scheduleSectionFilter" onchange="renderSchedule();"><option value="">اختر الشعبة</option></select>
                        <button class="btn-primary" onclick="openScheduleModal()"><i class="fas fa-plus"></i> إضافة حصة</button>
                        <button class="btn-primary danger" onclick="clearSchedule()"><i class="fas fa-trash"></i> مسح الجدول</button>
                    </div>
                    <div id="scheduleContainer"><div class="empty-state"><i class="fas fa-table"></i><p>اختر المرحلة والشعبة لعرض الجدول</p></div></div>
                </div>
            </div>

            <!-- ===== SETTINGS ===== -->
            <div class="page" id="page-settings">
                <div class="table-card settings-card">
                    <h3><i class="fas fa-cog" style="color:var(--primary);margin-left:8px;"></i>إعدادات النظام</h3>
                    <div class="form-group"><label>اسم المستخدم</label><input type="text" id="settingsUsername" /></div>
                    <div class="form-group"><label>كلمة المرور الجديدة</label><input type="password" id="settingsPassword" placeholder="اتركه فارغاً إذا لا تريد التغيير" /></div>
                    <div class="form-group"><label>تأكيد كلمة المرور</label><input type="password" id="settingsPasswordConfirm" placeholder="أعد كتابة كلمة المرور" /></div>
                    <button class="btn-primary success" onclick="saveSettings()"><i class="fas fa-save"></i> حفظ الإعدادات</button>
                </div>
            </div>

        </div>

        <div style="margin-top:30px;text-align:center;font-size:var(--font-sm);color:var(--gray-400);border-top:1px solid var(--gray-200);padding-top:18px;">
            <i class="fas fa-graduation-cap" style="color:var(--primary);margin-left:4px;"></i>
            مدرستي 2026-2027 &bull; جميع الحقوق محفوظة
        </div>

    </main>

    <!-- ===== MODAL ===== -->
    <div class="modal-overlay" id="modalOverlay">
        <div class="modal" id="modalContent">
            <h2 id="modalTitle"><i class="fas fa-plus-circle"></i> إضافة</h2>
            <div id="modalBody"></div>
            <div class="modal-actions">
                <button class="btn-outline" onclick="closeModal()">إلغاء</button>
                <button class="btn-primary" id="modalSaveBtn" onclick="saveModal()">حفظ</button>
            </div>
        </div>
    </div>

    <script>
        // ============================================================
        // DATA LAYER
        // ============================================================
        const DB = {
            get(key, def) { try { const d = localStorage.getItem('ms_' + key); return d ? JSON.parse(d) : def; } catch (
                e) { return def; } },
            set(key, val) { localStorage.setItem('ms_' + key, JSON.stringify(val)); }
        };

        let stages = DB.get('stages', []);
        let students = DB.get('students', []);
        let teachers = DB.get('teachers', []);
        let subjects = DB.get('subjects', []);
        let parents = DB.get('parents', []);
        let grades = DB.get('grades', {});
        let attendance = DB.get('attendance', {});
        let gradeSubjects = DB.get('gradeSubjects', []);
        let schedule = DB.get('schedule', {});
        let settings = DB.get('settings', { username: 'admin', password: '123' });
        let absenceLimit = DB.get('absenceLimit', 5);

        // ============================================================
        // HELPERS
        // ============================================================
        function saveAllData() {
            DB.set('stages', stages);
            DB.set('students', students);
            DB.set('teachers', teachers);
            DB.set('subjects', subjects);
            DB.set('parents', parents);
            DB.set('grades', grades);
            DB.set('attendance', attendance);
            DB.set('gradeSubjects', gradeSubjects);
            DB.set('schedule', schedule);
            DB.set('settings', settings);
            DB.set('absenceLimit', absenceLimit);
        }

        function generateId() { return Date.now().toString(36) + Math.random().toString(36).substr(2, 4); }

        function toast(msg, type = 'info') {
            const el = document.getElementById('toast');
            el.textContent = msg;
            el.className = 'toast ' + type;
            el.classList.add('show');
            clearTimeout(el._timer);
            el._timer = setTimeout(() => el.classList.remove('show'), 2800);
        }

        function getStageName(id) { const s = stages.find(x => x.id === id); return s ? s.name : 'غير محدد'; }

        function getSectionName(stageId, sectionId) {
            const s = stages.find(x => x.id === stageId);
            if (!s) return 'غير محدد';
            const sec = s.sections.find(x => x.id === sectionId);
            return sec ? sec.name : 'غير محدد';
        }

        function getTeacherName(id) { const t = teachers.find(x => x.id === id); return t ? t.name : 'غير محدد'; }

        function getSubjectName(id) { const s = subjects.find(x => x.id === id); return s ? s.name : 'غير محدد'; }

        function getStudentName(id) { const s = students.find(x => x.id === id); return s ? s.name : 'غير محدد'; }

        function getStageStudents(stageId, sectionId) {
            return students.filter(s => s.stageId === stageId && (sectionId ? s.sectionId === sectionId : true));
        }

        function getStageSubjects(stageId) {
            return subjects.filter(s => s.stageId === stageId);
        }

        function getStudentGrade(studentId, subjectId) {
            const key = studentId + '_' + subjectId;
            return grades[key] || { term1: '', midYear: '', term2: '', annualEffort: '', finalExam: '', total: '' };
        }

        function setStudentGrade(studentId, subjectId, data) {
            const key = studentId + '_' + subjectId;
            grades[key] = data;
            saveAllData();
        }

        function getAttendanceKey(date, studentId) {
            return date + '_' + studentId;
        }

        function getStudentAttendance(date, studentId) {
            const key = getAttendanceKey(date, studentId);
            return attendance[key] || 'present';
        }

        function setStudentAttendance(date, studentId, status) {
            const key = getAttendanceKey(date, studentId);
            attendance[key] = status;
            saveAllData();
        }

        function countStudentAbsences(studentId) {
            const allKeys = Object.keys(attendance);
            let count = 0;
            allKeys.forEach(key => {
                const [date, sid] = key.split('_');
                if (sid === studentId && attendance[key] === 'absent') {
                    count++;
                }
            });
            return count;
        }

        function getAbsenceLimit() {
            return parseInt(document.getElementById('absenceLimitInput').value) || absenceLimit || 5;
        }

        function saveAbsenceLimit() {
            const val = parseInt(document.getElementById('absenceLimitInput').value);
            if (val > 0) {
                absenceLimit = val;
                saveAllData();
                toast('تم تحديث الحد الأقصى للغياب', 'success');
            }
        }

        function applyAbsenceLimit() {
            saveAbsenceLimit();
            renderAttendance();
        }

        // ============================================================
        // NAVIGATION
        // ============================================================
        const pageSubtitle = document.getElementById('pageSubtitle');
        const subtitles = {
            dashboard: 'نظام إدارة المدارس المتكامل – لوحة التحكم الرئيسية',
            stages: 'إدارة المراحل والشعب – هيكل المدرسة',
            students: 'إدارة الطلاب – قائمة الطلاب المسجلين',
            teachers: 'إدارة المدرسين – قائمة أعضاء هيئة التدريس',
            subjects: 'المواد الدراسية – قائمة المقررات',
            parents: 'أولياء الأمور – قائمة أولياء الأمور',
            grades: 'سجلات الدرجات – إدارة درجات الطلاب',
            attendance: 'سجل الحضور – متابعة حضور الطلاب مع تتبع الغياب',
            schedule: 'جدول الدروس الأسبوعي – تنظيم الحصص الدراسية',
            settings: 'إعدادات النظام – تعديل بيانات الدخول'
        };

        function navigateTo(page) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active-page'));
            const target = document.getElementById('page-' + page);
            if (target) target.classList.add('active-page');
            document.querySelectorAll('.sidebar-nav .nav-item').forEach(el => {
                el.classList.remove('active');
                if (el.dataset.page === page) el.classList.add('active');
            });
            if (subtitles[page]) pageSubtitle.textContent = subtitles[page];
            if (window.innerWidth <= 768) closeSidebar();
            window.scrollTo({ top: 0, behavior: 'smooth' });
            if (page === 'dashboard') { updateDashboard();
                renderCalendar();
                renderDashChart();
                renderLevelChart(); }
            if (page === 'stages') renderStages();
            if (page === 'students') { populateStageFilters();
                renderStudents(); }
            if (page === 'teachers') renderTeachers();
            if (page === 'subjects') renderSubjects();
            if (page === 'parents') renderParents();
            if (page === 'grades') { populateGradeFilters();
                renderGrades(); }
            if (page === 'attendance') { populateAttendanceFilters();
                renderAttendance(); }
            if (page === 'schedule') { populateScheduleFilters();
                renderSchedule(); }
            if (page === 'settings') { loadSettings(); }
            updateBadges();
        }

        document.querySelectorAll('.sidebar-nav .nav-item').forEach(el => {
            el.addEventListener('click', function(e) {
                e.preventDefault();
                const page = this.dataset.page;
                if (page) navigateTo(page);
            });
        });

        // ============================================================
        // SIDEBAR TOGGLE
        // ============================================================
        const menuToggle = document.getElementById('menuToggle');
        const sidebar = document.getElementById('sidebar');
        const overlay = document.getElementById('sidebarOverlay');

        function toggleSidebar() {
            sidebar.classList.toggle('open');
            overlay.classList.toggle('active');
            document.body.style.overflow = sidebar.classList.contains('open') ? 'hidden' : '';
        }

        function closeSidebar() {
            sidebar.classList.remove('open');
            overlay.classList.remove('active');
            document.body.style.overflow = '';
        }
        menuToggle.addEventListener('click', toggleSidebar);
        overlay.addEventListener('click', closeSidebar);
        window.addEventListener('resize', () => { if (window.innerWidth > 768) closeSidebar(); });
        document.addEventListener('keydown', (e) => { if (e.key === 'Escape') closeSidebar(); });

        // ============================================================
        // DATETIME
        // ============================================================
        function updateDateTime() {
            const now = new Date();
            let h = now.getHours();
            const ampm = h >= 12 ? 'PM' : 'AM';
            h = h % 12 || 12;
            const m = String(now.getMinutes()).padStart(2, '0');
            document.getElementById('currentTime').textContent = h + ':' + m + ' ' + ampm;
            const d = String(now.getDate()).padStart(2, '0');
            const mo = String(now.getMonth() + 1).padStart(2, '0');
            const y = now.getFullYear();
            document.getElementById('currentDate').textContent = d + '/' + mo + '/' + y;
            const dateInput = document.getElementById('attendanceDate');
            if (dateInput && !dateInput.value) {
                dateInput.value = y + '-' + mo + '-' + d;
            }
        }
        updateDateTime();
        setInterval(updateDateTime, 30000);

        // ============================================================
        // USER AVATAR
        // ============================================================
        document.getElementById('userAvatar').addEventListener('click', () => toast('👤 الملف الشخصي'));

        // ============================================================
        // LOGIN / LOGOUT
        // ============================================================
        function showDefaultCredentials() {
            document.getElementById('loginUser').value = 'admin';
            document.getElementById('loginPass').value = '123';
            toast('تم تعبئة البيانات الافتراضية (admin / 123)', 'info');
        }

        function login() {
            const user = document.getElementById('loginUser').value;
            const pass = document.getElementById('loginPass').value;
            if (user === settings.username && pass === settings.password) {
                document.getElementById('loginScreen').classList.remove('active');
                document.getElementById('mainContent').style.display = 'block';
                toast('تم تسجيل الدخول بنجاح', 'success');
                initApp();
            } else {
                toast('اسم المستخدم أو كلمة المرور غير صحيحة', 'error');
            }
        }

        function logout() {
            if (confirm('هل أنت متأكد من الخروج؟ سيتم حفظ جميع البيانات.')) {
                document.getElementById('loginScreen').classList.add('active');
                document.getElementById('mainContent').style.display = 'none';
                toast('تم الخروج بنجاح', 'success');
            }
        }

        // ============================================================
        // DASHBOARD
        // ============================================================
        function updateDashboard() {
            document.getElementById('dashStages').textContent = stages.length;
            document.getElementById('dashStudents').textContent = students.length;
            document.getElementById('dashTeachers').textContent = teachers.length;
            document.getElementById('dashSubjects').textContent = subjects.length;
            document.getElementById('dashParents').textContent = parents.length;
        }

        function updateBadges() {
            document.getElementById('stageBadge').textContent = stages.length;
            document.getElementById('studentBadge').textContent = students.length;
            document.getElementById('teacherBadge').textContent = teachers.length;
            document.getElementById('subjectBadge').textContent = subjects.length;
        }

        // ============================================================
        // CALENDAR
        // ============================================================
        let calDate = new Date();

        function renderCalendar() {
            const container = document.getElementById('calendar');
            const year = calDate.getFullYear();
            const month = calDate.getMonth();
            const today = new Date();
            const firstDay = new Date(year, month, 1).getDay();
            const daysInMonth = new Date(year, month + 1, 0).getDate();
            const daysInPrev = new Date(year, month, 0).getDate();
            let html =
                `<div class="cal-header"><button onclick="changeMonth(-1)"><i class="fas fa-chevron-right"></i></button><span>${new Intl.DateTimeFormat('ar-EG', { month: 'long', year: 'numeric' }).format(calDate)}</span><button onclick="changeMonth(1)"><i class="fas fa-chevron-left"></i></button></div><div class="cal-weekdays"><span>أحد</span><span>إثنين</span><span>ثلاثاء</span><span>أربعاء</span><span>خميس</span><span>جمعة</span><span>سبت</span></div><div class="cal-days">`;
            const startOffset = firstDay === 0 ? 6 : firstDay - 1;
            for (let i = startOffset; i > 0; i--) { const d = daysInPrev - i + 1;
                html += `<div class="cal-day other-month">${d}</div>`; }
            for (let d = 1; d <= daysInMonth; d++) {
                const isToday = (d === today.getDate() && month === today.getMonth() && year === today.getFullYear());
                const dayOfWeek = new Date(year, month, d).getDay();
                const isWeekend = (dayOfWeek === 5 || dayOfWeek === 6);
                const hasEvent = (d % 5 === 0);
                let cls = 'cal-day';
                if (isToday) cls += ' today';
                if (isWeekend) cls += ' cal-day-weekend';
                if (hasEvent) cls += ' has-event';
                html += `<div class="${cls}">${d}</div>`;
            }
            const remaining = 42 - (startOffset + daysInMonth);
            for (let d = 1; d <= remaining; d++) { html += `<div class="cal-day other-month">${d}</div>`; }
            html += '</div>';
            container.innerHTML = html;
        }

        function changeMonth(delta) { calDate.setMonth(calDate.getMonth() + delta);
            renderCalendar(); }

        // ============================================================
        // DASHBOARD CHART
        // ============================================================
        function renderDashChart() {
            const container = document.getElementById('dashChart');
            const colors = ['chart-colors-1', 'chart-colors-2', 'chart-colors-3', 'chart-colors-4', 'chart-colors-5',
                'chart-colors-6', 'chart-colors-7'
            ];
            let html = '';
            stages.forEach((stage, idx) => {
                const count = students.filter(s => s.stageId === stage.id).length;
                const max = Math.max(1, ...stages.map(s => students.filter(st => st.stageId === s.id).length));
                const height = max > 0 ? Math.max(15, (count / max) * 100) : 15;
                const color = colors[idx % colors.length];
                html +=
                    `<div class="chart-bar-wrapper"><div class="chart-bar-value">${count}</div><div class="chart-bar ${color}" style="height:${height}px;"></div><span class="chart-bar-label">${stage.name.replace('متوسط','')}</span></div>`;
            });
            container.innerHTML = html || '<p style="color:var(--gray-500);text-align:center;">لا توجد مراحل</p>';
        }

        // ============================================================
        // LEVEL CHART
        // ============================================================
        function renderLevelChart() {
            if (!students.length) {
                ['levelExcellent', 'levelGood', 'levelAverage', 'levelWeak'].forEach(id => {
                    document.getElementById(id).style.width = '0%';
                    document.getElementById(id).textContent = '0';
                });
                ['levelExcellentCount', 'levelGoodCount', 'levelAverageCount', 'levelWeakCount'].forEach(id => {
                    document.getElementById(id).textContent = '0';
                });
                return;
            }
            const studentAverages = {};
            students.forEach(student => {
                let total = 0,
                    count = 0;
                const stageSubjects = subjects.filter(s => s.stageId === student.stageId);
                const displaySubs = gradeSubjects.length ? gradeSubjects : stageSubjects.map(s => s.name);
                if (!displaySubs.length) { studentAverages[student.id] = 0; return; }
                displaySubs.forEach(sub => {
                    let subObj = subjects.find(s => s.name === sub && s.stageId === student.stageId);
                    let subId = subObj ? subObj.id : sub;
                    const g = getStudentGrade(student.id, subId);
                    const effort = parseInt(g.annualEffort) || 0;
                    const final = parseFloat(g.finalExam) || 0;
                    const totalGrade = Math.round((effort + final) / 2);
                    if (totalGrade > 0) { total += totalGrade;
                        count++; }
                });
                studentAverages[student.id] = count > 0 ? Math.round(total / count) : 0;
            });
            let excellent = 0,
                good = 0,
                average = 0,
                weak = 0;
            Object.values(studentAverages).forEach(avg => {
                if (avg >= 85) excellent++;
                else if (avg >= 70) good++;
                else if (avg >= 50) average++;
                else weak++;
            });
            const total = students.length;
            const pct = (n) => total > 0 ? Math.round((n / total) * 100) : 0;
            const levels = [
                { id: 'excellent', count: excellent, pct: pct(excellent) },
                { id: 'good', count: good, pct: pct(good) },
                { id: 'average', count: average, pct: pct(average) },
                { id: 'weak', count: weak, pct: pct(weak) }
            ];
            levels.forEach(level => {
                const bar = document.getElementById('level' + level.id.charAt(0).toUpperCase() + level.id.slice(1));
                const countEl = document.getElementById('level' + level.id.charAt(0).toUpperCase() + level.id.slice(
                    1) + 'Count');
                if (bar) { bar.style.width = level.pct + '%';
                    bar.textContent = level.count; }
                if (countEl) countEl.textContent = level.count;
            });
        }

        // ============================================================
        // STAGES CRUD
        // ============================================================
        let tempSections = [];

        function renderStages() {
            const container = document.getElementById('stagesContainer');
            if (!stages.length) {
                container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-layer-group"></i><p>لا توجد مراحل. قم بإضافة مرحلة جديدة</p></div>';
                return;
            }
            let html =
                `<table><thead><tr><th>#</th><th>المرحلة</th><th>الشعب</th><th>عدد الطلاب</th><th>الإجراءات</th></tr></thead><tbody>`;
            stages.forEach((s, i) => {
                const sectionNames = s.sections.map(sec => sec.name).join('، ');
                const studentCount = students.filter(st => st.stageId === s.id).length;
                html +=
                    `<tr><td>${i+1}</td><td><strong>${s.name}</strong></td><td>${sectionNames || 'لا توجد شعب'}</td><td>${studentCount}</td><td>
                                <button class="btn-primary btn-sm" onclick="editStage('${s.id}')"><i class="fas fa-edit"></i></button>
                                <button class="btn-primary danger btn-sm" onclick="deleteStage('${s.id}')"><i class="fas fa-trash"></i></button>
                                <button class="btn-primary warning btn-sm" onclick="addSectionToStage('${s.id}')"><i class="fas fa-plus-circle"></i> إضافة شعبة</button>
                            </td></tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function addSectionToStage(stageId) {
            const stage = stages.find(s => s.id === stageId);
            if (!stage) { toast('المرحلة غير موجودة', 'error'); return; }
            const sectionName = prompt('أدخل اسم الشعبة الجديدة:');
            if (sectionName && sectionName.trim()) {
                const name = sectionName.trim();
                if (stage.sections.some(sec => sec.name === name)) {
                    toast('هذه الشعبة موجودة بالفعل', 'error');
                    return;
                }
                stage.sections.push({ id: generateId(), name: name });
                saveAllData();
                renderStages();
                updateBadges();
                toast('تم إضافة الشعبة: ' + name, 'success');
            }
        }

        function openStageModal(data) {
            const isEdit = !!data;
            const title = isEdit ? 'تعديل المرحلة' : 'إضافة مرحلة جديدة';
            document.getElementById('modalTitle').innerHTML = `<i class="fas fa-layer-group"></i> ${title}`;
            const name = isEdit ? data.name : '';
            tempSections = isEdit ? (data.sections || []).map(s => ({ ...s })) : [];

            let sectionsHtml = tempSections.map(sec =>
                `<li><span class="section-name">${sec.name}</span><button class="remove-section" onclick="removeTempSection('${sec.id}')"><i class="fas fa-times"></i></button></li>`
            ).join('');

            document.getElementById('modalBody').innerHTML = `
                        <div class="form-group">
                            <label>اسم المرحلة</label>
                            <input type="text" id="fStageName" value="${name}" placeholder="مثال: الرابع العلمي" />
                        </div>
                        <div class="form-group">
                            <label>الشعب</label>
                            <ul class="section-list" id="tempSectionList">
                                ${sectionsHtml || '<li style="color:var(--gray-500);justify-content:center;">لا توجد شعب مضافة</li>'}
                            </ul>
                            <div class="add-section-row">
                                <input type="text" id="fNewSectionName" placeholder="أدخل اسم الشعبة" />
                                <button class="btn-primary btn-sm" onclick="addTempSection()">إضافة</button>
                            </div>
                        </div>
                    `;
            document.getElementById('modalSaveBtn').dataset.id = isEdit ? data.id : '';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function addTempSection() {
            const input = document.getElementById('fNewSectionName');
            const name = input.value.trim();
            if (!name) { toast('الرجاء إدخال اسم الشعبة', 'error'); return; }
            if (tempSections.some(s => s.name === name)) {
                toast('هذه الشعبة موجودة بالفعل', 'error');
                return;
            }
            tempSections.push({ id: generateId(), name: name });
            input.value = '';
            renderTempSections();
        }

        function removeTempSection(id) {
            tempSections = tempSections.filter(s => s.id !== id);
            renderTempSections();
        }

        function renderTempSections() {
            const list = document.getElementById('tempSectionList');
            if (!list) return;
            if (tempSections.length === 0) {
                list.innerHTML = '<li style="color:var(--gray-500);justify-content:center;">لا توجد شعب مضافة</li>';
                return;
            }
            list.innerHTML = tempSections.map(sec =>
                `<li><span class="section-name">${sec.name}</span><button class="remove-section" onclick="removeTempSection('${sec.id}')"><i class="fas fa-times"></i></button></li>`
            ).join('');
        }

        function saveStage() {
            const id = document.getElementById('modalSaveBtn').dataset.id;
            const name = document.getElementById('fStageName').value.trim();
            if (!name) { toast('الرجاء إدخال اسم المرحلة', 'error'); return; }

            const existing = stages.find(s => s.name === name && s.id !== id);
            if (existing) {
                toast('مرحلة بنفس الاسم موجودة بالفعل. يمكنك إضافة شعب لها من خلال زر "إضافة شعبة"', 'error');
                return;
            }

            if (id) {
                const stage = stages.find(s => s.id === id);
                if (stage) {
                    stage.name = name;
                    const existingNames = stage.sections.map(s => s.name);
                    tempSections.forEach(sec => {
                        if (!existingNames.includes(sec.name)) {
                            stage.sections.push({ id: generateId(), name: sec.name });
                        }
                    });
                    toast('تم تحديث المرحلة', 'success');
                }
            } else {
                const sections = tempSections.map(s => ({ id: s.id, name: s.name }));
                stages.push({ id: generateId(), name, sections });
                toast('تم إضافة المرحلة', 'success');
            }
            saveAllData();
            closeModal();
            renderStages();
            updateBadges();
            updateDashboard();
            populateStageFilters();
            populateGradeFilters();
            populateAttendanceFilters();
            populateScheduleFilters();
            renderDashChart();
            renderLevelChart();
        }

        function editStage(id) {
            const stage = stages.find(s => s.id === id);
            if (stage) openStageModal(stage);
        }

        function deleteStage(id) {
            if (!confirm('هل أنت متأكد من حذف هذه المرحلة؟ سيتم حذف جميع بياناتها المرتبطة.')) return;
            students = students.filter(s => s.stageId !== id);
            subjects = subjects.filter(s => s.stageId !== id);
            const studentIds = students.filter(s => s.stageId === id).map(s => s.id);
            studentIds.forEach(sid => {
                Object.keys(grades).forEach(key => {
                    if (key.startsWith(sid + '_')) delete grades[key];
                });
            });
            Object.keys(schedule).forEach(key => {
                if (key.startsWith(id + '_')) delete schedule[key];
            });
            stages = stages.filter(s => s.id !== id);
            saveAllData();
            renderStages();
            updateBadges();
            updateDashboard();
            populateStageFilters();
            populateGradeFilters();
            populateAttendanceFilters();
            populateScheduleFilters();
            renderDashChart();
            renderLevelChart();
            toast('تم حذف المرحلة', 'success');
        }

        // ============================================================
        // STUDENTS CRUD
        // ============================================================
        function populateStageFilters() {
            const selects = ['studentStageFilter', 'gradeStageFilter', 'attendanceStageFilter', 'scheduleStageFilter'];
            selects.forEach(id => {
                const el = document.getElementById(id);
                if (!el) return;
                const val = el.value;
                el.innerHTML = '<option value="">جميع المراحل</option>';
                stages.forEach(s => { el.innerHTML += `<option value="${s.id}">${s.name}</option>`; });
                if (val && stages.some(s => s.id === val)) el.value = val;
            });
            updateStudentSections();
            updateGradeSections();
            updateAttendanceSections();
            updateScheduleSections();
        }

        function updateStudentSections() {
            const stageId = document.getElementById('studentStageFilter').value;
            const el = document.getElementById('studentSectionFilter');
            const val = el.value;
            el.innerHTML = '<option value="">جميع الشعب</option>';
            const stage = stages.find(s => s.id === stageId);
            if (stage) { stage.sections.forEach(sec => { el.innerHTML += `<option value="${sec.id}">${sec.name}</option>`; }); }
            if (val && stage && stage.sections.some(s => s.id === val)) el.value = val;
        }
        document.getElementById('studentStageFilter').addEventListener('change', updateStudentSections);

        function renderStudents() {
            const container = document.getElementById('studentsContainer');
            const stageId = document.getElementById('studentStageFilter').value;
            const sectionId = document.getElementById('studentSectionFilter').value;
            let filtered = students;
            if (stageId) filtered = filtered.filter(s => s.stageId === stageId);
            if (sectionId) filtered = filtered.filter(s => s.sectionId === sectionId);
            if (!filtered.length) { container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-user-graduate"></i><p>لا يوجد طلاب مطابقين للفلتر</p></div>'; return; }
            let html =
                `<table><thead><tr><th>#</th><th>الاسم</th><th>المرحلة</th><th>الشعبة</th><th>ولي الأمر</th><th>الإجراءات</th></tr></thead><tbody>`;
            filtered.forEach((s, i) => {
                const parent = parents.find(p => p.id === s.parentId);
                html +=
                    `<tr><td>${i+1}</td><td>${s.name}</td><td>${getStageName(s.stageId)}</td><td>${getSectionName(s.stageId, s.sectionId)}</td><td>${parent ? parent.name : 'غير محدد'}</td><td><button class="btn-primary btn-sm" onclick="editStudent('${s.id}')"><i class="fas fa-edit"></i></button><button class="btn-primary danger btn-sm" onclick="deleteStudent('${s.id}')"><i class="fas fa-trash"></i></button><button class="whatsapp-btn" onclick="sendWhatsApp('${s.id}','رسالة لولي الأمر')"><i class="fab fa-whatsapp"></i></button></td></tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function openStudentModal(data) {
            const isEdit = !!data;
            document.getElementById('modalTitle').innerHTML =
                `<i class="fas fa-user-graduate"></i> ${isEdit ? 'تعديل طالب' : 'إضافة طالب جديد'}`;
            let stageOpts = '',
                sectionOpts = '',
                parentOpts = '';
            stages.forEach(s => { const sel = (data && data.stageId === s.id) ? 'selected' : '';
                stageOpts += `<option value="${s.id}" ${sel}>${s.name}</option>`; });
            const stageId = data ? data.stageId : (stages.length ? stages[0].id : '');
            const stage = stages.find(s => s.id === stageId);
            if (stage) { stage.sections.forEach(sec => { const sel = (data && data.sectionId === sec.id) ? 'selected' : '';
                    sectionOpts += `<option value="${sec.id}" ${sel}>${sec.name}</option>`; }); }
            parents.forEach(p => { const sel = (data && data.parentId === p.id) ? 'selected' : '';
                parentOpts += `<option value="${p.id}" ${sel}>${p.name}</option>`; });
            document.getElementById('modalBody').innerHTML =
                `<div class="form-group"><label>اسم الطالب</label><input type="text" id="fStudentName" value="${data ? data.name : ''}" /></div><div class="form-row"><div class="form-group"><label>المرحلة</label><select id="fStudentStage" onchange="updateStudentModalSections()">${stageOpts}</select></div><div class="form-group"><label>الشعبة</label><select id="fStudentSection">${sectionOpts}</select></div></div><div class="form-group"><label>ولي الأمر</label><select id="fStudentParent"><option value="">بدون ولي أمر</option>${parentOpts}</select></div><div class="form-group"><label>رقم ولي الأمر (واتساب)</label><input type="text" id="fParentPhone" value="${data && data.parentPhone ? data.parentPhone : ''}" placeholder="مثال: 0555123456" /></div>`;
            document.getElementById('modalSaveBtn').dataset.id = isEdit ? data.id : '';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function updateStudentModalSections() {
            const stageId = document.getElementById('fStudentStage').value;
            const el = document.getElementById('fStudentSection');
            const val = el.value;
            el.innerHTML = '';
            const stage = stages.find(s => s.id === stageId);
            if (stage) { stage.sections.forEach(sec => { el.innerHTML += `<option value="${sec.id}">${sec.name}</option>`; }); }
            if (val && stage && stage.sections.some(s => s.id === val)) el.value = val;
        }

        function saveStudent() {
            const id = document.getElementById('modalSaveBtn').dataset.id;
            const name = document.getElementById('fStudentName').value.trim();
            const stageId = document.getElementById('fStudentStage').value;
            const sectionId = document.getElementById('fStudentSection').value;
            const parentId = document.getElementById('fStudentParent').value || null;
            const parentPhone = document.getElementById('fParentPhone').value.trim();
            if (!name) { toast('الرجاء إدخال اسم الطالب', 'error'); return; }
            if (!stageId) { toast('الرجاء اختيار المرحلة', 'error'); return; }
            if (!sectionId) { toast('الرجاء اختيار الشعبة', 'error'); return; }
            if (id) {
                const student = students.find(s => s.id === id);
                if (student) { student.name = name;
                    student.stageId = stageId;
                    student.sectionId = sectionId;
                    student.parentId = parentId;
                    student.parentPhone = parentPhone;
                    toast('تم تحديث الطالب', 'success'); }
            } else {
                students.push({ id: generateId(), name, stageId, sectionId, parentId, parentPhone });
                toast('تم إضافة الطالب', 'success');
            }
            saveAllData();
            closeModal();
            renderStudents();
            updateBadges();
            updateDashboard();
            renderDashChart();
            renderLevelChart();
        }

        function editStudent(id) { const student = students.find(s => s.id === id); if (student) openStudentModal(student); }

        function deleteStudent(id) {
            if (!confirm('هل أنت متأكد من حذف هذا الطالب؟')) return;
            students = students.filter(s => s.id !== id);
            Object.keys(grades).forEach(key => { if (key.startsWith(id + '_')) delete grades[key]; });
            saveAllData();
            renderStudents();
            updateBadges();
            updateDashboard();
            renderDashChart();
            renderLevelChart();
            toast('تم حذف الطالب', 'success');
        }

        // ============================================================
        // WHATSAPP
        // ============================================================
        function sendWhatsApp(studentId, defaultMsg = '') {
            const student = students.find(s => s.id === studentId);
            if (!student) { toast('الطالب غير موجود', 'error'); return; }
            const phone = student.parentPhone || '';
            if (!phone) { toast('رقم ولي الأمر غير مسجل، قم بتحديث بيانات الطالب', 'error'); return; }
            document.getElementById('modalTitle').innerHTML =
                `<i class="fab fa-whatsapp" style="color:#25D366;"></i> إرسال رسالة لولي أمر ${student.name}`;
            document.getElementById('modalBody').innerHTML =
                `<div class="form-group"><label>رقم ولي الأمر</label><input type="text" id="whatsappPhone" value="${phone}" readonly /></div><div class="form-group"><label>الرسالة</label><textarea id="whatsappMessage" rows="4">${defaultMsg}</textarea></div>`;
            document.getElementById('modalSaveBtn').dataset.action = 'whatsapp';
            document.getElementById('modalSaveBtn').textContent = 'إرسال عبر واتساب';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function sendWhatsAppMessage() {
            const phone = document.getElementById('whatsappPhone').value;
            const msg = document.getElementById('whatsappMessage').value.trim();
            if (!msg) { toast('الرجاء كتابة الرسالة', 'error'); return; }
            window.open(`https://wa.me/${phone}?text=${encodeURIComponent(msg)}`, '_blank');
            closeModal();
            toast('تم فتح واتساب لإرسال الرسالة', 'success');
            document.getElementById('modalSaveBtn').dataset.action = '';
            document.getElementById('modalSaveBtn').textContent = 'حفظ';
        }

        // ============================================================
        // TEACHERS CRUD
        // ============================================================
        function renderTeachers() {
            const container = document.getElementById('teachersContainer');
            if (!teachers.length) { container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-chalkboard-teacher"></i><p>لا يوجد مدرسين. قم بإضافة مدرس جديد</p></div>'; return; }
            let html =
                `<table><thead><tr><th>#</th><th>الاسم</th><th>التخصص</th><th>البريد</th><th>الإجراءات</th></tr></thead><tbody>`;
            teachers.forEach((t, i) => {
                html +=
                    `<tr><td>${i+1}</td><td>${t.name}</td><td>${t.specialty || '-'}</td><td>${t.email || '-'}</td><td><button class="btn-primary btn-sm" onclick="editTeacher('${t.id}')"><i class="fas fa-edit"></i></button><button class="btn-primary danger btn-sm" onclick="deleteTeacher('${t.id}')"><i class="fas fa-trash"></i></button></td></tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function openTeacherModal(data) {
            const isEdit = !!data;
            document.getElementById('modalTitle').innerHTML =
                `<i class="fas fa-chalkboard-teacher"></i> ${isEdit ? 'تعديل مدرس' : 'إضافة مدرس جديد'}`;
            document.getElementById('modalBody').innerHTML =
                `<div class="form-group"><label>اسم المدرس</label><input type="text" id="fTeacherName" value="${data ? data.name : ''}" /></div><div class="form-row"><div class="form-group"><label>التخصص</label><input type="text" id="fTeacherSpecialty" value="${data ? data.specialty : ''}" /></div><div class="form-group"><label>البريد الإلكتروني</label><input type="email" id="fTeacherEmail" value="${data ? data.email : ''}" /></div></div>`;
            document.getElementById('modalSaveBtn').dataset.id = isEdit ? data.id : '';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function saveTeacher() {
            const id = document.getElementById('modalSaveBtn').dataset.id;
            const name = document.getElementById('fTeacherName').value.trim();
            const specialty = document.getElementById('fTeacherSpecialty').value.trim();
            const email = document.getElementById('fTeacherEmail').value.trim();
            if (!name) { toast('الرجاء إدخال اسم المدرس', 'error'); return; }
            if (id) {
                const teacher = teachers.find(t => t.id === id);
                if (teacher) { teacher.name = name;
                    teacher.specialty = specialty;
                    teacher.email = email;
                    toast('تم تحديث المدرس', 'success'); }
            } else {
                teachers.push({ id: generateId(), name, specialty, email });
                toast('تم إضافة المدرس', 'success');
            }
            saveAllData();
            closeModal();
            renderTeachers();
            updateBadges();
            updateDashboard();
        }

        function editTeacher(id) { const teacher = teachers.find(t => t.id === id); if (teacher) openTeacherModal(teacher); }

        function deleteTeacher(id) {
            if (!confirm('هل أنت متأكد من حذف هذا المدرس؟')) return;
            teachers = teachers.filter(t => t.id !== id);
            saveAllData();
            renderTeachers();
            updateBadges();
            updateDashboard();
            toast('تم حذف المدرس', 'success');
        }

        // ============================================================
        // SUBJECTS CRUD
        // ============================================================
        function renderSubjects() {
            const container = document.getElementById('subjectsContainer');
            if (!subjects.length) { container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-book-open"></i><p>لا توجد مواد. قم بإضافة مادة جديدة</p></div>'; return; }
            let html =
                `<table><thead><tr><th>#</th><th>المادة</th><th>المرحلة</th><th>المدرس</th><th>الإجراءات</th></tr></thead><tbody>`;
            subjects.forEach((s, i) => {
                html +=
                    `<tr><td>${i+1}</td><td>${s.name}</td><td>${getStageName(s.stageId)}</td><td>${getTeacherName(s.teacherId)}</td><td><button class="btn-primary btn-sm" onclick="editSubject('${s.id}')"><i class="fas fa-edit"></i></button><button class="btn-primary danger btn-sm" onclick="deleteSubject('${s.id}')"><i class="fas fa-trash"></i></button></td></tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function openSubjectModal(data) {
            const isEdit = !!data;
            document.getElementById('modalTitle').innerHTML =
                `<i class="fas fa-book-open"></i> ${isEdit ? 'تعديل مادة' : 'إضافة مادة جديدة'}`;
            let stageOpts = '',
                teacherOpts = '';
            stages.forEach(s => { const sel = (data && data.stageId === s.id) ? 'selected' : '';
                stageOpts += `<option value="${s.id}" ${sel}>${s.name}</option>`; });
            teachers.forEach(t => { const sel = (data && data.teacherId === t.id) ? 'selected' : '';
                teacherOpts += `<option value="${t.id}" ${sel}>${t.name}</option>`; });
            document.getElementById('modalBody').innerHTML =
                `<div class="form-group"><label>اسم المادة</label><input type="text" id="fSubjectName" value="${data ? data.name : ''}" /></div><div class="form-row"><div class="form-group"><label>المرحلة</label><select id="fSubjectStage">${stageOpts}</select></div><div class="form-group"><label>المدرس</label><select id="fSubjectTeacher"><option value="">بدون مدرس</option>${teacherOpts}</select></div></div>`;
            document.getElementById('modalSaveBtn').dataset.id = isEdit ? data.id : '';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function saveSubject() {
            const id = document.getElementById('modalSaveBtn').dataset.id;
            const name = document.getElementById('fSubjectName').value.trim();
            const stageId = document.getElementById('fSubjectStage').value;
            const teacherId = document.getElementById('fSubjectTeacher').value || null;
            if (!name) { toast('الرجاء إدخال اسم المادة', 'error'); return; }
            if (!stageId) { toast('الرجاء اختيار المرحلة', 'error'); return; }
            if (id) {
                const subject = subjects.find(s => s.id === id);
                if (subject) { subject.name = name;
                    subject.stageId = stageId;
                    subject.teacherId = teacherId;
                    toast('تم تحديث المادة', 'success'); }
            } else {
                subjects.push({ id: generateId(), name, stageId, teacherId });
                toast('تم إضافة المادة', 'success');
            }
            saveAllData();
            closeModal();
            renderSubjects();
            updateBadges();
            updateDashboard();
        }

        function editSubject(id) { const subject = subjects.find(s => s.id === id); if (subject) openSubjectModal(subject); }

        function deleteSubject(id) {
            if (!confirm('هل أنت متأكد من حذف هذه المادة؟')) return;
            subjects = subjects.filter(s => s.id !== id);
            saveAllData();
            renderSubjects();
            updateBadges();
            updateDashboard();
            toast('تم حذف المادة', 'success');
        }

        // ============================================================
        // PARENTS CRUD
        // ============================================================
        function renderParents() {
            const container = document.getElementById('parentsContainer');
            if (!parents.length) { container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-user-friends"></i><p>لا يوجد أولياء أمور. قم بإضافة ولي أمر جديد</p></div>'; return; }
            let html =
                `<table><thead><tr><th>#</th><th>الاسم</th><th>الطالب</th><th>الهاتف</th><th>الإجراءات</th></tr></thead><tbody>`;
            parents.forEach((p, i) => {
                const student = students.find(s => s.id === p.studentId);
                html +=
                    `<tr><td>${i+1}</td><td>${p.name}</td><td>${student ? student.name : 'غير محدد'}</td><td>${p.phone || '-'}</td><td><button class="btn-primary btn-sm" onclick="editParent('${p.id}')"><i class="fas fa-edit"></i></button><button class="btn-primary danger btn-sm" onclick="deleteParent('${p.id}')"><i class="fas fa-trash"></i></button></td></tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function openParentModal(data) {
            const isEdit = !!data;
            document.getElementById('modalTitle').innerHTML =
                `<i class="fas fa-user-friends"></i> ${isEdit ? 'تعديل ولي أمر' : 'إضافة ولي أمر جديد'}`;
            let studentOpts = '';
            students.forEach(s => { const sel = (data && data.studentId === s.id) ? 'selected' : '';
                studentOpts += `<option value="${s.id}" ${sel}>${s.name}</option>`; });
            document.getElementById('modalBody').innerHTML =
                `<div class="form-group"><label>اسم ولي الأمر</label><input type="text" id="fParentName" value="${data ? data.name : ''}" /></div><div class="form-row"><div class="form-group"><label>الطالب</label><select id="fParentStudent"><option value="">بدون طالب</option>${studentOpts}</select></div><div class="form-group"><label>رقم الهاتف</label><input type="text" id="fParentPhone" value="${data ? data.phone : ''}" /></div></div>`;
            document.getElementById('modalSaveBtn').dataset.id = isEdit ? data.id : '';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function saveParent() {
            const id = document.getElementById('modalSaveBtn').dataset.id;
            const name = document.getElementById('fParentName').value.trim();
            const studentId = document.getElementById('fParentStudent').value || null;
            const phone = document.getElementById('fParentPhone').value.trim();
            if (!name) { toast('الرجاء إدخال اسم ولي الأمر', 'error'); return; }
            if (id) {
                const parent = parents.find(p => p.id === id);
                if (parent) { parent.name = name;
                    parent.studentId = studentId;
                    parent.phone = phone;
                    toast('تم تحديث ولي الأمر', 'success'); }
            } else {
                parents.push({ id: generateId(), name, studentId, phone });
                toast('تم إضافة ولي الأمر', 'success');
            }
            saveAllData();
            closeModal();
            renderParents();
            updateBadges();
            updateDashboard();
        }

        function editParent(id) { const parent = parents.find(p => p.id === id); if (parent) openParentModal(parent); }

        function deleteParent(id) {
            if (!confirm('هل أنت متأكد من حذف ولي الأمر؟')) return;
            parents = parents.filter(p => p.id !== id);
            saveAllData();
            renderParents();
            updateBadges();
            updateDashboard();
            toast('تم حذف ولي الأمر', 'success');
        }

        // ============================================================
        // GRADES
        // ============================================================
        function populateGradeFilters() {
            const el = document.getElementById('gradeStageFilter');
            const val = el.value;
            el.innerHTML = '<option value="">اختر المرحلة</option>';
            stages.forEach(s => { el.innerHTML += `<option value="${s.id}">${s.name}</option>`; });
            if (val && stages.some(s => s.id === val)) el.value = val;
            updateGradeSections();
        }

        function updateGradeSections() {
            const stageId = document.getElementById('gradeStageFilter').value;
            const el = document.getElementById('gradeSectionFilter');
            const val = el.value;
            el.innerHTML = '<option value="">اختر الشعبة</option>';
            const stage = stages.find(s => s.id === stageId);
            if (stage) { stage.sections.forEach(sec => { el.innerHTML += `<option value="${sec.id}">${sec.name}</option>`; }); }
            if (val && stage && stage.sections.some(s => s.id === val)) el.value = val;
        }

        function renderGrades() {
            const container = document.getElementById('gradesContainer');
            const stageId = document.getElementById('gradeStageFilter').value;
            const sectionId = document.getElementById('gradeSectionFilter').value;
            const searchTerm = document.getElementById('gradeSearchInput').value.trim().toLowerCase();
            if (!stageId || !sectionId) {
                container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-pencil-alt"></i><p>اختر المرحلة والشعبة لعرض سجل الدرجات</p></div>';
                return;
            }
            let stageStudents = students.filter(s => s.stageId === stageId && s.sectionId === sectionId);
            if (searchTerm) {
                stageStudents = stageStudents.filter(s => s.name.toLowerCase().includes(searchTerm));
            }
            let displaySubjects = gradeSubjects.length ? gradeSubjects : subjects.filter(s => s.stageId === stageId).map(s => s
                .name);
            if (!displaySubjects.length) displaySubjects = ['الرياضيات', 'اللغة العربية', 'العلوم'];
            if (!stageStudents.length) {
                container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-user-graduate"></i><p>لا يوجد طلاب مطابقين للبحث</p></div>';
                return;
            }
            let html = `<div class="grades-table-wrap"><table><tr><th style="min-width:100px;background:var(--primary);color:#fff;font-size:var(--font-base);font-weight:900;">المادة</th>`;
            stageStudents.forEach(student => {
                html +=
                    `<th colspan="6" style="background:var(--primary);color:#fff;font-size:var(--font-sm);font-weight:800;text-align:center;border-color:var(--primary-dark);">${student.name}</th>`;
            });
            html += `</tr><tr class="sub-header"><th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;"></th>`;
            stageStudents.forEach(() => {
                html +=
                    `<th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;">الفصل1</th><th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;">نصف السنه</th><th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;">الفصل2</th><th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;">السعي</th><th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;">النهائي</th><th style="background:var(--primary-dark);color:#fff;font-size:var(--font-sm);font-weight:900;">النهائية</th>`;
            });
            html += `</tr>`;
            displaySubjects.forEach((sub, subIdx) => {
                const bgColor = subIdx % 2 === 0 ? '#ffffff' : '#f5f3ff';
                html += `<tr style="background:${bgColor}; border-bottom: 3px solid var(--gray-300);"><td class="subject-name-row" style="font-weight:800;font-size:var(--font-base);border-left:4px solid #f59e0b;background:#eef2ff;">${sub}</td>`;
                stageStudents.forEach(student => {
                    let subObj = subjects.find(s => s.name === sub && s.stageId === stageId);
                    let subId = subObj ? subObj.id : sub;
                    const g = getStudentGrade(student.id, subId);
                    const t1 = parseFloat(g.term1) || 0;
                    const mid = parseFloat(g.midYear) || 0;
                    const t2 = parseFloat(g.term2) || 0;
                    const effort = Math.round((t1 + mid + t2) / 3);
                    if (g.annualEffort !== effort.toString()) { g.annualEffort = effort;
                        setStudentGrade(student.id, subId, g); }
                    const final = parseFloat(g.finalExam) || 0;
                    const total = Math.round((effort + final) / 2);
                    if (g.total !== total.toString()) { g.total = total;
                        setStudentGrade(student.id, subId, g); }
                    let totalClass = 'grade-total';
                    if (total < 50) totalClass += ' fail';
                    else if (total >= 85) totalClass += ' pass-high';
                    else if (total >= 70) totalClass += ' pass-mid';
                    html +=
                        `<td><input class="grade-input" type="number" step="0.5" min="0" max="100" value="${g.term1}" onchange="updateGrade('${student.id}','${subId}','term1',this.value)" /></td><td><input class="grade-input" type="number" step="0.5" min="0" max="100" value="${g.midYear}" onchange="updateGrade('${student.id}','${subId}','midYear',this.value)" /></td><td><input class="grade-input" type="number" step="0.5" min="0" max="100" value="${g.term2}" onchange="updateGrade('${student.id}','${subId}','term2',this.value)" /></td><td><span style="font-weight:700;color:#e65100;font-size:var(--font-base);">${effort}</span></td><td><input class="grade-input" type="number" step="0.5" min="0" max="100" value="${g.finalExam}" onchange="updateGrade('${student.id}','${subId}','finalExam',this.value)" /></td><td><span class="${totalClass}">${total}</span></td>`;
                });
                html += `</tr>`;
            });
            html += '</table></div>';
            html +=
                `<div style="margin-top:10px;font-size:var(--font-sm);color:var(--gray-500);"><i class="fas fa-info-circle"></i> السعي = (الفصل1 + نصف السنة + الفصل2) / 3 (مقرب). النهائية = (السعي + الامتحان النهائي) / 2 (مقرب). الدرجة < 50 باللون الأحمر الغامق.</div>`;
            container.innerHTML = html;
        }

        function updateGrade(studentId, subjectId, field, value) {
            const g = getStudentGrade(studentId, subjectId);
            g[field] = value;
            if (field === 'term1' || field === 'midYear' || field === 'term2') {
                const t1 = parseFloat(g.term1) || 0;
                const mid = parseFloat(g.midYear) || 0;
                const t2 = parseFloat(g.term2) || 0;
                const effort = Math.round((t1 + mid + t2) / 3);
                g.annualEffort = effort;
            }
            const effort = parseInt(g.annualEffort) || 0;
            const final = parseFloat(g.finalExam) || 0;
            const total = Math.round((effort + final) / 2);
            g.total = total;
            setStudentGrade(studentId, subjectId, g);
            renderGrades();
            renderLevelChart();
        }

        function saveAllGrades() { toast('تم حفظ جميع الدرجات', 'success');
            renderGrades();
            renderLevelChart(); }

        function addGradeSubject() {
            const name = prompt('أدخل اسم المادة الجديدة:');
            if (name && name.trim()) { gradeSubjects.push(name.trim());
                saveAllData();
                renderGrades();
                toast('تم إضافة المادة', 'success'); }
        }

        function removeGradeSubject() {
            const name = prompt('أدخل اسم المادة المراد حذفها:');
            if (name && name.trim()) {
                const idx = gradeSubjects.indexOf(name.trim());
                if (idx > -1) { gradeSubjects.splice(idx, 1);
                    saveAllData();
                    renderGrades();
                    toast('تم حذف المادة', 'success'); } else { toast('المادة غير موجودة', 'error'); }
            }
        }

        // ============================================================
        // ATTENDANCE (محسّن)
        // ============================================================
        function populateAttendanceFilters() {
            const el = document.getElementById('attendanceStageFilter');
            const val = el.value;
            el.innerHTML = '<option value="">اختر المرحلة</option>';
            stages.forEach(s => { el.innerHTML += `<option value="${s.id}">${s.name}</option>`; });
            if (val && stages.some(s => s.id === val)) el.value = val;
            updateAttendanceSections();
            const dateInput = document.getElementById('attendanceDate');
            if (!dateInput.value) {
                const now = new Date();
                dateInput.value = now.getFullYear() + '-' + String(now.getMonth() + 1).padStart(2, '0') + '-' + String(now
                    .getDate()).padStart(2, '0');
            }
            document.getElementById('absenceLimitInput').value = absenceLimit || 5;
        }

        function updateAttendanceSections() {
            const stageId = document.getElementById('attendanceStageFilter').value;
            const el = document.getElementById('attendanceSectionFilter');
            const val = el.value;
            el.innerHTML = '<option value="">اختر الشعبة</option>';
            const stage = stages.find(s => s.id === stageId);
            if (stage) { stage.sections.forEach(sec => { el.innerHTML += `<option value="${sec.id}">${sec.name}</option>`; }); }
            if (val && stage && stage.sections.some(s => s.id === val)) el.value = val;
        }

        document.querySelectorAll('.tab-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                this.classList.add('active');
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                document.getElementById(this.dataset.tab).classList.add('active');
                renderAttendance();
            });
        });

        function renderAttendance() {
            const stageId = document.getElementById('attendanceStageFilter').value;
            const sectionId = document.getElementById('attendanceSectionFilter').value;
            const date = document.getElementById('attendanceDate').value;
            const searchTerm = document.getElementById('attendanceSearchInput').value.trim().toLowerCase();

            let stageStudents = students.filter(s => s.stageId === stageId && (sectionId ? s.sectionId === sectionId : true));
            if (searchTerm) {
                stageStudents = stageStudents.filter(s => s.name.toLowerCase().includes(searchTerm));
            }

            if (!stageId || !sectionId || !stageStudents.length) {
                const msg = !stageId || !sectionId ? 'اختر المرحلة والشعبة' : 'لا يوجد طلاب مطابقين للبحث';
                ['attendanceDailyContainer', 'attendanceWeeklyContainer', 'attendanceMonthlyContainer',
                    'attendanceYearlyContainer'
                ].forEach(id => {
                    document.getElementById(id).innerHTML =
                        `<div class="empty-state"><i class="fas fa-calendar-check"></i><p>${msg}</p></div>`;
                });
                document.getElementById('attendanceSummary').innerHTML = '';
                return;
            }

            const activeTab = document.querySelector('.tab-btn.active');
            if (activeTab) {
                const tabId = activeTab.dataset.tab;
                if (tabId === 'attendance-daily') renderAttendanceDaily(stageStudents, date);
                else if (tabId === 'attendance-weekly') renderAttendanceWeekly(stageStudents, date);
                else if (tabId === 'attendance-monthly') renderAttendanceMonthly(stageStudents, date);
                else if (tabId === 'attendance-yearly') renderAttendanceYearly(stageStudents, date);
            }
        }

        function getAbsenceWarnings(students) {
            const limit = getAbsenceLimit();
            const warnings = [];
            students.forEach(s => {
                const absences = countStudentAbsences(s.id);
                if (absences >= limit) {
                    warnings.push({ student: s, absences: absences, limit: limit });
                }
            });
            return warnings;
        }

        function renderAttendanceDaily(students, date) {
            const container = document.getElementById('attendanceDailyContainer');
            if (!date) {
                container.innerHTML = '<div class="empty-state"><i class="fas fa-calendar-day"></i><p>اختر التاريخ</p></div>';
                updateSummary(students, date);
                return;
            }
            const dayNames = ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة', 'السبت'];
            const d = new Date(date);
            const dayName = dayNames[d.getDay()];

            const warnings = getAbsenceWarnings(students);
            let warningHtml = '';
            if (warnings.length > 0) {
                warningHtml = `<div class="absence-warning danger"><i class="fas fa-exclamation-triangle"></i> <strong>تنبيه:</strong> الطلاب التاليين تجاوزوا الحد الأقصى للغياب (${getAbsenceLimit()} أيام): `;
                warningHtml += warnings.map(w =>
                    `<span style="font-weight:700;">${w.student.name} (${w.absences} يوم)</span>`
                ).join('، ');
                warningHtml += `</div>`;
            }

            let html = warningHtml;
            html += `<div style="margin-bottom:10px;font-weight:700;font-size:var(--font-base);color:var(--gray-800);"><i class="fas fa-calendar-day"></i> ${dayName} - ${date}</div>`;
            html +=
                `<table><thead><tr><th>#</th><th>الطالب</th><th>الغياب الكلي</th><th>الحالة</th><th>إرسال تبليغ</th></tr></thead><tbody>`;
            students.forEach((s, i) => {
                const status = getStudentAttendance(date, s.id);
                const totalAbs = countStudentAbsences(s.id);
                const limit = getAbsenceLimit();
                const isExceeded = totalAbs >= limit;
                const statusLabels = { present: 'حاضر', absent: 'غائب', late: 'متأخر', leave: 'مجاز' };
                let whatsappBtn = '';
                if (status === 'absent' || status === 'late') {
                    const msg = `الطالب ${s.name} بتاريخ ${date} : الحالة ${statusLabels[status]}`;
                    whatsappBtn =
                        `<button class="whatsapp-btn" onclick="sendWhatsApp('${s.id}','${msg}')"><i class="fab fa-whatsapp"></i> تبليغ</button>`;
                }
                const rowClass = isExceeded ? 'absence-exceed' : '';
                html +=
                    `<tr class="${rowClass}"><td>${i+1}</td><td>${s.name} ${isExceeded ? '<span class="absence-warn-badge" title="تجاوز حد الغياب">!</span>' : ''}</td><td style="font-weight:700;color:${isExceeded ? '#dc3545' : 'var(--gray-800)'};">${totalAbs}</td><td><button class="attendance-btn present ${status === 'present' ? 'active-status' : ''}" onclick="setAttendance('${date}','${s.id}','present')">حاضر</button><button class="attendance-btn absent ${status === 'absent' ? 'active-status' : ''}" onclick="setAttendance('${date}','${s.id}','absent')">غائب</button><button class="attendance-btn late ${status === 'late' ? 'active-status' : ''}" onclick="setAttendance('${date}','${s.id}','late')">متأخر</button><button class="attendance-btn leave ${status === 'leave' ? 'active-status' : ''}" onclick="setAttendance('${date}','${s.id}','leave')">مجاز</button></td><td>${whatsappBtn}</td></tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
            updateSummary(students, date);
        }

        function renderAttendanceWeekly(students, date) {
            const container = document.getElementById('attendanceWeeklyContainer');
            if (!date) {
                container.innerHTML = '<div class="empty-state"><i class="fas fa-calendar-week"></i><p>اختر التاريخ</p></div>';
                return;
            }
            const currentDate = new Date(date);
            const dayOfWeek = currentDate.getDay();
            const startDate = new Date(currentDate);
            startDate.setDate(currentDate.getDate() - dayOfWeek);
            const endDate = new Date(startDate);
            endDate.setDate(startDate.getDate() + 4);

            const days = [];
            for (let d = new Date(startDate); d <= endDate; d.setDate(d.getDate() + 1)) {
                const ds = d.toISOString().split('T')[0];
                const dayNames = ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس'];
                days.push({ date: ds, label: dayNames[d.getDay()] });
            }

            const warnings = getAbsenceWarnings(students);
            let warningHtml = '';
            if (warnings.length > 0) {
                warningHtml = `<div class="absence-warning danger"><i class="fas fa-exclamation-triangle"></i> <strong>تنبيه:</strong> `;
                warningHtml += warnings.map(w =>
                    `<span style="font-weight:700;">${w.student.name} (${w.absences} غياب)</span>`
                ).join('، ');
                warningHtml += ` تجاوزوا الحد الأقصى للغياب (${getAbsenceLimit()} أيام)</div>`;
            }

            let html = warningHtml;
            html +=
                `<div style="margin-bottom:10px;font-weight:700;font-size:var(--font-base);color:var(--gray-800);"><i class="fas fa-calendar-week"></i> الأسبوع: ${startDate.toISOString().split('T')[0]} إلى ${endDate.toISOString().split('T')[0]}</div>`;
            html += `<table><thead><tr><th>الطالب</th><th>الغياب الكلي</th>`;
            days.forEach(d => { html += `<th>${d.label}<br><span style="font-size:var(--font-sm);color:var(--gray-500);">${d.date}</span></th>`; });
            html += `<th>حاضر</th><th>غائب</th><th>متأخر</th><th>مجاز</th></tr></thead><tbody>`;

            students.forEach(s => {
                let present = 0,
                    absent = 0,
                    late = 0,
                    leave = 0;
                const totalAbs = countStudentAbsences(s.id);
                const isExceeded = totalAbs >= getAbsenceLimit();
                const rowClass = isExceeded ? 'absence-exceed' : '';
                html += `<tr class="${rowClass}"><td><strong>${s.name} ${isExceeded ? '<span class="absence-warn-badge">!</span>' : ''}</strong></td><td style="font-weight:700;color:${isExceeded ? '#dc3545' : 'var(--gray-800)'};">${totalAbs}</td>`;
                days.forEach(d => {
                    const status = getStudentAttendance(d.date, s.id);
                    const cls = 'day-status-badge ' + status;
                    const labels = { present: 'ح', absent: 'غ', late: 'ت', leave: 'م' };
                    if (status === 'present') present++;
                    else if (status === 'absent') absent++;
                    else if (status === 'late') late++;
                    else if (status === 'leave') leave++;
                    html += `<td><span class="${cls}">${labels[status] || '-'}</span></td>`;
                });
                html +=
                    `<td style="color:#2e7d32;">${present}</td><td style="color:#c62828;">${absent}</td><td style="color:#e65100;">${late}</td><td style="color:#0d47a1;">${leave}</td>`;
                html += `</tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
            let totalP = 0,
                totalA = 0,
                totalL = 0,
                totalLe = 0;
            students.forEach(s => {
                days.forEach(d => {
                    const status = getStudentAttendance(d.date, s.id);
                    if (status === 'present') totalP++;
                    else if (status === 'absent') totalA++;
                    else if (status === 'late') totalL++;
                    else if (status === 'leave') totalLe++;
                });
            });
            const totalDays = days.length * students.length || 1;
            document.getElementById('attendanceSummary').innerHTML =
                `<div class="stat-box present-box"><div class="num">${totalP}</div><div class="label">حاضر</div></div><div class="stat-box absent-box"><div class="num">${totalA}</div><div class="label">غائب</div></div><div class="stat-box late-box"><div class="num">${totalL}</div><div class="label">متأخر</div></div><div class="stat-box leave-box"><div class="num">${totalLe}</div><div class="label">مجاز</div></div><div class="stat-box total-box"><div class="num">${students.length}</div><div class="label">الطلاب</div></div><div class="stat-box pct-box"><div class="num">${Math.round((totalP/totalDays)*100)}%</div><div class="label">نسبة الحضور</div></div>`;
        }

        function renderAttendanceMonthly(students, date) {
            const container = document.getElementById('attendanceMonthlyContainer');
            if (!date) {
                container.innerHTML = '<div class="empty-state"><i class="fas fa-calendar-alt"></i><p>اختر التاريخ</p></div>';
                return;
            }
            const currentDate = new Date(date);
            const year = currentDate.getFullYear();
            const month = currentDate.getMonth();
            const daysInMonth = new Date(year, month + 1, 0).getDate();
            const dayNames = ['أحد', 'إثن', 'ثلاث', 'أرب', 'خميس'];

            const warnings = getAbsenceWarnings(students);
            let warningHtml = '';
            if (warnings.length > 0) {
                warningHtml = `<div class="absence-warning danger"><i class="fas fa-exclamation-triangle"></i> <strong>تنبيه:</strong> `;
                warningHtml += warnings.map(w =>
                    `<span style="font-weight:700;">${w.student.name} (${w.absences} غياب)</span>`
                ).join('، ');
                warningHtml += ` تجاوزوا الحد الأقصى للغياب (${getAbsenceLimit()} أيام)</div>`;
            }

            let html = warningHtml;
            html +=
                `<div style="margin-bottom:10px;font-weight:700;font-size:var(--font-base);color:var(--gray-800);"><i class="fas fa-calendar-alt"></i> ${currentDate.toLocaleDateString('ar-EG', { month: 'long', year: 'numeric' })}</div>`;
            html += `<table><thead><tr><th>الطالب</th><th>الغياب الكلي</th>`;
            for (let d = 1; d <= daysInMonth; d++) {
                const dt = new Date(year, month, d);
                const dayOfWeek = dt.getDay();
                if (dayOfWeek >= 0 && dayOfWeek <= 4) {
                    html += `<th style="font-size:var(--font-sm);">${d}<br>${dayNames[dayOfWeek]||''}</th>`;
                }
            }
            html += `<th>حاضر</th><th>غائب</th><th>متأخر</th><th>مجاز</th></tr></thead><tbody>`;

            students.forEach(s => {
                let present = 0,
                    absent = 0,
                    late = 0,
                    leave = 0;
                const totalAbs = countStudentAbsences(s.id);
                const isExceeded = totalAbs >= getAbsenceLimit();
                const rowClass = isExceeded ? 'absence-exceed' : '';
                html += `<tr class="${rowClass}"><td><strong>${s.name} ${isExceeded ? '<span class="absence-warn-badge">!</span>' : ''}</strong></td><td style="font-weight:700;color:${isExceeded ? '#dc3545' : 'var(--gray-800)'};">${totalAbs}</td>`;
                for (let d = 1; d <= daysInMonth; d++) {
                    const dt = new Date(year, month, d);
                    const dayOfWeek = dt.getDay();
                    if (dayOfWeek >= 0 && dayOfWeek <= 4) {
                        const dateStr =
                            `${year}-${String(month+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
                        const status = getStudentAttendance(dateStr, s.id);
                        const cls = 'day-status-badge ' + status;
                        const labels = { present: 'ح', absent: 'غ', late: 'ت', leave: 'م' };
                        if (status === 'present') present++;
                        else if (status === 'absent') absent++;
                        else if (status === 'late') late++;
                        else if (status === 'leave') leave++;
                        html += `<td><span class="${cls}">${labels[status] || '-'}</span></td>`;
                    }
                }
                html +=
                    `<td style="color:#2e7d32;">${present}</td><td style="color:#c62828;">${absent}</td><td style="color:#e65100;">${late}</td><td style="color:#0d47a1;">${leave}</td>`;
                html += `</tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function renderAttendanceYearly(students, date) {
            const container = document.getElementById('attendanceYearlyContainer');
            if (!date) {
                container.innerHTML = '<div class="empty-state"><i class="fas fa-calendar"></i><p>اختر التاريخ</p></div>';
                return;
            }
            const currentDate = new Date(date);
            const year = currentDate.getFullYear();
            const months = ['يناير', 'فبراير', 'مارس', 'أبريل', 'مايو', 'يونيو', 'يوليو', 'أغسطس', 'سبتمبر', 'أكتوبر', 'نوفمبر',
                'ديسمبر'
            ];

            const warnings = getAbsenceWarnings(students);
            let warningHtml = '';
            if (warnings.length > 0) {
                warningHtml = `<div class="absence-warning danger"><i class="fas fa-exclamation-triangle"></i> <strong>تنبيه:</strong> `;
                warningHtml += warnings.map(w =>
                    `<span style="font-weight:700;">${w.student.name} (${w.absences} غياب)</span>`
                ).join('، ');
                warningHtml += ` تجاوزوا الحد الأقصى للغياب (${getAbsenceLimit()} أيام)</div>`;
            }

            let html = warningHtml;
            html +=
                `<div style="margin-bottom:10px;font-weight:700;font-size:var(--font-base);color:var(--gray-800);"><i class="fas fa-calendar"></i> السنة: ${year}</div>`;
            html += `<table><thead><tr><th>الطالب</th><th>الغياب الكلي</th>`;
            for (let m = 0; m < 12; m++) {
                html += `<th style="font-size:var(--font-sm);">${months[m].substring(0,3)}</th>`;
            }
            html += `<th>حاضر</th><th>غائب</th><th>متأخر</th><th>مجاز</th></tr></thead><tbody>`;

            students.forEach(s => {
                let totalP = 0,
                    totalA = 0,
                    totalL = 0,
                    totalLe = 0;
                const totalAbs = countStudentAbsences(s.id);
                const isExceeded = totalAbs >= getAbsenceLimit();
                const rowClass = isExceeded ? 'absence-exceed' : '';
                html += `<tr class="${rowClass}"><td><strong>${s.name} ${isExceeded ? '<span class="absence-warn-badge">!</span>' : ''}</strong></td><td style="font-weight:700;color:${isExceeded ? '#dc3545' : 'var(--gray-800)'};">${totalAbs}</td>`;
                for (let m = 0; m < 12; m++) {
                    const daysInMonth = new Date(year, m + 1, 0).getDate();
                    let p = 0,
                        a = 0,
                        l = 0,
                        le = 0;
                    let totalDays = 0;
                    for (let d = 1; d <= daysInMonth; d++) {
                        const dt = new Date(year, m, d);
                        const dayOfWeek = dt.getDay();
                        if (dayOfWeek >= 0 && dayOfWeek <= 4) {
                            const dateStr =
                                `${year}-${String(m+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
                            const status = getStudentAttendance(dateStr, s.id);
                            if (status === 'present') { p++;
                                totalP++; } else if (status === 'absent') { a++;
                                totalA++; } else if (status === 'late') { l++;
                                totalL++; } else if (status === 'leave') { le++;
                                totalLe++; }
                            totalDays++;
                        }
                    }
                    const pct = totalDays > 0 ? Math.round((p / totalDays) * 100) : 0;
                    html += `<td>${pct}%</td>`;
                }
                html +=
                    `<td style="color:#2e7d32;">${totalP}</td><td style="color:#c62828;">${totalA}</td><td style="color:#e65100;">${totalL}</td><td style="color:#0d47a1;">${totalLe}</td>`;
                html += `</tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function updateSummary(students, date) {
            if (!date || !students.length) {
                document.getElementById('attendanceSummary').innerHTML = '';
                return;
            }
            let present = 0,
                absent = 0,
                late = 0,
                leave = 0;
            students.forEach(s => {
                const status = getStudentAttendance(date, s.id);
                if (status === 'present') present++;
                else if (status === 'absent') absent++;
                else if (status === 'late') late++;
                else if (status === 'leave') leave++;
            });
            const total = students.length || 1;
            document.getElementById('attendanceSummary').innerHTML =
                `<div class="stat-box present-box"><div class="num">${present}</div><div class="label">حاضر</div></div><div class="stat-box absent-box"><div class="num">${absent}</div><div class="label">غائب</div></div><div class="stat-box late-box"><div class="num">${late}</div><div class="label">متأخر</div></div><div class="stat-box leave-box"><div class="num">${leave}</div><div class="label">مجاز</div></div><div class="stat-box total-box"><div class="num">${students.length}</div><div class="label">الطلاب</div></div><div class="stat-box pct-box"><div class="num">${Math.round((present/total)*100)}%</div><div class="label">نسبة الحضور</div></div>`;
        }

        function setAttendance(date, studentId, status) {
            setStudentAttendance(date, studentId, status);
            renderAttendance();
            toast('تم تحديث الحضور', 'success');
        }

        function markAllPresent() {
            const stageId = document.getElementById('attendanceStageFilter').value;
            const sectionId = document.getElementById('attendanceSectionFilter').value;
            const date = document.getElementById('attendanceDate').value;
            if (!stageId || !sectionId || !date) { toast('اختر المرحلة والشعبة والتاريخ أولاً', 'error'); return; }
            const stageStudents = students.filter(s => s.stageId === stageId && s.sectionId === sectionId);
            stageStudents.forEach(s => { setStudentAttendance(date, s.id, 'present'); });
            renderAttendance();
            toast('تم تحديد جميع الطلاب حضور', 'success');
        }

        function saveAttendance() { toast('تم حفظ سجل الحضور', 'success');
            renderAttendance(); }

        // ============================================================
        // SCHEDULE
        // ============================================================
        const dayNames = ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس'];
        const periodNames = ['الدرس الأول', 'الدرس الثاني', 'الدرس الثالث', 'الدرس الرابع', 'الدرس الخامس', 'الدرس السادس'];

        function populateScheduleFilters() {
            const stageEl = document.getElementById('scheduleStageFilter');
            const sectionEl = document.getElementById('scheduleSectionFilter');
            const stageVal = stageEl.value;
            const sectionVal = sectionEl.value;
            stageEl.innerHTML = '<option value="">اختر المرحلة</option>';
            stages.forEach(s => { stageEl.innerHTML += `<option value="${s.id}">${s.name}</option>`; });
            if (stageVal && stages.some(s => s.id === stageVal)) stageEl.value = stageVal;
            updateScheduleSections();
            if (sectionVal) {
                const stage = stages.find(s => s.id === stageEl.value);
                if (stage && stage.sections.some(sec => sec.id === sectionVal)) sectionEl.value = sectionVal;
            }
            updateScheduleSubjects();
        }

        function updateScheduleSections() {
            const stageId = document.getElementById('scheduleStageFilter').value;
            const el = document.getElementById('scheduleSectionFilter');
            const val = el.value;
            el.innerHTML = '<option value="">اختر الشعبة</option>';
            const stage = stages.find(s => s.id === stageId);
            if (stage) { stage.sections.forEach(sec => { el.innerHTML += `<option value="${sec.id}">${sec.name}</option>`; }); }
            if (val && stage && stage.sections.some(s => s.id === val)) el.value = val;
        }

        function updateScheduleSubjects() {}

        document.getElementById('scheduleStageFilter').addEventListener('change', function() {
            updateScheduleSections();
            updateScheduleSubjects();
            renderSchedule();
        });
        document.getElementById('scheduleSectionFilter').addEventListener('change', renderSchedule);

        function renderSchedule() {
            const container = document.getElementById('scheduleContainer');
            const stageId = document.getElementById('scheduleStageFilter').value;
            const sectionId = document.getElementById('scheduleSectionFilter').value;
            if (!stageId || !sectionId) {
                container.innerHTML =
                    '<div class="empty-state"><i class="fas fa-table"></i><p>اختر المرحلة والشعبة لعرض الجدول</p></div>';
                return;
            }
            const prefix = stageId + '_' + sectionId + '_';
            let html =
                `<table class="schedule-table"><thead><tr><th style="background:linear-gradient(135deg,var(--primary),var(--primary-dark));color:#fff;font-size:var(--font-base);font-weight:800;">الفترة</th>`;
            dayNames.forEach((d, idx) => {
                const isWeekend = (idx === 4);
                html +=
                    `<th class="day-header ${isWeekend ? 'weekend' : ''}" style="font-size:var(--font-base);font-weight:900;">${d}</th>`;
            });
            html += `</tr></thead><tbody>`;
            periodNames.forEach((period, pIdx) => {
                html += `<tr><td class="period-label">${period}</td>`;
                dayNames.forEach((day, dIdx) => {
                    const key = prefix + dIdx + '_' + pIdx;
                    const entry = schedule[key];
                    if (entry) {
                        const teacherName = entry.teacherName || getTeacherName(entry.subjectId) || '';
                        html +=
                            `<td class="subject-cell">${entry.subjectName}<span class="teacher-name" style="font-size:var(--font-sm);color:var(--gray-500);display:block;">${teacherName}</span></td>`;
                    } else { html += `<td class="empty-cell">-</td>`; }
                });
                html += `</tr>`;
            });
            html += '</tbody></table>';
            container.innerHTML = html;
        }

        function openScheduleModal() {
            const stageId = document.getElementById('scheduleStageFilter').value;
            const sectionId = document.getElementById('scheduleSectionFilter').value;
            if (!stageId || !sectionId) { toast('اختر المرحلة والشعبة أولاً', 'error'); return; }

            let dayOpts = '',
                periodOpts = '',
                subjectOpts = '';
            dayNames.forEach((d, i) => { dayOpts += `<option value="${i}">${d}</option>`; });
            periodNames.forEach((p, i) => { periodOpts += `<option value="${i}">${p}</option>`; });

            const stageSubjects = subjects.filter(s => s.stageId === stageId);
            if (stageSubjects.length > 0) {
                stageSubjects.forEach(s => {
                    subjectOpts += `<option value="${s.id}">${s.name}</option>`;
                });
            } else {
                subjectOpts += `<option value="">⚠️ لا توجد مواد مسجلة</option>`;
            }

            document.getElementById('modalTitle').innerHTML = `<i class="fas fa-plus-circle"></i> إضافة حصة دراسية`;
            document.getElementById('modalBody').innerHTML = `
                        <div class="form-row">
                            <div class="form-group">
                                <label>اليوم</label>
                                <select id="fScheduleDay">${dayOpts}</select>
                            </div>
                            <div class="form-group">
                                <label>الفترة</label>
                                <select id="fSchedulePeriod">${periodOpts}</select>
                            </div>
                        </div>
                        <div class="form-group subject-input-wrapper">
                            <label>المادة</label>
                            <select id="fScheduleSubject">${subjectOpts}</select>
                            <div class="or-divider">أو</div>
                            <input type="text" id="fScheduleSubjectManual" placeholder="اكتب اسم المادة يدوياً..." />
                            <span style="font-size:var(--font-sm);color:var(--gray-500);">يمكنك اختيار مادة من القائمة أو كتابة اسم مادة جديد</span>
                        </div>
                        <div class="form-group">
                            <label>اسم المدرس (اختياري)</label>
                            <input type="text" id="fScheduleTeacherName" placeholder="اسم المدرس" />
                        </div>
                    `;
            document.getElementById('modalSaveBtn').dataset.action = 'schedule';
            document.getElementById('modalSaveBtn').textContent = 'إضافة حصة';
            document.getElementById('modalOverlay').classList.add('open');
        }

        function saveScheduleEntry() {
            const stageId = document.getElementById('scheduleStageFilter').value;
            const sectionId = document.getElementById('scheduleSectionFilter').value;
            const day = parseInt(document.getElementById('fScheduleDay').value);
            const period = parseInt(document.getElementById('fSchedulePeriod').value);
            const selectedSubjectId = document.getElementById('fScheduleSubject').value;
            const manualSubject = document.getElementById('fScheduleSubjectManual').value.trim();
            const teacherName = document.getElementById('fScheduleTeacherName').value.trim();

            if (!stageId || !sectionId) { toast('الرجاء اختيار المرحلة والشعبة', 'error'); return; }

            let subjectName = '';
            let subjectId = null;

            if (manualSubject) {
                subjectName = manualSubject;
                const existing = subjects.find(s => s.name === manualSubject && s.stageId === stageId);
                if (existing) {
                    subjectId = existing.id;
                } else {
                    const newSubject = { id: generateId(), name: manualSubject, stageId: stageId, teacherId: null };
                    subjects.push(newSubject);
                    saveAllData();
                    subjectId = newSubject.id;
                    toast('تم إنشاء مادة جديدة: ' + manualSubject, 'success');
                }
            } else if (selectedSubjectId) {
                const subject = subjects.find(s => s.id === selectedSubjectId);
                if (subject) {
                    subjectName = subject.name;
                    subjectId = subject.id;
                } else {
                    toast('المادة غير موجودة', 'error');
                    return;
                }
            } else {
                toast('الرجاء إدخال اسم المادة أو اختيارها من القائمة', 'error');
                return;
            }

            const key = stageId + '_' + sectionId + '_' + day + '_' + period;
            schedule[key] = {
                subjectId: subjectId,
                subjectName: subjectName,
                teacherName: teacherName || getTeacherName(subjectId) || ''
            };
            saveAllData();
            closeModal();
            renderSchedule();
            toast('تم إضافة الحصة: ' + subjectName, 'success');
            document.getElementById('modalSaveBtn').dataset.action = '';
            document.getElementById('modalSaveBtn').textContent = 'حفظ';
        }

        function clearSchedule() {
            const stageId = document.getElementById('scheduleStageFilter').value;
            const sectionId = document.getElementById('scheduleSectionFilter').value;
            if (!stageId || !sectionId) { toast('اختر المرحلة والشعبة أولاً', 'error'); return; }
            if (!confirm('هل أنت متأكد من مسح جميع حصص هذا الجدول؟')) return;
            const prefix = stageId + '_' + sectionId + '_';
            Object.keys(schedule).forEach(key => { if (key.startsWith(prefix)) delete schedule[key]; });
            saveAllData();
            renderSchedule();
            toast('تم مسح الجدول', 'success');
        }

        // ============================================================
        // SETTINGS
        // ============================================================
        function loadSettings() {
            document.getElementById('settingsUsername').value = settings.username || '';
            document.getElementById('settingsPassword').value = '';
            document.getElementById('settingsPasswordConfirm').value = '';
        }

        function saveSettings() {
            const username = document.getElementById('settingsUsername').value.trim();
            const pass = document.getElementById('settingsPassword').value;
            const passConfirm = document.getElementById('settingsPasswordConfirm').value;
            if (!username) { toast('الرجاء إدخال اسم المستخدم', 'error'); return; }
            if (pass && pass !== passConfirm) { toast('كلمة المرور غير متطابقة', 'error'); return; }
            settings.username = username;
            if (pass) settings.password = pass;
            saveAllData();
            toast('تم حفظ الإعدادات', 'success');
        }

        // ============================================================
        // MODAL HELPERS
        // ============================================================
        function closeModal() {
            document.getElementById('modalOverlay').classList.remove('open');
            document.getElementById('modalSaveBtn').dataset.action = '';
            document.getElementById('modalSaveBtn').textContent = 'حفظ';
        }

        function saveModal() {
            const action = document.getElementById('modalSaveBtn').dataset.action;
            if (action === 'whatsapp') { sendWhatsAppMessage(); return; }
            if (action === 'schedule') { saveScheduleEntry(); return; }
            const title = document.getElementById('modalTitle').textContent;
            if (title.includes('مرحلة')) saveStage();
            else if (title.includes('طالب')) saveStudent();
            else if (title.includes('مدرس')) saveTeacher();
            else if (title.includes('مادة')) saveSubject();
            else if (title.includes('ولي أمر')) saveParent();
            else { toast('حدث خطأ', 'error'); }
        }
        document.getElementById('modalOverlay').addEventListener('click', function(e) { if (e.target === this) closeModal(); });

        // ============================================================
        // INIT APP
        // ============================================================
        function initApp() {
            document.getElementById('loginUser').value = settings.username || 'admin';
            document.getElementById('loginPass').value = settings.password || '123';

            if (!stages.length) {
                const stageNames = ['الأول متوسط', 'الثاني متوسط', 'الثالث متوسط', 'الرابع العلمي', 'الخامس العلمي', 'السادس العلمي'];
                stageNames.forEach(name => {
                    const sections = ['أ', 'ب', 'ج'].map(n => ({ id: generateId(), name: n }));
                    stages.push({ id: generateId(), name, sections });
                });
                saveAllData();
            }

            if (!students.length) {
                const sampleNames = ['محمد السعيد', 'ليلى أحمد', 'خالد عمر', 'نورة سعد', 'فيصل مبارك', 'أحمد علي', 'سارة خالد',
                    'عمر حسن'
                ];
                stages.forEach((stage, idx) => {
                    const sec = stage.sections[0] || stage.sections[0];
                    if (sec) {
                        const count = idx === 0 ? 3 : 2;
                        for (let i = 0; i < count && sampleNames.length > 0; i++) {
                            const name = sampleNames.pop();
                            if (name) {
                                students.push({ id: generateId(), name, stageId: stage.id, sectionId: sec.id,
                                    parentId: null, parentPhone: '' });
                            }
                        }
                    }
                });
                saveAllData();
            }

            if (!teachers.length) {
                teachers = [
                    { id: generateId(), name: 'د. أحمد زكي', specialty: 'رياضيات', email: 'ahmed@school.edu' },
                    { id: generateId(), name: 'د. سامية حسن', specialty: 'فيزياء', email: 'samia@school.edu' },
                    { id: generateId(), name: 'أ. خالد يوسف', specialty: 'لغة عربية', email: 'khaled@school.edu' },
                    { id: generateId(), name: 'أ. نورة علي', specialty: 'لغة إنجليزية', email: 'nora@school.edu' },
                ];
                saveAllData();
            }

            if (!subjects.length) {
                const subNames = ['الرياضيات', 'الفيزياء', 'الكيمياء', 'الأحياء', 'اللغة العربية', 'اللغة الإنجليزية', 'التاريخ',
                    'الجغرافيا'
                ];
                stages.forEach((stage, idx) => {
                    const count = idx === 0 ? 3 : 2;
                    for (let i = 0; i < count && subNames.length > 0; i++) {
                        const name = subNames.pop();
                        if (name) {
                            const teacher = teachers[idx % teachers.length] || teachers[0];
                            subjects.push({ id: generateId(), name, stageId: stage.id, teacherId: teacher ? teacher
                                    .id : null });
                        }
                    }
                });
                saveAllData();
            }

            if (!gradeSubjects.length) {
                gradeSubjects = ['الرياضيات', 'اللغة العربية', 'العلوم', 'الدراسات'];
                saveAllData();
            }

            populateStageFilters();
            populateGradeFilters();
            populateAttendanceFilters();
            populateScheduleFilters();
            updateDashboard();
            updateBadges();
            renderStages();
            renderStudents();
            renderTeachers();
            renderSubjects();
            renderParents();
            renderCalendar();
            renderDashChart();
            renderLevelChart();
            loadSettings();

            const dateInput = document.getElementById('attendanceDate');
            if (!dateInput.value) {
                const now = new Date();
                dateInput.value = now.getFullYear() + '-' + String(now.getMonth() + 1).padStart(2, '0') + '-' + String(now
                    .getDate()).padStart(2, '0');
            }
            document.getElementById('absenceLimitInput').value = absenceLimit || 5;

            navigateTo('dashboard');
        }

        // ============================================================
        // START
        // ============================================================
        document.getElementById('loginScreen').classList.add('active');
        document.getElementById('mainContent').style.display = 'none';
        document.getElementById('loginUser').value = settings.username || 'admin';
        document.getElementById('loginPass').value = settings.password || '123';

        console.log('✅ مدرستي – نظام إدارة المدارس يعمل بنجاح!');
        console.log('📊 البيانات مخزنة في localStorage');
    </script>
</body>
</html>
