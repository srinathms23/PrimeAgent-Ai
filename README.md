<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="PRIME AGENT — AI-powered inter-college event discovery and registration portal with glassmorphic UI, cognitive chatbot, and instant QR e-tickets.">
    <title>EventAgent Prime | Knowfest AI Hub</title>
    <!-- CDN: Bootstrap 5, FontAwesome 6, jsPDF -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Outfit:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
/* ============================================================
   THEME VARIABLES
   ============================================================ */
:root {
    --font-heading: 'Outfit', 'Inter', sans-serif;
    --font-body: 'Inter', sans-serif;
    --transition-fast: 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    --transition-normal: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    --transition-slow: 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    /* Light Theme */
    --bg-primary: #f5f3ff;
    --bg-secondary: #e8e4f8;
    --bg-gradient: linear-gradient(135deg, #f5f3ff 0%, #e0e7ff 100%);
    --bg-mesh: radial-gradient(at 0% 0%, rgba(99,102,241,.15) 0px, transparent 50%),
               radial-gradient(at 50% 0%, rgba(119, 226, 105, 0.12) 0px, transparent 50%),
               radial-gradient(at 100% 0%, rgba(6,182,212,.1) 0px, transparent 50%);
    --card-bg: rgba(255,255,255,.45);
    --card-border: rgba(99,102,241,.12);
    --card-hover-border: rgba(99,102,241,.25);
    --text-primary: #1e1b4b;
    --text-secondary: #4b5563;
    --text-muted: #6b7280;
    --primary-color: #6366f1;
    --primary-glow: rgba(99,102,241,.3);
    --secondary-color: #a855f7;
    --secondary-glow: rgba(168,85,247,.3);
    --accent-color: #06b6d4;
    --navbar-bg: rgba(255,255,255,.5);
    --glass-blur: blur(16px);
    --shadow-sm: 0 4px 6px -1px rgba(99,102,241,.05);
    --shadow-md: 0 10px 15px -3px rgba(99,102,241,.08);
    --shadow-lg: 0 20px 25px -5px rgba(99,102,241,.12);
    --input-bg: rgba(255,255,255,.7);
    --badge-bg: rgba(99,102,241,.1);
    --badge-text: #4f46e5;
}
[data-theme="dark"] {
    --bg-primary: #0a0618;
    --bg-secondary: #120e2e;
    --bg-gradient: linear-gradient(135deg, #0a0618 0%, #120e25 100%);
    --bg-mesh: radial-gradient(at 0% 0%, rgba(99,102,241,.22) 0px, transparent 50%),
               radial-gradient(at 50% 0%, rgba(168,85,247,.18) 0px, transparent 50%),
               radial-gradient(at 100% 0%, rgba(6,182,212,.15) 0px, transparent 50%);
    --card-bg: rgba(20,16,42,.45);
    --card-border: rgba(255,255,255,.07);
    --card-hover-border: rgba(168,85,247,.3);
    --text-primary: #f3f4f6;
    --text-secondary: #d1d5db;
    --text-muted: #9ca3af;
    --primary-color: #818cf8;
    --primary-glow: rgba(129,140,248,.4);
    --secondary-color: #c084fc;
    --secondary-glow: rgba(192,132,252,.4);
    --accent-color: #22d3ee;
    --navbar-bg: rgba(10,6,24,.5);
    --shadow-sm: 0 4px 6px -1px rgba(0,0,0,.3);
    --shadow-md: 0 10px 15px -3px rgba(0,0,0,.4);
    --shadow-lg: 0 20px 25px -5px rgba(0,0,0,.5);
    --input-bg: rgba(15,10,35,.6);
    --badge-bg: rgba(168,85,247,.15);
    --badge-text: #d8b4fe;
}
/* ============================================================
   BASE RESET
   ============================================================ */
* { margin: 0; padding: 0; box-sizing: border-box; }
body {
    font-family: var(--font-body);
    background: var(--bg-primary);
    background-image: var(--bg-mesh);
    background-attachment: fixed;
    color: var(--text-primary);
    min-height: 100vh;
    overflow-x: hidden;
    line-height: 1.6;
    transition: background var(--transition-normal), color var(--transition-normal);
}
h1,h2,h3,h4,h5,h6 { font-family: var(--font-heading); font-weight: 700; letter-spacing: -.02em; }
a { text-decoration: none; color: var(--primary-color); transition: color var(--transition-fast); }
a:hover { color: var(--secondary-color); }
::-webkit-scrollbar { width: 8px; }
::-webkit-scrollbar-track { background: var(--bg-primary); }
::-webkit-scrollbar-thumb { background: var(--card-border); border-radius: 99px; border: 2px solid var(--bg-primary); }
::-webkit-scrollbar-thumb:hover { background: var(--primary-color); }
/* ============================================================
   UTILITIES
   ============================================================ */
.text-gradient-primary {
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
}
.text-gradient-accent {
    background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
}
.glass-panel {
    background: var(--card-bg);
    backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur);
    border: 1px solid var(--card-border); border-radius: 16px;
    box-shadow: var(--shadow-md);
    transition: transform var(--transition-normal), border-color var(--transition-normal), box-shadow var(--transition-normal);
}
.glass-panel:hover { border-color: var(--card-hover-border); box-shadow: var(--shadow-lg), 0 0 20px var(--primary-glow); }
.glass-card {
    background: var(--card-bg);
    backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur);
    border: 1px solid var(--card-border); border-radius: 16px; padding: 24px;
    transition: transform var(--transition-normal), border-color var(--transition-normal), box-shadow var(--transition-normal);
}
.glass-card:hover { transform: translateY(-5px); border-color: var(--card-hover-border); box-shadow: var(--shadow-lg); }
.btn-gradient {
    background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
    color: #fff !important; border: none; padding: 12px 28px; font-weight: 600;
    border-radius: 30px; letter-spacing: .02em; position: relative; z-index: 1; overflow: hidden;
    box-shadow: 0 4px 15px var(--primary-glow);
    transition: transform var(--transition-fast), box-shadow var(--transition-fast);
}
.btn-gradient::before {
    content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 100%;
    background: linear-gradient(135deg, var(--secondary-color) 0%, var(--primary-color) 100%);
    opacity: 0; z-index: -1; transition: opacity var(--transition-normal);
}
.btn-gradient:hover { transform: translateY(-2px); box-shadow: 0 6px 20px var(--primary-glow), 0 0 10px var(--secondary-glow); }
.btn-gradient:hover::before { opacity: 1; }
.btn-glass {
    background: rgba(255,255,255,.08); backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur);
    border: 1px solid var(--card-border); color: var(--text-primary);
    padding: 11px 26px; font-weight: 600; border-radius: 30px; transition: all var(--transition-fast);
}
.btn-glass:hover { background: rgba(255,255,255,.15); border-color: var(--primary-color); color: var(--primary-color); }
/* ============================================================
   LOADER
   ============================================================ */
#loading-overlay {
    position: fixed; top: 0; left: 0; width: 100%; height: 100%;
    background: var(--bg-primary); z-index: 9999;
    display: flex; justify-content: center; align-items: center;
    transition: opacity var(--transition-slow);
}
.loader-logo { display: flex; flex-direction: column; align-items: center; animation: pulse 1.8s infinite ease-in-out; }
.loader-spinner {
    width: 60px; height: 60px;
    border: 4px solid var(--card-border);
    border-top: 4px solid var(--primary-color);
    border-radius: 50%; animation: spin 1s linear infinite; margin-bottom: 20px;
}
.loader-prime-badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    color: #fff; padding: 3px 12px; border-radius: 20px; font-size: .7rem;
    font-weight: 700; letter-spacing: .08em; text-transform: uppercase; margin-bottom: 8px;
}
/* ============================================================
   NAVBAR
   ============================================================ */
.navbar {
    background: var(--navbar-bg); backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur);
    border-bottom: 1px solid var(--card-border); padding: 15px 0; z-index: 1000;
    transition: background var(--transition-normal);
}
.navbar-brand { font-family: var(--font-heading); font-weight: 800; font-size: 1.5rem; display: flex; align-items: center; gap: 8px; }
.navbar-brand i { background: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
.nav-link { font-weight: 500; color: var(--text-secondary); padding: 8px 16px !important; border-radius: 20px; transition: all var(--transition-fast); }
.nav-link:hover, .nav-link.active { color: var(--primary-color) !important; background: var(--badge-bg); }
.theme-toggle-btn {
    background: none; border: none; color: var(--text-primary); cursor: pointer; font-size: 1.25rem;
    padding: 8px; border-radius: 50%; display: flex; align-items: center; justify-content: center;
    transition: background var(--transition-fast), transform var(--transition-fast);
}
.theme-toggle-btn:hover { background: var(--card-border); transform: rotate(15deg); }
/* ============================================================
   PAGE LAYOUT & TRANSITIONS
   ============================================================ */
.page-view { display: none; opacity: 0; transform: translateY(15px); transition: opacity var(--transition-slow), transform var(--transition-slow); padding: 100px 0 60px; }
.page-view.active { display: block; opacity: 1; transform: translateY(0); }
/* ============================================================
   HOME HERO
   ============================================================ */
.hero-section { position: relative; padding: 80px 0 140px; }
.hero-glow { position: absolute; width: 350px; height: 350px; background: radial-gradient(circle, var(--primary-glow) 0%, transparent 70%); top: -50px; right: 5%; z-index: -1; filter: blur(40px); animation: float-glow 8s infinite alternate ease-in-out; }
.hero-glow-2 { position: absolute; width: 250px; height: 250px; background: radial-gradient(circle, var(--secondary-glow) 0%, transparent 70%); bottom: 50px; left: 5%; z-index: -1; filter: blur(30px); animation: float-glow 6s infinite alternate-reverse ease-in-out; }
.hero-title { font-size: 3.5rem; line-height: 1.15; font-weight: 800; margin-bottom: 24px; }
.hero-subtitle { font-size: 1.2rem; color: var(--text-secondary); margin-bottom: 35px; max-width: 550px; }
.hero-illustration { position: relative; display: flex; justify-content: center; align-items: center; }
.hero-glass-blob {
    width: 100%; max-width: 450px; height: 400px;
    background: linear-gradient(135deg, rgba(255,255,255,.1) 0%, rgba(255,255,255,.03) 100%);
    backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur);
    border: 1px solid rgba(255,255,255,.1);
    border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    box-shadow: var(--shadow-lg), 0 0 30px var(--primary-glow);
    animation: blob-morph 12s infinite alternate ease-in-out, float-animation 6s infinite ease-in-out;
    display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; padding: 40px;
}
.hero-agent-badge {
    position: absolute; background: var(--card-bg); border: 1px solid var(--card-border);
    backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur);
    padding: 12px 20px; border-radius: 16px; box-shadow: var(--shadow-md);
    display: flex; align-items: center; gap: 12px; animation: float-animation 5s infinite ease-in-out;
}
.badge-1 { top: 10%; left: 5%; animation-delay: 0.5s; }
.badge-2 { bottom: 15%; right: 5%; animation-delay: 1.5s; }
.section-title { font-size: 2.25rem; font-weight: 800; margin-bottom: 12px; text-align: center; }
.section-subtitle { color: var(--text-muted); text-align: center; max-width: 600px; margin: 0 auto 50px; }
.feature-icon { width: 60px; height: 60px; border-radius: 16px; display: flex; align-items: center; justify-content: center; font-size: 1.5rem; background: linear-gradient(135deg, var(--primary-glow), var(--secondary-glow)); color: var(--primary-color); margin-bottom: 20px; }
.testimonial-card { height: 100%; display: flex; flex-direction: column; justify-content: space-between; }
.testimonial-rating { color: #fbbf24; margin-bottom: 15px; }
.user-meta { display: flex; align-items: center; gap: 15px; margin-top: 20px; }
.user-avatar-placeholder { width: 45px; height: 45px; border-radius: 50%; background: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); color: #fff; font-weight: 700; display: flex; align-items: center; justify-content: center; font-size: 1rem; }
/* ============================================================
   EVENTS
   ============================================================ */
.search-filter-bar { margin-bottom: 40px; }
.event-card { overflow: hidden; display: flex; flex-direction: column; height: 100%; }
.event-card-img-wrapper { position: relative; height: 200px; overflow: hidden; background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%); }
.event-card-img-overlay { position: absolute; top: 15px; left: 15px; z-index: 2; }
.event-category-badge { background: rgba(15,10,30,.6); backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px); color: #fff; padding: 6px 14px; border-radius: 20px; font-size: .75rem; font-weight: 600; letter-spacing: .05em; text-transform: uppercase; border: 1px solid rgba(255,255,255,.15); }
.event-card-img { width: 100%; height: 100%; object-fit: cover; transition: transform var(--transition-slow); }
.event-card:hover .event-card-img { transform: scale(1.08); }
.event-card-body { display: flex; flex-direction: column; justify-content: space-between; flex-grow: 1; padding-top: 20px; }
.event-meta-item { display: flex; align-items: center; gap: 8px; font-size: .85rem; color: var(--text-secondary); margin-bottom: 8px; }
.event-meta-item i { color: var(--primary-color); }
.seats-indicator { font-size: .85rem; font-weight: 600; }
.seats-badge { padding: 3px 10px; border-radius: 12px; }
.seats-badge.success { background: rgba(16,185,129,.15); color: #10b981; }
.seats-badge.warning { background: rgba(245,158,11,.15); color: #f59e0b; }
.seats-badge.danger { background: rgba(239,68,68,.15); color: #ef4444; }
/* ============================================================
   EVENT DETAILS
   ============================================================ */
.details-header { position: relative; padding: 60px 40px; overflow: hidden; }
.details-grid-item { display: flex; flex-direction: column; gap: 5px; }
.details-grid-label { font-size: .8rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: .05em; }
.speaker-card { display: flex; align-items: center; gap: 20px; margin-top: 20px; }
.schedule-timeline { position: relative; padding-left: 30px; border-left: 2px solid var(--card-border); }
.timeline-item { position: relative; margin-bottom: 30px; }
.timeline-item::before { content: ''; position: absolute; left: -37px; top: 5px; width: 12px; height: 12px; border-radius: 50%; background: var(--primary-color); border: 2px solid var(--bg-primary); box-shadow: 0 0 10px var(--primary-glow); }
/* ============================================================
   REGISTRATION FORM
   ============================================================ */
.form-floating > .form-control { background: var(--input-bg); border: 1px solid var(--card-border); color: var(--text-primary); border-radius: 12px; transition: all var(--transition-normal); }
.form-floating > .form-control:focus { background: var(--input-bg); border-color: var(--primary-color); box-shadow: 0 0 8px var(--primary-glow); }
.form-floating > label { color: var(--text-muted); }
.form-floating > .form-control:focus ~ label, .form-floating > .form-control:not(:placeholder-shown) ~ label { color: var(--primary-color); }
.form-select { background-color: var(--input-bg); border: 1px solid var(--card-border); color: var(--text-primary); border-radius: 12px; height: 58px; padding: .375rem 2.25rem .375rem .75rem; }
.form-select:focus { border-color: var(--primary-color); box-shadow: 0 0 8px var(--primary-glow); background-color: var(--input-bg); color: var(--text-primary); }
.gender-radio-group { background: var(--input-bg); border: 1px solid var(--card-border); border-radius: 12px; padding: 12px 18px; min-height: 58px; display: flex; align-items: center; gap: 20px; }
.invalid-feedback { font-size: .8rem; font-weight: 500; }
/* ============================================================
   CHATBOT
   ============================================================ */
.chat-container { height: 600px; display: flex; flex-direction: column; overflow: hidden; }
.chat-header { padding: 20px; border-bottom: 1px solid var(--card-border); display: flex; align-items: center; gap: 15px; }
.chat-agent-avatar { width: 48px; height: 48px; border-radius: 50%; background: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); display: flex; align-items: center; justify-content: center; color: #fff; font-size: 1.25rem; position: relative; box-shadow: 0 0 10px var(--primary-glow); }
.chat-agent-status { position: absolute; width: 12px; height: 12px; background: #10b981; border: 2px solid var(--bg-primary); border-radius: 50%; bottom: 2px; right: 2px; }
.chat-body { flex-grow: 1; overflow-y: auto; padding: 24px; display: flex; flex-direction: column; gap: 16px; scroll-behavior: smooth; }
.chat-bubble { max-width: 75%; padding: 14px 18px; border-radius: 18px; font-size: .95rem; line-height: 1.45; }
.chat-bubble.bot { background: var(--input-bg); color: var(--text-primary); border: 1px solid var(--card-border); border-top-left-radius: 2px; align-self: flex-start; }
.chat-bubble.user { background: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); color: #fff; border-top-right-radius: 2px; align-self: flex-end; box-shadow: 0 4px 10px var(--primary-glow); }
.quick-reply-wrapper { display: flex; flex-wrap: wrap; gap: 10px; padding: 12px 24px; border-top: 1px solid var(--card-border); }
.quick-reply-btn { background: var(--badge-bg); border: 1px solid var(--card-border); color: var(--primary-color); padding: 8px 16px; border-radius: 20px; font-size: .85rem; font-weight: 500; transition: all var(--transition-fast); cursor: pointer; }
.quick-reply-btn:hover { background: var(--primary-color); color: #fff; border-color: var(--primary-color); transform: translateY(-1px); }
.chat-footer { padding: 16px 24px; border-top: 1px solid var(--card-border); display: flex; gap: 12px; }
.chat-input { background: var(--input-bg); border: 1px solid var(--card-border); color: var(--text-primary); border-radius: 24px; padding: 12px 20px; flex-grow: 1; outline: none; transition: border var(--transition-fast); }
.chat-input:focus { border-color: var(--primary-color); }
.chat-send-btn { width: 48px; height: 48px; border-radius: 50%; background: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); color: #fff; border: none; display: flex; align-items: center; justify-content: center; cursor: pointer; box-shadow: 0 4px 10px var(--primary-glow); transition: transform var(--transition-fast); }
.chat-send-btn:hover { transform: scale(1.05); }
.typing-indicator { display: flex; gap: 5px; padding: 5px 0; }
.typing-dot { width: 8px; height: 8px; background: var(--text-muted); border-radius: 50%; animation: typing-bounce 1.4s infinite ease-in-out; }
.typing-dot:nth-child(2) { animation-delay: .2s; }
.typing-dot:nth-child(3) { animation-delay: .4s; }
/* ============================================================
   ADMIN DASHBOARD
   ============================================================ */
.dashboard-stat-card { padding: 24px; display: flex; justify-content: space-between; align-items: center; }
.dashboard-stat-info h3 { font-size: 2rem; margin-bottom: 2px; }
.dashboard-stat-info p { color: var(--text-muted); margin-bottom: 0; font-size: .9rem; text-transform: uppercase; letter-spacing: .05em; }
.dashboard-stat-icon { width: 56px; height: 56px; border-radius: 14px; display: flex; align-items: center; justify-content: center; font-size: 1.5rem; background: var(--badge-bg); color: var(--primary-color); }
.admin-tabs { border-bottom: 1px solid var(--card-border) !important; gap: 15px; margin-bottom: 25px; }
.admin-tabs .nav-link { border: none !important; background: none !important; color: var(--text-muted) !important; border-radius: 0; border-bottom: 2px solid transparent !important; font-weight: 600; }
.admin-tabs .nav-link.active { color: var(--primary-color) !important; border-bottom-color: var(--primary-color) !important; }
.glass-table { border-radius: 12px; overflow: hidden; border: 1px solid var(--card-border); }
.glass-table table { margin-bottom: 0; background: transparent; color: var(--text-primary); }
.glass-table th { background: rgba(255,255,255,.05) !important; color: var(--text-primary); border-bottom: 1px solid var(--card-border) !important; padding: 15px 20px; font-family: var(--font-heading); font-weight: 600; }
.glass-table td { padding: 15px 20px; border-bottom: 1px solid var(--card-border); vertical-align: middle; }
.table-hover tbody tr:hover { background-color: rgba(99,102,241,.03) !important; }
/* ============================================================
   TOAST SYSTEM
   ============================================================ */
.toast-container { position: fixed; bottom: 24px; right: 24px; z-index: 1050; display: flex; flex-direction: column; gap: 10px; }
.custom-toast { background: var(--card-bg); backdrop-filter: var(--glass-blur); -webkit-backdrop-filter: var(--glass-blur); border: 1px solid var(--card-border); border-left: 4px solid var(--primary-color); padding: 16px 20px; border-radius: 8px; box-shadow: var(--shadow-lg); display: flex; align-items: center; gap: 12px; min-width: 300px; color: var(--text-primary); transform: translateX(120%); animation: toast-slide-in .3s forwards cubic-bezier(.175,.885,.32,1.1); }
.custom-toast.success { border-left-color: #10b981; }
.custom-toast.error { border-left-color: #ef4444; }
.custom-toast.info { border-left-color: #06b6d4; }
.custom-toast.warning { border-left-color: #f59e0b; }
.custom-toast-close { margin-left: auto; background: none; border: none; color: var(--text-muted); cursor: pointer; }
/* ============================================================
   MODALS
   ============================================================ */
.modal-content { background: var(--bg-primary); background-image: var(--bg-mesh); border: 1px solid var(--card-border); backdrop-filter: var(--glass-blur); border-radius: 20px; color: var(--text-primary); }
.modal-header { border-bottom: 1px solid var(--card-border); }
.modal-footer { border-top: 1px solid var(--card-border); }
.btn-close { filter: invert(var(--theme-invert, 0)); }
.ticket-qr-container { width: 150px; height: 150px; margin: 0 auto; background: white; padding: 8px; border-radius: 12px; box-shadow: var(--shadow-md); display: flex; justify-content: center; align-items: center; }
/* ============================================================
   FOOTER
   ============================================================ */
footer { background: rgba(10,6,24,.1); border-top: 1px solid var(--card-border); padding: 50px 0 30px; margin-top: 80px; }
.social-links { display: flex; gap: 15px; }
.social-icon { width: 40px; height: 40px; border-radius: 50%; background: var(--card-bg); border: 1px solid var(--card-border); color: var(--text-secondary); display: flex; align-items: center; justify-content: center; transition: all var(--transition-fast); }
.social-icon:hover { background: var(--primary-color); color: #fff; transform: translateY(-2px); box-shadow: 0 4px 10px var(--primary-glow); }
/* ============================================================
   KEYFRAMES
   ============================================================ */
@keyframes spin { to { transform: rotate(360deg); } }
@keyframes pulse { 0%,100% { opacity: .6; transform: scale(.98); } 50% { opacity: 1; transform: scale(1.02); } }
@keyframes float-glow { 0% { transform: translate(0,0) scale(1); } 100% { transform: translate(20px,-20px) scale(1.1); } }
@keyframes float-animation { 0% { transform: translateY(0); } 50% { transform: translateY(-12px); } 100% { transform: translateY(0); } }
@keyframes blob-morph { 0% { border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%; } 100% { border-radius: 60% 40% 30% 70% / 50% 60% 40% 50%; } }
@keyframes typing-bounce { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-6px); } }
@keyframes toast-slide-in { to { transform: translateX(0); } }
</style>
</head>
<body>
<!-- Loading Overlay -->
<div id="loading-overlay">
    <div class="loader-logo">
        <div class="loader-spinner"></div>
        <div class="loader-prime-badge"><i class="fas fa-star-of-life fa-spin" style="font-size:.6rem"></i> PrimeAgent Ai</div>
        <h4 class="fw-bold text-gradient-primary mt-1 mb-0">Primefest AI Hub</h4>
        <p class="text-muted" style="font-size:.85rem;margin-top:6px">Initializing cognitive interface...</p>
    </div>
</div>
<!-- Toast Container -->
<div id="toast-container" class="toast-container"></div>
<!-- ===================== NAVBAR ===================== -->
<nav class="navbar navbar-expand-lg fixed-top">
    <div class="container">
        <a class="navbar-brand text-gradient-primary" href="#/home">
            <i class="fas fa-project-diagram"></i> EventAgent <span style="font-size:.7em;background:linear-gradient(135deg,var(--primary-color),var(--secondary-color));-webkit-background-clip:text;-webkit-text-fill-color:transparent;font-weight:800">PRIME</span>
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav ms-auto align-items-center">
                <li class="nav-item"><a class="nav-link" href="#/home">Home</a></li>
                <li class="nav-item"><a class="nav-link" href="#/events">Events</a></li>
                <li class="nav-item"><a class="nav-link" href="#/chatbot">AI Assistant</a></li>
                <li class="nav-item"><a class="nav-link" href="#/admin">Admin</a></li>
                <li class="nav-item"><a class="nav-link" href="#/about">About</a></li>
                <li class="nav-item"><a class="nav-link" href="#/contact">Contact</a></li>
                <li class="nav-item ms-lg-3">
                    <button class="theme-toggle-btn" id="theme-toggle" aria-label="Toggle Theme">
                        <i class="fas fa-moon"></i>
                    </button>
                </li>
            </ul>
        </div>
    </div>
</nav>
<!-- ===================== HOME PAGE ===================== -->
<section id="view-home" class="page-view">
    <div class="hero-section">
        <div class="hero-glow"></div>
        <div class="hero-glow-2"></div>
        <div class="container">
            <div class="row align-items-center">
                <div class="col-lg-6 mb-5 mb-lg-0">
                    <div class="badge bg-secondary mb-3 py-2 px-3 event-category-badge">Powered by Agentic AI</div>
                    <h1 class="hero-title">Experience Next-Gen <span class="text-gradient-primary">Inter-College Events</span></h1>
                    <p class="hero-subtitle">Discover Primefest technical workshops, design sprints, and business pitch competitions. Register in seconds or let our cognitive chatbot handle it all.</p>
                    <div class="d-flex gap-3">
                        <a href="#/events" class="btn btn-gradient">Browse Events</a>
                        <a href="#/chatbot" class="btn btn-glass">Consult Agent</a>
                    </div>
                </div>
                <div class="col-lg-6 hero-illustration">
                    <div class="hero-glass-blob">
                        <h3 class="fw-bold mb-2">Cognitive Assistant</h3>
                        <p class="text-muted px-4" style="font-size:.9rem">Instant answers about Primefest schedules, seat availability, fees, and registrations.</p>
                        <a href="#/chatbot" class="btn btn-gradient btn-sm mt-3 px-4">Start Chatting</a>
                    </div>
                    <div class="hero-agent-badge badge-1">
                        <i class="fas fa-ticket-alt text-gradient-primary"></i>
                        <div><h6 class="mb-0 fw-bold">Live Booking</h6><small class="text-muted">Dynamic seat count</small></div>
                    </div>
                    <div class="hero-agent-badge badge-2">
                        <i class="fas fa-shield-alt text-gradient-accent"></i>
                        <div><h6 class="mb-0 fw-bold">Verified QR</h6><small class="text-muted">Instant ticket PDF</small></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Features -->
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-lg-8">
                <h2 class="section-title">Why Register With Us?</h2>
                <p class="section-subtitle">Experience a modern SaaS workflow designed for convenience, security, and velocity.</p>
            </div>
        </div>
        <div class="row mt-4">
            <div class="col-md-4 mb-4">
                <div class="glass-card text-center p-4">
                    <div class="feature-icon mx-auto"><i class="fas fa-robot"></i></div>
                    <h4 class="fw-bold mb-3">AI Support Assistant</h4>
                    <p class="text-secondary" style="font-size:.9rem">Consult our AI chatbot anytime for event schedules, guidelines, pricing, and seat queries.</p>
                </div>
            </div>
            <div class="col-md-4 mb-4">
                <div class="glass-card text-center p-4">
                    <div class="feature-icon mx-auto"><i class="fas fa-qrcode"></i></div>
                    <h4 class="fw-bold mb-3">Instant QR Tickets</h4>
                    <p class="text-secondary" style="font-size:.9rem">Unique verification QR codes generated for your ticket immediately after sign-up.</p>
                </div>
            </div>
            <div class="col-md-4 mb-4">
                <div class="glass-card text-center p-4">
                    <div class="feature-icon mx-auto"><i class="fas fa-file-invoice-dollar"></i></div>
                    <h4 class="fw-bold mb-3">PDF Receipts</h4>
                    <p class="text-secondary" style="font-size:.9rem">Download official PDF invoice slips client-side — fast, lightweight, and offline-ready.</p>
                </div>
            </div>
        </div>
    </div>
    <!-- Upcoming Events -->
    <div class="container my-5 py-5">
        <div class="row justify-content-between align-items-center mb-4">
            <div class="col-md-8">
                <h2 class="section-title text-start mb-2">Featured Primefest Workshops</h2>
                <p class="text-muted">Secure your slots for our highly anticipated upcoming events.</p>
            </div>
            <div class="col-md-4 text-md-end">
                <a href="#/events" class="btn btn-glass">View All Events <i class="fas fa-arrow-right ms-1"></i></a>
            </div>
        </div>
        <div class="row" id="upcoming-events-list"></div>
    </div>
    <!-- Testimonials -->
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-lg-8">
                <h2 class="section-title">What Our Attendees Say</h2>
                <p class="section-subtitle">Feedback from students who attended previous Primefest editions.</p>
            </div>
        </div>
        <div class="row mt-4">
            <div class="col-md-6 mb-4">
                <div class="glass-card testimonial-card">
                    <div>
                        <div class="testimonial-rating"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></div>
                        <p class="text-secondary" style="font-style:italic">"The registration process was flawless! Generating a QR-coded ticket and downloading a PDF was simple and took under a minute. Outstanding UI/UX!"</p>
                    </div>
                    <div class="user-meta">
                        <div class="user-avatar-placeholder">DK</div>
                        <div><h6 class="mb-0 fw-bold">David Kova</h6><small class="text-muted">Staff Engineer, FinTech Corp</small></div>
                    </div>
                </div>
            </div>
            <div class="col-md-6 mb-4">
                <div class="glass-card testimonial-card">
                    <div>
                        <div class="testimonial-rating"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star-half-alt"></i></div>
                        <p class="text-secondary" style="font-style:italic">"I asked the AI Chatbot about timings and available seats for the Design sprint — it gave me precise answers instantly. Glassmorphic theme is stunning."</p>
                    </div>
                    <div class="user-meta">
                        <div class="user-avatar-placeholder">ML</div>
                        <div><h6 class="mb-0 fw-bold">Maya Lin</h6><small class="text-muted">UI/UX Researcher, Canvas Labs</small></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
<!-- ===================== EVENTS PAGE ===================== -->
<section id="view-events" class="page-view">
    <div class="container">
        <div class="row justify-content-center mb-5">
            <div class="col-lg-8 text-center">
                <h1 class="fw-bold mb-2">Explore Active Listings</h1>
                <p class="text-muted">Filter by category or search keywords to find the perfect event.</p>
            </div>
        </div>
        <div class="row justify-content-center search-filter-bar">
            <div class="col-lg-10">
                <div class="glass-panel p-4">
                    <div class="row align-items-center g-3">
                        <div class="col-md-4">
                            <div class="position-relative">
                                <input type="text" id="event-search-input" class="form-control rounded-pill ps-4 pe-5 py-2" placeholder="Search event, speaker..." onkeyup="searchEvents()">
                                <i class="fas fa-search position-absolute top-50 translate-middle-y end-0 me-3 text-muted"></i>
                            </div>
                        </div>
                        <div class="col-md-8">
                            <div class="d-flex flex-wrap gap-2 justify-content-md-end">
                                <button class="btn btn-gradient btn-sm filter-btn" data-filter="All" onclick="filterCategory('All')">All Categories</button>
                                <button class="btn btn-glass btn-sm filter-btn" data-filter="Tech" onclick="filterCategory('Tech')">Tech</button>
                                <button class="btn btn-glass btn-sm filter-btn" data-filter="Design" onclick="filterCategory('Design')">Design</button>
                                <button class="btn btn-glass btn-sm filter-btn" data-filter="Business" onclick="filterCategory('Business')">Business</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="row mt-4" id="events-grid"></div>
    </div>
</section>
<!-- ===================== EVENT DETAILS PAGE ===================== -->
<section id="view-details" class="page-view">
    <div class="container">
        <div class="mb-4">
            <a href="#/events" class="btn btn-glass btn-sm"><i class="fas fa-arrow-left me-2"></i>Back to Listings</a>
        </div>
        <div class="row">
            <div class="col-lg-8 mb-4">
                <div class="glass-panel details-header mb-4">
                    <span class="badge bg-secondary mb-3 py-2 px-3 event-category-badge" id="detail-category">Tech</span>
                    <h1 class="fw-bold mb-3" id="detail-title">Event Title</h1>
                    <p class="text-secondary mb-0" id="detail-desc">Loading details...</p>
                </div>
                <div class="glass-card mb-4">
                    <h4 class="fw-bold mb-3">Keynote Speaker</h4>
                    <div class="speaker-card">
                        <div class="user-avatar-placeholder" id="detail-speaker-avatar" style="width:60px;height:60px;font-size:1.5rem">SP</div>
                        <div>
                            <h5 class="fw-bold mb-1" id="detail-speaker-name">Speaker Name</h5>
                            <p class="text-muted mb-0" id="detail-speaker-title">Title</p>
                        </div>
                    </div>
                </div>
                <div class="glass-card">
                    <h4 class="fw-bold mb-4">Event Schedule</h4>
                    <div class="schedule-timeline" id="detail-schedule"></div>
                </div>
            </div>
            <div class="col-lg-4 mb-4">
                <div class="glass-card position-sticky" style="top:100px">
                    <h4 class="fw-bold mb-4">Reservation Info</h4>
                    <div class="row g-4 mb-4">
                        <div class="col-6 details-grid-item"><span class="details-grid-label">Date</span><span class="fw-bold" id="detail-date">-</span></div>
                        <div class="col-6 details-grid-item"><span class="details-grid-label">Time</span><span class="fw-bold" id="detail-time">-</span></div>
                        <div class="col-12 details-grid-item"><span class="details-grid-label">Venue</span><span class="fw-bold" id="detail-venue">-</span></div>
                        <div class="col-6 details-grid-item"><span class="details-grid-label">Capacity</span><span class="fw-bold" id="detail-seats">-</span></div>
                        <div class="col-6 details-grid-item"><span class="details-grid-label">Reg Fee</span><span class="fw-bold text-gradient-primary" id="detail-fee">-</span></div>
                    </div>
                    <button id="detail-register-btn" onclick="triggerRegisterCurrent()" class="btn btn-gradient w-100 py-3">Register for Event</button>
                </div>
            </div>
        </div>
    </div>
</section>
<!-- ===================== REGISTRATION PAGE ===================== -->
<section id="view-register" class="page-view">
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-lg-8 col-md-10">
                <div class="glass-card p-5">
                    <div class="text-center mb-5">
                        <div class="feature-icon mx-auto"><i class="fas fa-user-edit"></i></div>
                        <h1 class="fw-bold">Reserve Your Ticket</h1>
                        <p class="text-muted">Enter attendee information to reserve event credentials.</p>
                    </div>
                    <form id="registration-form" novalidate>
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <div class="form-floating">
                                    <input type="text" class="form-control" id="reg-name" placeholder="Full Name" required>
                                    <label for="reg-name">Full Name</label>
                                    <div class="invalid-feedback">Please enter your full name.</div>
                                </div>
                            </div>
                            <div class="col-md-6 mb-3">
                                <div class="form-floating">
                                    <input type="email" class="form-control" id="reg-email" placeholder="name@example.com" required>
                                    <label for="reg-email">Email Address</label>
                                    <div class="invalid-feedback">Please enter a valid email address.</div>
                                </div>
                            </div>
                            <div class="col-md-6 mb-3">
                                <div class="form-floating">
                                    <input type="tel" class="form-control" id="reg-phone" placeholder="Phone Number" required>
                                    <label for="reg-phone">Phone Number</label>
                                    <div class="invalid-feedback">Please enter a valid phone number.</div>
                                </div>
                            </div>
                            <div class="col-md-6 mb-3">
                                <div class="form-floating">
                                    <input type="text" class="form-control" id="reg-org" placeholder="College or Company" required>
                                    <label for="reg-org">College / Company Name</label>
                                    <div class="invalid-feedback">Please enter your college or company name.</div>
                                </div>
                            </div>
                            <div class="col-md-12 mb-3">
                                <label for="reg-event" class="form-label text-muted ms-2" style="font-size:.85rem">Select Event Listing</label>
                                <select class="form-select" id="reg-event" required>
                                    <option value="" disabled selected>Select an Event</option>
                                </select>
                                <div class="invalid-feedback">Please select an event to register.</div>
                            </div>
                            <div class="col-md-6 mb-3">
                                <label class="form-label text-muted ms-2" style="font-size:.85rem">Gender</label>
                                <div class="gender-radio-group">
                                    <div class="form-check"><input class="form-check-input" type="radio" name="gender" id="gender-male" value="Male"><label class="form-check-label" for="gender-male">Male</label></div>
                                    <div class="form-check"><input class="form-check-input" type="radio" name="gender" id="gender-female" value="Female"><label class="form-check-label" for="gender-female">Female</label></div>
                                    <div class="form-check"><input class="form-check-input" type="radio" name="gender" id="gender-other" value="Other"><label class="form-check-label" for="gender-other">Other</label></div>
                                </div>
                                <div class="invalid-feedback" id="gender-feedback" style="display:none;color:#dc3545;font-size:.8rem;margin-top:5px">Please select gender identity.</div>
                            </div>
                            <div class="col-md-6 mb-4 d-flex align-items-end">
                                <div class="form-floating w-100">
                                    <input type="text" class="form-control" id="reg-city" placeholder="City" required>
                                    <label for="reg-city">City</label>
                                    <div class="invalid-feedback">Please enter your city.</div>
                                </div>
                            </div>
                        </div>
                        <button type="submit" class="btn btn-gradient w-100 py-3 mt-2">Confirm Registration</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</section>
<!-- ===================== CHATBOT PAGE ===================== -->
<section id="view-chatbot" class="page-view">
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-lg-8">
                <div class="glass-panel chat-container">
                    <div class="chat-header">
                        <div class="chat-agent-avatar">
                            <i class="fas fa-robot"></i>
                            <div class="chat-agent-status"></div>
                        </div>
                        <div>
                            <h5 class="fw-bold mb-0">PrimeAgent AI</h5>
                            <small class="text-success">Active &amp; Consulting</small>
                        </div>
                    </div>
                    <div class="chat-body" id="chat-body"></div>
                    <div class="quick-reply-wrapper" id="chatbot-quick-replies"></div>
                    <div class="chat-footer">
                        <input type="text" class="chat-input" id="chat-input-text" placeholder="Ask about timings, venues, seat availability...">
                        <button class="chat-send-btn" id="chat-send-btn" aria-label="Send message"><i class="fas fa-paper-plane"></i></button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
<!-- ===================== ADMIN PAGE ===================== -->
<section id="view-admin" class="page-view">
    <div class="container" id="admin-content-area"></div>
</section>
<!-- ===================== ABOUT PAGE ===================== -->
<section id="view-about" class="page-view">
    <div class="container">
        <div class="row justify-content-center mb-5">
            <div class="col-lg-8 text-center">
                <h1 class="fw-bold mb-2">About The Project</h1>
                <p class="text-muted">Empowering event coordination with cognitive micro-agents.</p>
            </div>
        </div>
        <div class="row mt-4">
            <div class="col-md-6 mb-4">
                <div class="glass-card h-100 p-5">
                    <h3 class="fw-bold mb-3 text-gradient-primary">Project Description</h3>
                    <p class="text-secondary">EventAgent Prime is a highly visual, cognitive web application built to revolutionize catalog discovery and attendee coordination for inter-college events. It uses modern design paradigms like glassmorphism and gradient transitions to establish a state-of-the-art SaaS interface, with a built-in cognitive assistant that parses inquiries regarding Knowfest schedules, venues, and pricing instantly.</p>
                </div>
            </div>
            <div class="col-md-6 mb-4">
                <div class="glass-card h-100 p-5">
                    <h3 class="fw-bold mb-3 text-gradient-accent">Mission &amp; Vision</h3>
                    <p class="text-secondary">Our mission is to minimize friction between discovery and confirmation. Through automated receipt generation, unique validation QR codes, and cognitive chatbot interfaces, we envision an integrated platform where inter-college events can be managed with automated capacity calibrations and real-time seat tracking.</p>
                </div>
            </div>
        </div>
        <div class="row justify-content-center mt-5">
            <div class="col-md-8">
                <div class="glass-panel p-5 text-center">
                    <div class="user-avatar-placeholder mx-auto mb-4" style="width:80px;height:80px;font-size:2rem">AG</div>
                    <h3 class="fw-bold mb-1">Developer Profile</h3>
                    <p class="text-gradient-primary fw-bold mb-3">PrimeAgent Ai · Antigravity AI Platform</p>
                    <p class="text-secondary px-lg-5 mb-0">Crafted with high-fidelity frontend styles, responsive glass grids, standalone localStorage database engine, and production-ready Node.js REST API routes for deployment with MongoDB.</p>
                </div>
            </div>
        </div>
    </div>
</section>
<!-- ===================== CONTACT PAGE ===================== -->
<section id="view-contact" class="page-view">
    <div class="container">
        <div class="row justify-content-center mb-5">
            <div class="col-lg-8 text-center">
                <h1 class="fw-bold mb-2">Get in Touch</h1>
                <p class="text-muted">Have inquiries regarding event setups or corporate custom packages?</p>
            </div>
        </div>
        <div class="row">
            <div class="col-lg-5 mb-4">
                <div class="glass-card mb-4">
                    <h4 class="fw-bold mb-4">Contact Information</h4>
                    <div class="d-flex align-items-center gap-3 mb-3">
                        <div class="feature-icon mb-0" style="width:40px;height:40px;font-size:1rem"><i class="fas fa-envelope"></i></div>
                        <div><h6 class="mb-0 fw-bold">Email Us</h6><small class="text-secondary">srinathms360@gmail.com</small></div>
                    </div>
                    <div class="d-flex align-items-center gap-3 mb-3">
                        <div class="feature-icon mb-0" style="width:40px;height:40px;font-size:1rem"><i class="fas fa-phone-alt"></i></div>
                        <div><h6 class="mb-0 fw-bold">Call Support</h6><small class="text-secondary">+91 9443423728</small></div>
                    </div>
                    <div class="d-flex align-items-center gap-3">
                        <div class="feature-icon mb-0" style="width:40px;height:40px;font-size:1rem"><i class="fas fa-map-marker-alt"></i></div>
                        <div><h6 class="mb-0 fw-bold">Headquarters</h6><small class="text-secondary">Primefest Organizing Committee, Main Block</small></div>
                    </div>
                </div>
                <div class="glass-panel overflow-hidden" style="height:250px">
                    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3168.6392900750794!2d-122.0838511!3d37.4220011!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x808fba02425da8f9%3A0x2ca00e53ef302856!2sGoogleplex!5e0!3m2!1sen!2sus!4v1700000000000!5m2!1sen!2sus" width="100%" height="100%" style="border:0" allowfullscreen loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
                </div>
            </div>
            <div class="col-lg-7 mb-4">
                <div class="glass-card p-5 h-100">
                    <h4 class="fw-bold mb-4">Send a Message</h4>
                    <form id="contact-form">
                        <div class="form-floating mb-3">
                            <input type="text" class="form-control" id="contact-name" placeholder="Full Name" required>
                            <label for="contact-name">Full Name</label>
                        </div>
                        <div class="form-floating mb-3">
                            <input type="email" class="form-control" id="contact-email" placeholder="name@example.com" required>
                            <label for="contact-email">Email Address</label>
                        </div>
                        <div class="form-floating mb-4">
                            <textarea class="form-control" placeholder="Leave a message here" id="contact-message" style="height:150px" required></textarea>
                            <label for="contact-message">Your Message</label>
                        </div>
                        <button type="submit" class="btn btn-gradient w-100 py-3">Submit Inquiry</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</section>
<!-- ===================== FOOTER ===================== -->
<footer>
    <div class="container">
        <div class="row align-items-center">
            <div class="col-md-6 text-center text-md-start mb-3 mb-md-0">
                <h5 class="fw-bold mb-1 text-gradient-primary"><i class="fas fa-project-diagram"></i> EventAgent Prime</h5>
                <p class="text-muted mb-0" style="font-size:.85rem">&copy; 2026 Primefest AI Hub. All rights reserved.</p>
            </div>
            <div class="col-md-6 d-flex justify-content-center justify-content-md-end">
                <div class="social-links">
                    <a href="https://twitter.com" class="social-icon" target="_blank" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
                    <a href="https://www.linkedin.com/in/srinath-23ms/" class="social-icon" target="_blank" aria-label="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
                    <a href="https://github.com/srinathms23" class="social-icon" target="_blank" aria-label="GitHub"><i class="fab fa-github"></i></a>
                    <a href="https://www.instagram.com/green_cupid_23/" class="social-icon" target="_blank" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
                </div>
            </div>
        </div>
    </div>
</footer>
<!-- ===================== TICKET MODAL ===================== -->
<div class="modal fade" id="ticketModal" tabindex="-1" aria-labelledby="ticketModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title fw-bold text-gradient-primary" id="ticketModalLabel"><i class="fas fa-ticket-alt me-2"></i>Registration Success!</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body text-center p-4">
                <h4 class="fw-bold mb-1 text-gradient-accent">Your E-Ticket</h4>
                <p class="text-muted" id="ticket-id" style="font-size:.85rem">ID: -</p>
                <div class="ticket-qr-container my-4" id="ticket-qr"></div>
                <div class="glass-panel p-3 text-start mb-3">
                    <div class="mb-2"><span class="text-muted" style="font-size:.7rem;text-transform:uppercase">ATTENDEE</span><br><strong id="ticket-user-name">-</strong> (<span id="ticket-user-email">-</span>)</div>
                    <div class="mb-2"><span class="text-muted" style="font-size:.7rem;text-transform:uppercase">EVENT</span><br><strong id="ticket-event-title">-</strong></div>
                    <div class="row">
                        <div class="col-6"><span class="text-muted" style="font-size:.7rem;text-transform:uppercase">DATE</span><br><strong id="ticket-event-date">-</strong></div>
                        <div class="col-6"><span class="text-muted" style="font-size:.7rem;text-transform:uppercase">VENUE</span><br><strong id="ticket-event-venue">-</strong></div>
                    </div>
                </div>
                <p class="text-muted mb-0" style="font-size:.8rem">Show this QR code at the entrance gate for verification.</p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-glass" data-bs-dismiss="modal">Close</button>
                <button type="button" onclick="downloadTicketPDF()" class="btn btn-gradient"><i class="fas fa-file-pdf me-2"></i>Download Receipt</button>
            </div>
        </div>
    </div>
</div>
<!-- ===================== ADMIN EVENT FORM MODAL ===================== -->
<div class="modal fade" id="eventFormModal" tabindex="-1" aria-labelledby="eventModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title fw-bold" id="eventModalLabel">Add New Event</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body p-4">
                <form id="event-form">
                    <div class="row">
                        <div class="col-md-6 mb-3"><label for="evt-title" class="form-label text-muted" style="font-size:.85rem">Event Title</label><input type="text" class="form-control" id="evt-title" required></div>
                        <div class="col-md-6 mb-3"><label for="evt-category" class="form-label text-muted" style="font-size:.85rem">Category</label><select class="form-select" id="evt-category" required style="height:38px;padding:6px 12px"><option value="Tech">Tech</option><option value="Design">Design</option><option value="Business">Business</option></select></div>
                        <div class="col-md-6 mb-3"><label for="evt-date" class="form-label text-muted" style="font-size:.85rem">Date</label><input type="date" class="form-control" id="evt-date" required></div>
                        <div class="col-md-6 mb-3"><label for="evt-time" class="form-label text-muted" style="font-size:.85rem">Time (e.g. 10:00 AM - 05:00 PM)</label><input type="text" class="form-control" id="evt-time" required></div>
                        <div class="col-md-12 mb-3"><label for="evt-venue" class="form-label text-muted" style="font-size:.85rem">Venue</label><input type="text" class="form-control" id="evt-venue" required></div>
                        <div class="col-md-6 mb-3"><label for="evt-fee" class="form-label text-muted" style="font-size:.85rem">Registration Fee (₹)</label><input type="number" class="form-control" id="evt-fee" min="0" required></div>
                        <div class="col-md-6 mb-3"><label for="evt-seats" class="form-label text-muted" style="font-size:.85rem">Total Seats Capacity</label><input type="number" class="form-control" id="evt-seats" min="1" required></div>
                        <div class="col-md-6 mb-3"><label for="evt-speaker" class="form-label text-muted" style="font-size:.85rem">Speaker Name</label><input type="text" class="form-control" id="evt-speaker" required></div>
                        <div class="col-md-6 mb-3"><label for="evt-speaker-title" class="form-label text-muted" style="font-size:.85rem">Speaker Title / Affiliation</label><input type="text" class="form-control" id="evt-speaker-title"></div>
                        <div class="col-md-12 mb-3"><label for="evt-image" class="form-label text-muted" style="font-size:.85rem">Cover Image URL (Optional)</label><input type="url" class="form-control" id="evt-image" placeholder="https://images.unsplash.com/..."></div>
                        <div class="col-md-12 mb-3"><label for="evt-desc" class="form-label text-muted" style="font-size:.85rem">Complete Description</label><textarea class="form-control" id="evt-desc" style="height:120px" required></textarea></div>
                    </div>
                    <div class="d-flex justify-content-end gap-2 mt-3">
                        <button type="button" class="btn btn-glass btn-sm" data-bs-dismiss="modal">Cancel</button>
                        <button type="submit" class="btn btn-gradient btn-sm px-4">Save Listing</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</div>
<!-- CDN Scripts -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script>
/* ============================================================
   API SERVICE (api.js inlined)
   ============================================================ */
const API_URL = 'http://localhost:5000/api';
class ApiService {
    constructor() { this.useMock = true; this.serverChecked = false; }
    async init() {
        if (this.serverChecked) return;
        try {
            const res = await fetch(`${API_URL}/health`, { method: 'GET' }).catch(() => null);
            if (res && res.ok) {
                const data = await res.json();
                if (data.status === 'ok') { this.useMock = false; }
            }
        } catch (err) { /* offline */ } finally {
            this.serverChecked = true;
            if (this.useMock) this.initMockDb();
        }
    }
    initMockDb() {
        const existing = localStorage.getItem('events');
        if (existing && existing.includes('Global AI Summit')) {
            localStorage.removeItem('events'); localStorage.removeItem('registrations');
            localStorage.removeItem('users'); localStorage.removeItem('feedback');
        }
        if (!localStorage.getItem('events')) {
            localStorage.setItem('events', JSON.stringify([
                {
                    _id: 'mock-event-1',
                    title: "Inter-College PPT Presentation Showdown (Knowfest '26)",
                    description: "The flagship PowerPoint Presentation competition of Knowfest '26. Showcase your research papers, innovative prototypes, or conceptual systems in front of senior judges. Topics include Generative AI, Cyber Security, Quantum Computing, IoT, and Web3.",
                    date: '2026-08-15', time: '10:00 AM - 01:00 PM',
                    venue: 'Seminar Hall 1, Main Block', category: 'Tech', fee: '150',
                    seatsTotal: 60, seatsAvailable: 45,
                    speaker: 'Dr. R. K. Prasad', speakerTitle: 'Dean of Research & Innovation, Knowfest Committee',
                    image: 'https://images.unsplash.com/photo-1475721027785-f74eccf877e2?auto=format&fit=crop&q=80&w=800',
                    schedule: [
                        { time: '10:00 AM', activity: 'Introduction & Paper Screening' },
                        { time: '10:30 AM', activity: 'PPT Presentations (Batch A - AI & Cyber)' },
                        { time: '11:45 AM', activity: 'PPT Presentations (Batch B - Quantum & IoT)' },
                        { time: '12:45 PM', activity: 'Q&A & Winner Announcements' }
                    ]
                },
                {
                    _id: 'mock-event-2',
                    title: 'Hands-on Android App Development Workshop',
                    description: 'A comprehensive, hands-on workshop focused on building Android applications from scratch using Kotlin, XML layouts, and modern architecture. Learn how to interface with databases and build beautiful interfaces.',
                    date: '2026-09-02', time: '09:30 AM - 04:30 PM',
                    venue: 'E-Learning Lab, Computer Science Block', category: 'Tech', fee: '300',
                    seatsTotal: 80, seatsAvailable: 8,
                    speaker: 'Er. Amit Sharma', speakerTitle: 'Senior Android Architect, TechLabs India',
                    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&q=80&w=800',
                    schedule: [
                        { time: '09:30 AM', activity: 'Android Architecture & Setup' },
                        { time: '11:00 AM', activity: 'Kotlin Syntax for App Dev' },
                        { time: '01:00 PM', activity: 'Hands-on project building' },
                        { time: '03:30 PM', activity: 'Deploying APKs and Debugging' }
                    ]
                },
                {
                    _id: 'mock-event-3',
                    title: "UI/UX Design Masterclass (Knowfest '26)",
                    description: 'Discover visual layout patterns, color theory, glassmorphism, responsive web grids, and dynamic animations. A fast-paced sprint to take your design skills to developer-ready levels in Figma.',
                    date: '2026-09-03', time: '02:00 PM - 05:30 PM',
                    venue: 'Design Studio, Level 2, Arts Block', category: 'Design', fee: '200',
                    seatsTotal: 50, seatsAvailable: 15,
                    speaker: 'Ms. Priya Sen', speakerTitle: 'Lead Designer, Pixel Studio',
                    image: 'https://images.unsplash.com/photo-1586717791821-3f44a563fa4c?auto=format&fit=crop&q=80&w=800',
                    schedule: [
                        { time: '02:00 PM', activity: 'Visual Tokens and Psychology' },
                        { time: '03:15 PM', activity: 'Figma Sandbox Practical Sprint' },
                        { time: '04:45 PM', activity: 'Critiques and UI Walkthroughs' }
                    ]
                },
                {
                    _id: 'mock-event-4',
                    title: 'National Startup Pitch Challenge (PitchFest)',
                    description: 'A platform to pitch your innovative business models to angel investors, venture funds, and incubation leads. Ideal for aspiring entrepreneurs, designers, and developer teams. Free entry for inter-college teams.',
                    date: '2026-09-20', time: '10:00 AM - 03:00 PM',
                    venue: 'Conference Auditorium, MBA Block', category: 'Business', fee: '0',
                    seatsTotal: 150, seatsAvailable: 110,
                    speaker: 'Mr. Rohan Mehta', speakerTitle: 'Co-Founder, VentureHub India',
                    image: 'https://images.unsplash.com/photo-1475721027785-f74eccf877e2?auto=format&fit=crop&q=80&w=800',
                    schedule: [
                        { time: '10:00 AM', activity: 'Introductory Panels' },
                        { time: '10:30 AM', activity: 'Startup Pitches Cohort A' },
                        { time: '01:00 PM', activity: 'Startup Pitches Cohort B' },
                        { time: '02:30 PM', activity: 'Feedback, Incubation Grants & Winners' }
                    ]
                }
            ]));
        }
        if (!localStorage.getItem('users')) {
            localStorage.setItem('users', JSON.stringify([
                { _id: 'mock-user-1', name: 'Rohan Sharma', email: 'rohan@example.com', phone: '9876543210', company: 'IIT Madras', gender: 'Male', city: 'Chennai' },
                { _id: 'mock-user-2', name: 'Neha Gupta', email: 'neha@example.com', phone: '9123456789', company: 'BITS Pilani', gender: 'Female', city: 'Hyderabad' }
            ]));
        }
        if (!localStorage.getItem('registrations')) {
            localStorage.setItem('registrations', JSON.stringify([
                { _id: 'mock-reg-1', userId: 'mock-user-1', userName: 'Rohan Sharma', userEmail: 'rohan@example.com', eventId: 'mock-event-1', eventTitle: "Inter-College PPT Presentation Showdown (Knowfest '26)", regDate: '2026-07-01', status: 'Registered' },
                { _id: 'mock-reg-2', userId: 'mock-user-2', userName: 'Neha Gupta', userEmail: 'neha@example.com', eventId: 'mock-event-2', eventTitle: 'Hands-on Android App Development Workshop', regDate: '2026-07-02', status: 'Registered' }
            ]));
        }
        if (!localStorage.getItem('feedback')) {
            localStorage.setItem('feedback', JSON.stringify([
                { _id: 'mock-feed-1', name: 'Aravind Swamy', email: 'aravind@example.com', message: 'I registered for the PPT showdown. Are there guidelines for presentation lengths?', rating: 5, date: '2026-07-02' },
                { _id: 'mock-feed-2', name: 'Deepika Sen', email: 'deepika@example.com', message: 'Excellent UI. I love the glass theme!', rating: 4, date: '2026-07-03' }
            ]));
        }
    }
    getMockData(key) { return JSON.parse(localStorage.getItem(key)) || []; }
    setMockData(key, data) { localStorage.setItem(key, JSON.stringify(data)); }
    async getEvents() { await this.init(); if (this.useMock) return this.getMockData('events'); return (await fetch(`${API_URL}/events`)).json(); }
    async getEvent(id) { await this.init(); if (this.useMock) return this.getMockData('events').find(e => e._id === id); return (await fetch(`${API_URL}/events/${id}`)).json(); }
    async createEvent(eventData) {
        await this.init();
        if (this.useMock) {
            const events = this.getMockData('events');
            const newEvent = { _id: 'mock-event-' + Date.now(), ...eventData, seatsAvailable: parseInt(eventData.seatsTotal), seatsTotal: parseInt(eventData.seatsTotal), schedule: eventData.schedule || [{ time: '09:00 AM', activity: 'Event Commences' }, { time: '12:00 PM', activity: 'Networking session' }, { time: '04:00 PM', activity: 'Closing remarks' }] };
            events.push(newEvent); this.setMockData('events', events); return newEvent;
        }
        return (await fetch(`${API_URL}/events`, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(eventData) })).json();
    }
    async updateEvent(id, eventData) {
        await this.init();
        if (this.useMock) {
            const events = this.getMockData('events'); const idx = events.findIndex(e => e._id === id);
            if (idx !== -1) { events[idx] = { ...events[idx], ...eventData }; this.setMockData('events', events); return events[idx]; }
            throw new Error('Event not found');
        }
        return (await fetch(`${API_URL}/events/${id}`, { method: 'PUT', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(eventData) })).json();
    }
    async deleteEvent(id) {
        await this.init();
        if (this.useMock) {
            this.setMockData('events', this.getMockData('events').filter(e => e._id !== id));
            this.setMockData('registrations', this.getMockData('registrations').filter(r => r.eventId !== id));
            return { success: true };
        }
        return (await fetch(`${API_URL}/events/${id}`, { method: 'DELETE' })).json();
    }
    async registerUser(regForm) {
        await this.init();
        if (this.useMock) {
            const users = this.getMockData('users'), regs = this.getMockData('registrations'), events = this.getMockData('events');
            const event = events.find(e => e._id === regForm.eventId);
            if (!event) throw new Error('Event not found');
            if (event.seatsAvailable <= 0) throw new Error('No seats available for this event.');
            event.seatsAvailable -= 1; this.setMockData('events', events);
            let user = users.find(u => u.email.toLowerCase() === regForm.email.toLowerCase());
            if (!user) { user = { _id: 'mock-user-' + Date.now(), name: regForm.name, email: regForm.email, phone: regForm.phone, company: regForm.company, gender: regForm.gender, city: regForm.city }; users.push(user); this.setMockData('users', users); }
            const newReg = { _id: 'mock-reg-' + Date.now(), userId: user._id, userName: user.name, userEmail: user.email, eventId: event._id, eventTitle: event.title, regDate: new Date().toISOString().split('T')[0], status: 'Registered' };
            regs.push(newReg); this.setMockData('registrations', regs);
            return { success: true, user, registration: newReg, event };
        }
        return (await fetch(`${API_URL}/register`, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(regForm) })).json();
    }
    async getRegistrations() { await this.init(); if (this.useMock) return this.getMockData('registrations'); return (await fetch(`${API_URL}/registrations`)).json(); }
    async deleteRegistration(id) {
        await this.init();
        if (this.useMock) {
            let regs = this.getMockData('registrations'); const reg = regs.find(r => r._id === id);
            if (reg) {
                const events = this.getMockData('events'); const event = events.find(e => e._id === reg.eventId);
                if (event) { event.seatsAvailable = Math.min(event.seatsTotal, event.seatsAvailable + 1); this.setMockData('events', events); }
                regs = regs.filter(r => r._id !== id); this.setMockData('registrations', regs);
                return { success: true };
            }
            throw new Error('Registration not found');
        }
        return (await fetch(`${API_URL}/registrations/${id}`, { method: 'DELETE' })).json();
    }
    async getUsers() { await this.init(); if (this.useMock) return this.getMockData('users'); return (await fetch(`${API_URL}/users`)).json(); }
    async submitFeedback(feedData) {
        await this.init();
        if (this.useMock) {
            const feedbackList = this.getMockData('feedback');
            const newFeedback = { _id: 'mock-feed-' + Date.now(), ...feedData, date: new Date().toISOString().split('T')[0] };
            feedbackList.push(newFeedback); this.setMockData('feedback', feedbackList); return newFeedback;
        }
        return (await fetch(`${API_URL}/feedback`, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(feedData) })).json();
    }
    async getFeedback() { await this.init(); if (this.useMock) return this.getMockData('feedback'); return (await fetch(`${API_URL}/feedback`)).json(); }
}
const api = new ApiService();
window.api = api;
/* ============================================================
   APP LOGIC (app.js inlined)
   ============================================================ */
const state = {
    events: [], registrations: [], users: [], feedback: [],
    currentEventId: null, isAdminLoggedIn: false,
    theme: localStorage.getItem('theme') || 'light'
};
document.addEventListener('DOMContentLoaded', async () => {
    initTheme(); setupRouting(); setupEventListeners();
    await loadInitialData(); hideLoader();
});
function initTheme() {
    document.documentElement.setAttribute('data-theme', state.theme);
    const themeBtn = document.getElementById('theme-toggle');
    if (themeBtn) themeBtn.innerHTML = state.theme === 'dark' ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
}
function toggleTheme() {
    state.theme = state.theme === 'light' ? 'dark' : 'light';
    localStorage.setItem('theme', state.theme);
    document.documentElement.setAttribute('data-theme', state.theme);
    const themeBtn = document.getElementById('theme-toggle');
    if (themeBtn) themeBtn.innerHTML = state.theme === 'dark' ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
    showToast('Theme updated to ' + state.theme + ' mode!', 'info');
}
function hideLoader() {
    const loader = document.getElementById('loading-overlay');
    if (loader) { loader.style.opacity = '0'; setTimeout(() => loader.style.display = 'none', 500); }
}
function setupRouting() {
    const views = document.querySelectorAll('.page-view');
    const navLinks = document.querySelectorAll('.navbar-nav .nav-link');
    function route() {
        const hash = window.location.hash || '#/home';
        views.forEach(v => v.classList.remove('active'));
        navLinks.forEach(l => l.classList.remove('active'));
        if (hash === '#/home') { document.getElementById('view-home').classList.add('active'); highlightNavLink('#/home'); renderHomeEvents(); }
        else if (hash === '#/events') { document.getElementById('view-events').classList.add('active'); highlightNavLink('#/events'); renderEventsGrid(); }
        else if (hash.startsWith('#/event/')) { showEventDetails(hash.split('/').pop()); }
        else if (hash === '#/register') { document.getElementById('view-register').classList.add('active'); highlightNavLink('#/register'); populateEventSelection(); }
        else if (hash === '#/chatbot') { document.getElementById('view-chatbot').classList.add('active'); highlightNavLink('#/chatbot'); initChatbot(); }
        else if (hash === '#/admin') { document.getElementById('view-admin').classList.add('active'); highlightNavLink('#/admin'); renderAdminDashboard(); }
        else if (hash === '#/contact') { document.getElementById('view-contact').classList.add('active'); highlightNavLink('#/contact'); }
        else if (hash === '#/about') { document.getElementById('view-about').classList.add('active'); highlightNavLink('#/about'); }
        else { window.location.hash = '#/home'; }
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }
    function highlightNavLink(hash) { navLinks.forEach(l => { if (l.getAttribute('href') === hash) l.classList.add('active'); }); }
    window.addEventListener('hashchange', route);
    route();
}
async function loadInitialData() {
    try {
        state.events = await window.api.getEvents();
        state.registrations = await window.api.getRegistrations();
        state.users = await window.api.getUsers();
        state.feedback = await window.api.getFeedback();
    } catch (err) { showToast('Error loading application data.', 'error'); }
}
function renderHomeEvents() {
    const container = document.getElementById('upcoming-events-list');
    if (!container) return;
    container.innerHTML = '';
    const sorted = [...state.events].sort((a, b) => new Date(a.date) - new Date(b.date)).slice(0, 3);
    if (sorted.length === 0) { container.innerHTML = '<div class="col-12 text-center text-muted">No upcoming events scheduled.</div>'; return; }
    sorted.forEach(evt => { container.innerHTML += buildEventCard(evt); });
}
let activeCategoryFilter = 'All';
function filterCategory(cat) {
    activeCategoryFilter = cat;
    document.querySelectorAll('.filter-btn').forEach(btn => {
        if (btn.getAttribute('data-filter') === cat) { btn.classList.add('btn-gradient'); btn.classList.remove('btn-glass'); }
        else { btn.classList.remove('btn-gradient'); btn.classList.add('btn-glass'); }
    });
    renderEventsGrid();
}
function searchEvents() { renderEventsGrid(); }
function renderEventsGrid() {
    const container = document.getElementById('events-grid');
    const searchVal = (document.getElementById('event-search-input').value || '').toLowerCase();
    if (!container) return;
    container.innerHTML = '';
    const filtered = state.events.filter(evt => {
        const matchesCat = activeCategoryFilter === 'All' || evt.category.toLowerCase() === activeCategoryFilter.toLowerCase();
        const matchesSearch = evt.title.toLowerCase().includes(searchVal) || evt.description.toLowerCase().includes(searchVal) || evt.venue.toLowerCase().includes(searchVal) || evt.speaker.toLowerCase().includes(searchVal);
        return matchesCat && matchesSearch;
    });
    if (filtered.length === 0) { container.innerHTML = '<div class="col-12 text-center text-muted my-5">No events match your search or filter.</div>'; return; }
    filtered.forEach(evt => { container.innerHTML += buildEventCard(evt); });
}
function buildEventCard(evt) {
    const seatsClass = getSeatsClass(evt.seatsAvailable);
    const feeText = parseFloat(evt.fee) === 0 ? 'Free' : `₹${evt.fee}`;
    return `
    <div class="col-lg-4 col-md-6 mb-4">
        <div class="glass-card event-card">
            <div class="event-card-img-wrapper">
                <div class="event-card-img-overlay"><span class="event-category-badge">${evt.category}</span></div>
                <img src="${evt.image || 'https://images.unsplash.com/photo-1501281668745-f7f57925c3b4?auto=format&fit=crop&q=80&w=800'}" class="event-card-img" alt="${evt.title}">
            </div>
            <div class="event-card-body d-flex flex-column justify-content-between p-4 flex-grow-1">
                <div>
                    <h4 class="mb-3">${evt.title}</h4>
                    <div class="event-meta-item"><i class="far fa-calendar-alt"></i> ${formatDate(evt.date)}</div>
                    <div class="event-meta-item"><i class="far fa-clock"></i> ${evt.time}</div>
                    <div class="event-meta-item"><i class="fas fa-map-marker-alt"></i> ${evt.venue}</div>
                </div>
                <div class="mt-4">
                    <div class="d-flex justify-content-between align-items-center mb-3">
                        <span class="seats-indicator">Seats: <span class="seats-badge ${seatsClass}">${evt.seatsAvailable}/${evt.seatsTotal}</span></span>
                        <span class="fw-bold text-gradient-primary">${feeText}</span>
                    </div>
                    <div class="d-flex gap-2">
                        <a href="#/event/${evt._id}" class="btn btn-glass flex-fill text-center btn-sm py-2">Details</a>
                        <button onclick="triggerRegisterForEvent('${evt._id}')" class="btn btn-gradient flex-fill btn-sm py-2" ${evt.seatsAvailable === 0 ? 'disabled' : ''}>${evt.seatsAvailable === 0 ? 'Sold Out' : 'Register'}</button>
                    </div>
                </div>
            </div>
        </div>
    </div>`;
}
function showEventDetails(id) {
    const event = state.events.find(e => e._id === id);
    if (!event) { window.location.hash = '#/events'; return; }
    state.currentEventId = id;
    document.getElementById('view-details').classList.add('active');
    document.getElementById('detail-title').innerText = event.title;
    document.getElementById('detail-category').innerText = event.category;
    document.getElementById('detail-desc').innerText = event.description;
    document.getElementById('detail-date').innerText = formatDate(event.date);
    document.getElementById('detail-time').innerText = event.time;
    document.getElementById('detail-venue').innerText = event.venue;
    document.getElementById('detail-fee').innerText = parseFloat(event.fee) === 0 ? 'Free' : `₹${event.fee}`;
    const seatsClass = getSeatsClass(event.seatsAvailable);
    document.getElementById('detail-seats').innerHTML = `<span class="seats-badge ${seatsClass}">${event.seatsAvailable} of ${event.seatsTotal} remaining</span>`;
    document.getElementById('detail-speaker-name').innerText = event.speaker;
    document.getElementById('detail-speaker-title').innerText = event.speakerTitle || 'Keynote Speaker';
    document.getElementById('detail-speaker-avatar').innerText = event.speaker.split(' ').map(n => n[0]).join('');
    const timeline = document.getElementById('detail-schedule');
    timeline.innerHTML = '';
    if (event.schedule && event.schedule.length > 0) {
        event.schedule.forEach(s => { timeline.innerHTML += `<div class="timeline-item"><h5 class="mb-1">${s.time}</h5><p class="text-secondary mb-0">${s.activity}</p></div>`; });
    } else {
        timeline.innerHTML = `<div class="timeline-item"><h5 class="mb-1">${event.time.split(' - ')[0]}</h5><p class="text-secondary mb-0">Event Commences</p></div><div class="timeline-item"><h5 class="mb-1">${event.time.split(' - ')[1] || 'End'}</h5><p class="text-secondary mb-0">Event Concludes</p></div>`;
    }
    const regBtn = document.getElementById('detail-register-btn');
    if (event.seatsAvailable <= 0) { regBtn.innerText = 'Sold Out'; regBtn.disabled = true; }
    else { regBtn.innerText = 'Register for Event'; regBtn.disabled = false; }
}
function triggerRegisterForEvent(eventId) { state.currentEventId = eventId; window.location.hash = '#/register'; }
function triggerRegisterCurrent() { if (state.currentEventId) window.location.hash = '#/register'; }
function populateEventSelection() {
    const select = document.getElementById('reg-event');
    if (!select) return;
    select.innerHTML = '<option value="" disabled selected>Select an Event</option>';
    state.events.forEach(e => {
        const disabled = e.seatsAvailable <= 0 ? 'disabled' : '';
        const selected = e._id === state.currentEventId ? 'selected' : '';
        select.innerHTML += `<option value="${e._id}" ${selected} ${disabled}>${e.title} (${e.seatsAvailable} seats left) - ${parseFloat(e.fee) === 0 ? 'Free' : `₹${e.fee}`}</option>`;
    });
}
function validateRegistrationForm() {
    const name = document.getElementById('reg-name'), email = document.getElementById('reg-email'),
          phone = document.getElementById('reg-phone'), org = document.getElementById('reg-org'),
          event = document.getElementById('reg-event'), city = document.getElementById('reg-city');
    let isValid = true;
    if (!name.value.trim()) { showFieldError(name, 'Full name is required.'); isValid = false; } else clearFieldError(name);
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!email.value.trim()) { showFieldError(email, 'Email address is required.'); isValid = false; }
    else if (!emailRegex.test(email.value.trim())) { showFieldError(email, 'Please enter a valid email address.'); isValid = false; }
    else clearFieldError(email);
    const phoneRegex = /^\+?[0-9\s-]{10,14}$/;
    if (!phone.value.trim()) { showFieldError(phone, 'Phone number is required.'); isValid = false; }
    else if (!phoneRegex.test(phone.value.trim())) { showFieldError(phone, 'Please enter a valid phone number (10-14 digits).'); isValid = false; }
    else clearFieldError(phone);
    if (!org.value.trim()) { showFieldError(org, 'College or Company name is required.'); isValid = false; } else clearFieldError(org);
    if (!event.value) { showFieldError(event, 'Please select an event to attend.'); isValid = false; } else clearFieldError(event);
    const genderFeedback = document.getElementById('gender-feedback');
    if (!document.getElementById('gender-male').checked && !document.getElementById('gender-female').checked && !document.getElementById('gender-other').checked) { genderFeedback.style.display = 'block'; isValid = false; } else genderFeedback.style.display = 'none';
    if (!city.value.trim()) { showFieldError(city, 'City is required.'); isValid = false; } else clearFieldError(city);
    return isValid;
}
function showFieldError(inputEl, msg) {
    inputEl.classList.add('is-invalid');
    const feedback = inputEl.parentElement.querySelector('.invalid-feedback') || inputEl.parentElement.parentElement.querySelector('.invalid-feedback');
    if (feedback) feedback.innerText = msg;
}
function clearFieldError(inputEl) { inputEl.classList.remove('is-invalid'); }
async function submitContactForm(e) {
    e.preventDefault();
    const name = document.getElementById('contact-name').value, email = document.getElementById('contact-email').value, msg = document.getElementById('contact-message').value;
    if (!name || !email || !msg) { showToast('Please fill in all details.', 'error'); return; }
    try { await window.api.submitFeedback({ name, email, message: msg, rating: 5 }); showToast('Message submitted successfully! Thank you.', 'success'); document.getElementById('contact-form').reset(); await loadInitialData(); } catch (err) { showToast('Failed to submit message.', 'error'); }
}
// Chatbot
const chatPresets = {
    timings: "Our main event is the \"Inter-College PPT Presentation Showdown (Knowfest '26)\" which runs from 10:00 AM to 01:00 PM on August 15, 2026. The Hands-on Android App Development Workshop runs from 09:30 AM to 04:30 PM on September 2, 2026. Review our Events page for full timelines!",
    venue: "All Knowfest '26 events are hosted on campus:\n- PPT Showdown: Seminar Hall 1, Main Block.\n- Android Workshop: E-Learning Lab, CS Block.\n- UI/UX Masterclass: Design Studio, Level 2, Arts Block.\n- Startup PitchFest: Conference Auditorium, MBA Block.",
    seats: 'Seat status (real-time):\n- PPT Showdown: 45 seats left.\n- Android Workshop: ONLY 8 seats remaining! (Book soon)\n- UI/UX Design: 15 seats left.\n- Startup Pitch: 110 seats left.',
    process: 'To register:\n1. Go to the "Events" page.\n2. Pick your event and click "Register".\n3. Input your details (Name, College, Email, Phone).\n4. Submit to generate your QR ticket and PDF receipt!',
    contact: 'Get in touch with the Knowfest organizing committee at support@eventagent.ai or call at +91 98765 43210.',
    fees: 'Registration fees (INR):\n- PPT Presentation Showdown: ₹150\n- Android Development Workshop: ₹300\n- UI/UX Design Masterclass: ₹200\n- Startup Pitch Challenge: FREE (₹0)!',
    cancellation: 'Refunds for ticket cancellations are allowed up to 48 hours prior to the event. Cancellations restore seats to the pool and refunds are processed within 5 working days.'
};
function initChatbot() {
    const chatBody = document.getElementById('chat-body');
    if (chatBody.children.length === 0) { addBotMessage("Hello! I am EventAgent Prime AI. How can I help you today? Ask about Knowfest event timings, pricing, venues, or seat availability!"); renderChatbotQuickReplies(); }
}
function addBotMessage(text) { const chatBody = document.getElementById('chat-body'); const bubble = document.createElement('div'); bubble.className = 'chat-bubble bot'; bubble.innerText = text; chatBody.appendChild(bubble); chatBody.scrollTop = chatBody.scrollHeight; }
function addUserMessage(text) { const chatBody = document.getElementById('chat-body'); const bubble = document.createElement('div'); bubble.className = 'chat-bubble user'; bubble.innerText = text; chatBody.appendChild(bubble); chatBody.scrollTop = chatBody.scrollHeight; }
function showTypingIndicator() {
    const chatBody = document.getElementById('chat-body');
    const indicator = document.createElement('div'); indicator.className = 'chat-bubble bot'; indicator.id = 'chat-typing-indicator';
    indicator.innerHTML = '<div class="typing-indicator"><div class="typing-dot"></div><div class="typing-dot"></div><div class="typing-dot"></div></div>';
    chatBody.appendChild(indicator); chatBody.scrollTop = chatBody.scrollHeight;
}
function removeTypingIndicator() { const el = document.getElementById('chat-typing-indicator'); if (el) el.remove(); }
function handleChatSend() {
    const input = document.getElementById('chat-input-text'); const query = input.value.trim(); if (!query) return;
    addUserMessage(query); input.value = ''; showTypingIndicator();
    setTimeout(() => { removeTypingIndicator(); addBotMessage(matchChatQuery(query)); }, 1000);
}
function selectQuickReply(key, label) {
    addUserMessage(label); showTypingIndicator();
    setTimeout(() => { removeTypingIndicator(); addBotMessage(chatPresets[key] || "I'm sorry, I don't have information on that topic right now."); }, 800);
}
function matchChatQuery(query) {
    const t = query.toLowerCase();
    if (t.includes('time') || t.includes('schedule') || t.includes('when') || t.includes('date')) return chatPresets.timings;
    if (t.includes('venue') || t.includes('location') || t.includes('where')) return chatPresets.venue;
    if (t.includes('seat') || t.includes('availability') || t.includes('left') || t.includes('slot')) return chatPresets.seats;
    if (t.includes('register') || t.includes('booking') || t.includes('sign up') || t.includes('how to')) return chatPresets.process;
    if (t.includes('contact') || t.includes('phone') || t.includes('email') || t.includes('support')) return chatPresets.contact;
    if (t.includes('fee') || t.includes('price') || t.includes('cost') || t.includes('pay') || t.includes('free')) return chatPresets.fees;
    if (t.includes('cancel') || t.includes('refund')) return chatPresets.cancellation;
    return "I'm not sure I understood that. Feel free to ask about 'timings', 'venue', 'seats available', 'registration process', or 'pricing'!";
}
function renderChatbotQuickReplies() {
    const container = document.getElementById('chatbot-quick-replies');
    if (!container) return;
    container.innerHTML = `
        <span class="quick-reply-btn" onclick="selectQuickReply('timings','🕒 Event Timings')">Event Timings</span>
        <span class="quick-reply-btn" onclick="selectQuickReply('venue','📍 Event Venue')">Venue Locations</span>
        <span class="quick-reply-btn" onclick="selectQuickReply('seats','💺 Seats Available')">Seats Available</span>
        <span class="quick-reply-btn" onclick="selectQuickReply('process','📝 How to Register')">How to Register</span>
        <span class="quick-reply-btn" onclick="selectQuickReply('fees','💵 Fees & Pricing')">Fees & Pricing</span>
        <span class="quick-reply-btn" onclick="selectQuickReply('cancellation','❌ Cancellation Policy')">Cancellation Policy</span>`;
}
async function submitRegistration(e) {
    e.preventDefault();
    if (!validateRegistrationForm()) { showToast('Please correct form errors before submitting.', 'error'); return; }
    const payload = {
        name: document.getElementById('reg-name').value, email: document.getElementById('reg-email').value,
        phone: document.getElementById('reg-phone').value, company: document.getElementById('reg-org').value,
        eventId: document.getElementById('reg-event').value, city: document.getElementById('reg-city').value,
        gender: document.getElementById('gender-male').checked ? 'Male' : document.getElementById('gender-female').checked ? 'Female' : 'Other'
    };
    try {
        const result = await window.api.registerUser(payload);
        if (result.success) {
            showToast('Registration Successful!', 'success');
            document.getElementById('registration-form').reset();
            await loadInitialData();
            showTicketModal(result.registration, result.event, result.user);
        } else { showToast(result.message || 'Registration failed.', 'error'); }
    } catch (err) { showToast(err.message || 'Error occurred during registration.', 'error'); }
}
let activeTicketData = null;
function showTicketModal(reg, event, user) {
    activeTicketData = { reg, event, user };
    document.getElementById('ticket-user-name').innerText = user.name;
    document.getElementById('ticket-user-email').innerText = user.email;
    document.getElementById('ticket-event-title').innerText = event.title;
    document.getElementById('ticket-event-date').innerText = formatDate(event.date);
    document.getElementById('ticket-event-venue').innerText = event.venue;
    document.getElementById('ticket-id').innerText = `ID: ${reg._id}`;
    const qrText = encodeURIComponent(`RegID:${reg._id}|User:${user.name}|Event:${event.title}`);
    document.getElementById('ticket-qr').innerHTML = `<img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=${qrText}" alt="Ticket QR Code" style="max-width:100%;height:auto">`;
    setTimeout(() => showToast(`Email confirmation sent to ${user.email}!`, 'info'), 1500);
    new bootstrap.Modal(document.getElementById('ticketModal')).show();
}
function downloadTicketPDF() {
    if (!activeTicketData) return;
    const { reg, event, user } = activeTicketData;
    try {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF({ orientation: 'portrait', unit: 'mm', format: 'a6' });
        doc.setFillColor(15, 12, 35); doc.rect(0, 0, 105, 148, 'F');
        doc.setDrawColor(168, 85, 247); doc.setLineWidth(1.5);
        doc.line(5, 5, 100, 5); doc.line(100, 5, 100, 143); doc.line(100, 143, 5, 143); doc.line(5, 143, 5, 5);
        doc.setTextColor(255, 255, 255); doc.setFont('Helvetica', 'bold'); doc.setFontSize(14);
        doc.text("EVENT REGISTRATION", 52.5, 15, null, null, 'center');
        doc.setTextColor(129, 140, 248); doc.setFontSize(10); doc.text("EventAgent Prime — Official E-Ticket", 52.5, 20, null, null, 'center');
        doc.setDrawColor(255, 255, 255, 0.1); doc.setLineWidth(0.3); doc.line(10, 25, 95, 25);
        doc.setTextColor(255, 255, 255); doc.setFontSize(11); doc.text(event.title, 12, 33);
        doc.setFont('Helvetica', 'normal'); doc.setFontSize(8.5); doc.setTextColor(209, 213, 219);
        doc.text(`Date: ${formatDate(event.date)}`, 12, 40); doc.text(`Time: ${event.time}`, 12, 45);
        doc.text(`Venue: ${event.venue}`, 12, 50); doc.text(`Fee: ${parseFloat(event.fee) === 0 ? 'Free' : `Rs ${event.fee} INR`}`, 12, 55);
        doc.line(10, 60, 95, 60);
        doc.setTextColor(129, 140, 248); doc.setFont('Helvetica', 'bold'); doc.text("ATTENDEE DETAILS", 12, 67);
        doc.setTextColor(255, 255, 255); doc.setFont('Helvetica', 'normal');
        doc.text(`Name: ${user.name}`, 12, 74); doc.text(`Email: ${user.email}`, 12, 79); doc.text(`College/Org: ${user.company}`, 12, 84);
        doc.line(10, 89, 95, 89);
        doc.setFontSize(8); doc.setTextColor(156, 163, 175); doc.text(`Registration ID: ${reg._id}`, 52.5, 96, null, null, 'center');
        doc.setFillColor(16, 185, 129); doc.rect(20, 105, 65, 8, 'F');
        doc.setTextColor(255, 255, 255); doc.setFont('Helvetica', 'bold'); doc.setFontSize(9); doc.text("VALID ENTRY TICKET", 52.5, 110, null, null, 'center');
        doc.setFontSize(7); doc.setTextColor(156, 163, 175); doc.setFont('Helvetica', 'normal');
        doc.text("Please show this ticket at the entrance gate.", 52.5, 125, null, null, 'center');
        doc.text("EventAgent Prime · Knowfest AI Hub", 52.5, 130, null, null, 'center');
        doc.save(`Ticket_${event.title.replace(/\s+/g, '_')}_Receipt.pdf`);
        showToast('Receipt PDF downloaded!', 'success');
    } catch (err) { showToast('Error generating PDF receipt.', 'error'); }
}
function handleAdminLogin(e) {
    e.preventDefault();
    if (document.getElementById('admin-username').value === 'admin' && document.getElementById('admin-password').value === 'admin123') {
        state.isAdminLoggedIn = true; showToast('Logged in as Administrator.', 'success'); renderAdminDashboard();
    } else { showToast('Invalid admin credentials.', 'error'); }
}
function handleAdminLogout() { state.isAdminLoggedIn = false; showToast('Logged out of Admin Panel.', 'info'); renderAdminDashboard(); }
function renderAdminDashboard() {
    const viewContainer = document.getElementById('admin-content-area');
    if (!viewContainer) return;
    if (!state.isAdminLoggedIn) {
        viewContainer.innerHTML = `<div class="row justify-content-center my-5"><div class="col-md-6 col-lg-5"><div class="glass-card p-5"><div class="text-center mb-4"><div class="feature-icon mx-auto"><i class="fas fa-lock"></i></div><h3 class="fw-bold">Admin Portal</h3><p class="text-muted" style="font-size:.9rem">Authorized credentials required</p></div><form id="admin-login-form" onsubmit="handleAdminLogin(event)"><div class="form-floating mb-3"><input type="text" class="form-control" id="admin-username" placeholder="Username" required><label for="admin-username">Username</label></div><div class="form-floating mb-4"><input type="password" class="form-control" id="admin-password" placeholder="Password" required><label for="admin-password">Password</label></div><button type="submit" class="btn btn-gradient w-100 py-3">Access Dashboard</button></form><div class="text-center mt-3 text-muted" style="font-size:.85rem">Hint: <code>admin</code> / <code>admin123</code></div></div></div></div>`;
        return;
    }
    const totalEvents = state.events.length, totalRegs = state.registrations.length,
          totalSeats = state.events.reduce((s, e) => s + e.seatsTotal, 0),
          availSeats = state.events.reduce((s, e) => s + e.seatsAvailable, 0),
          waitingList = state.registrations.filter(r => r.status === 'Waiting').length;
    viewContainer.innerHTML = `
    <div class="d-flex justify-content-between align-items-center mb-5">
        <div><h2 class="fw-bold mb-1">Control Console</h2><p class="text-muted">Review, manage, and edit registrations and catalog listings.</p></div>
        <button onclick="handleAdminLogout()" class="btn btn-glass btn-sm"><i class="fas fa-sign-out-alt me-2"></i>Logout</button>
    </div>
    <div class="row mb-5">
        <div class="col-md-3 mb-4"><div class="glass-panel dashboard-stat-card"><div class="dashboard-stat-info"><h3>${totalEvents}</h3><p>Total Events</p></div><div class="dashboard-stat-icon"><i class="fas fa-calendar-week"></i></div></div></div>
        <div class="col-md-3 mb-4"><div class="glass-panel dashboard-stat-card"><div class="dashboard-stat-info"><h3>${totalRegs}</h3><p>Registrations</p></div><div class="dashboard-stat-icon"><i class="fas fa-id-card"></i></div></div></div>
        <div class="col-md-3 mb-4"><div class="glass-panel dashboard-stat-card"><div class="dashboard-stat-info"><h3>${availSeats}/${totalSeats}</h3><p>Seats Left</p></div><div class="dashboard-stat-icon"><i class="fas fa-chair"></i></div></div></div>
        <div class="col-md-3 mb-4"><div class="glass-panel dashboard-stat-card"><div class="dashboard-stat-info"><h3>${waitingList}</h3><p>Waiting List</p></div><div class="dashboard-stat-icon"><i class="fas fa-clock"></i></div></div></div>
    </div>
    <div class="glass-panel p-4 mb-5">
        <ul class="nav admin-tabs mb-4" id="adminTab" role="tablist">
            <li class="nav-item" role="presentation"><button class="nav-link active" data-bs-toggle="tab" data-bs-target="#admin-events-pane" type="button" role="tab">Event Catalog</button></li>
            <li class="nav-item" role="presentation"><button class="nav-link" data-bs-toggle="tab" data-bs-target="#admin-users-pane" type="button" role="tab">Registrations</button></li>
            <li class="nav-item" role="presentation"><button class="nav-link" data-bs-toggle="tab" data-bs-target="#admin-feedback-pane" type="button" role="tab">Feedback Received</button></li>
        </ul>
        <div class="tab-content">
            <div class="tab-pane fade show active" id="admin-events-pane" role="tabpanel">
                <div class="d-flex justify-content-between align-items-center mb-3"><h4 class="fw-bold">Available Listings</h4><button onclick="showAddEventModal()" class="btn btn-gradient btn-sm"><i class="fas fa-plus me-2"></i>Add New Event</button></div>
                <div class="glass-table table-responsive"><table class="table table-hover"><thead><tr><th>Event Title</th><th>Date/Time</th><th>Venue</th><th>Category</th><th>Seats</th><th>Fee</th><th class="text-end">Actions</th></tr></thead><tbody id="admin-events-list">${renderAdminEventsRows()}</tbody></table></div>
            </div>
            <div class="tab-pane fade" id="admin-users-pane" role="tabpanel">
                <h4 class="fw-bold mb-3">Active Registered Users</h4>
                <div class="glass-table table-responsive"><table class="table table-hover"><thead><tr><th>Reg ID</th><th>Name</th><th>Email</th><th>Event</th><th>Date</th><th>Status</th><th class="text-end">Action</th></tr></thead><tbody>${renderAdminRegistrationsRows()}</tbody></table></div>
            </div>
            <div class="tab-pane fade" id="admin-feedback-pane" role="tabpanel">
                <h4 class="fw-bold mb-3">User Inquiries &amp; Feedback</h4>
                <div class="glass-table table-responsive"><table class="table table-hover"><thead><tr><th>Sender</th><th>Email</th><th>Message</th><th>Date</th></tr></thead><tbody>${renderAdminFeedbackRows()}</tbody></table></div>
            </div>
        </div>
    </div>`;
}
function renderAdminEventsRows() {
    if (!state.events.length) return '<tr><td colspan="7" class="text-center text-muted">No events listed.</td></tr>';
    return state.events.map(e => `<tr><td class="fw-semibold">${e.title}</td><td>${formatDate(e.date)}<br><span class="text-muted" style="font-size:.8rem">${e.time}</span></td><td>${e.venue}</td><td><span class="badge bg-secondary">${e.category}</span></td><td>${e.seatsAvailable}/${e.seatsTotal}</td><td>${parseFloat(e.fee) === 0 ? 'Free' : `₹${e.fee}`}</td><td class="text-end"><button onclick="showEditEventModal('${e._id}')" class="btn btn-sm btn-glass text-warning border-0 p-1 me-2" title="Edit"><i class="far fa-edit"></i></button><button onclick="handleDeleteEvent('${e._id}')" class="btn btn-sm btn-glass text-danger border-0 p-1" title="Delete"><i class="far fa-trash-alt"></i></button></td></tr>`).join('');
}
function renderAdminRegistrationsRows() {
    if (!state.registrations.length) return '<tr><td colspan="7" class="text-center text-muted">No registrations logged yet.</td></tr>';
    return state.registrations.map(r => `<tr><td class="font-monospace" style="font-size:.8rem">${r._id}</td><td>${r.userName}</td><td>${r.userEmail}</td><td class="fw-semibold">${r.eventTitle}</td><td>${formatDate(r.regDate)}</td><td><span class="badge bg-success">${r.status || 'Registered'}</span></td><td class="text-end"><button onclick="handleCancelRegistration('${r._id}')" class="btn btn-sm btn-glass text-danger border-0 p-1" title="Cancel"><i class="fas fa-user-minus"></i></button></td></tr>`).join('');
}
function renderAdminFeedbackRows() {
    if (!state.feedback.length) return '<tr><td colspan="4" class="text-center text-muted">No inquiries received.</td></tr>';
    return state.feedback.map(f => `<tr><td class="fw-semibold">${f.name}</td><td>${f.email}</td><td>${f.message}</td><td>${formatDate(f.date)}</td></tr>`).join('');
}
let editingEventId = null;
function showAddEventModal() { editingEventId = null; document.getElementById('eventModalLabel').innerText = 'Add New Event'; document.getElementById('event-form').reset(); new bootstrap.Modal(document.getElementById('eventFormModal')).show(); }
function showEditEventModal(id) {
    editingEventId = id; const event = state.events.find(e => e._id === id); if (!event) return;
    document.getElementById('eventModalLabel').innerText = 'Edit Event Details';
    document.getElementById('evt-title').value = event.title; document.getElementById('evt-date').value = event.date;
    document.getElementById('evt-time').value = event.time; document.getElementById('evt-venue').value = event.venue;
    document.getElementById('evt-category').value = event.category; document.getElementById('evt-fee').value = event.fee;
    document.getElementById('evt-seats').value = event.seatsTotal; document.getElementById('evt-speaker').value = event.speaker;
    document.getElementById('evt-speaker-title').value = event.speakerTitle || ''; document.getElementById('evt-image').value = event.image || '';
    document.getElementById('evt-desc').value = event.description;
    new bootstrap.Modal(document.getElementById('eventFormModal')).show();
}
async function handleEventFormSubmit(e) {
    e.preventDefault();
    const payload = { title: document.getElementById('evt-title').value, date: document.getElementById('evt-date').value, time: document.getElementById('evt-time').value, venue: document.getElementById('evt-venue').value, category: document.getElementById('evt-category').value, fee: document.getElementById('evt-fee').value, seatsTotal: parseInt(document.getElementById('evt-seats').value), speaker: document.getElementById('evt-speaker').value, speakerTitle: document.getElementById('evt-speaker-title').value, image: document.getElementById('evt-image').value || 'https://images.unsplash.com/photo-1501281668745-f7f57925c3b4?auto=format&fit=crop&q=80&w=800', description: document.getElementById('evt-desc').value };
    try {
        if (editingEventId) { await window.api.updateEvent(editingEventId, payload); showToast('Event updated successfully.', 'success'); }
        else { await window.api.createEvent(payload); showToast('Event listing created.', 'success'); }
        const modalEl = document.getElementById('eventFormModal'); const modal = bootstrap.Modal.getInstance(modalEl); if (modal) modal.hide();
        await loadInitialData(); renderAdminDashboard();
    } catch (err) { showToast('Failed to save event.', 'error'); }
}
async function handleDeleteEvent(id) {
    if (!confirm('Are you sure you want to delete this event?')) return;
    try { await window.api.deleteEvent(id); showToast('Event deleted.', 'warning'); await loadInitialData(); renderAdminDashboard(); } catch (err) { showToast('Failed to delete event.', 'error'); }
}
async function handleCancelRegistration(id) {
    if (!confirm('Are you sure you want to cancel this registration?')) return;
    try { await window.api.deleteRegistration(id); showToast('Registration cancelled.', 'warning'); await loadInitialData(); renderAdminDashboard(); } catch (err) { showToast('Failed to cancel registration.', 'error'); }
}
function showToast(message, type = 'info') {
    const container = document.getElementById('toast-container'); if (!container) return;
    const toast = document.createElement('div'); toast.className = `custom-toast ${type}`;
    let icon = 'info-circle';
    if (type === 'success') icon = 'check-circle'; if (type === 'error') icon = 'exclamation-circle'; if (type === 'warning') icon = 'exclamation-triangle';
    toast.innerHTML = `<i class="fas fa-${icon}"></i><div>${message}</div><button class="custom-toast-close" onclick="this.parentElement.remove()"><i class="fas fa-times"></i></button>`;
    container.appendChild(toast);
    setTimeout(() => { toast.style.animation = 'toast-slide-in .3s reverse forwards'; setTimeout(() => toast.remove(), 300); }, 4000);
}
function getSeatsClass(avail) { return avail === 0 ? 'danger' : avail < 10 ? 'warning' : 'success'; }
function formatDate(dateStr) { return new Date(dateStr).toLocaleDateString('en-US', { year: 'numeric', month: 'short', day: 'numeric' }); }
function setupEventListeners() {
    const toggleBtn = document.getElementById('theme-toggle'); if (toggleBtn) toggleBtn.addEventListener('click', toggleTheme);
    const chatSend = document.getElementById('chat-send-btn'); if (chatSend) chatSend.addEventListener('click', handleChatSend);
    const chatInput = document.getElementById('chat-input-text'); if (chatInput) chatInput.addEventListener('keypress', e => { if (e.key === 'Enter') handleChatSend(); });
    const regForm = document.getElementById('registration-form'); if (regForm) regForm.addEventListener('submit', submitRegistration);
    const contactForm = document.getElementById('contact-form'); if (contactForm) contactForm.addEventListener('submit', submitContactForm);
    const eventForm = document.getElementById('event-form'); if (eventForm) eventForm.addEventListener('submit', handleEventFormSubmit);
}
// Global scope exports
window.filterCategory = filterCategory; window.searchEvents = searchEvents;
window.triggerRegisterForEvent = triggerRegisterForEvent; window.triggerRegisterCurrent = triggerRegisterCurrent;
window.selectQuickReply = selectQuickReply; window.downloadTicketPDF = downloadTicketPDF;
window.handleAdminLogin = handleAdminLogin; window.handleAdminLogout = handleAdminLogout;
window.showAddEventModal = showAddEventModal; window.showEditEventModal = showEditEventModal;
window.handleDeleteEvent = handleDeleteEvent; window.handleCancelRegistration = handleCancelRegistration;
</script>
</body>
</html>

