<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Praveen S — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent: #7c3aed;
    --accent2: #06b6d4;
    --accent3: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: rgba(124, 58, 237, 0.4);
    --glow2: rgba(6, 182, 212, 0.3);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(124,58,237,0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,58,237,0.06) 1px, transparent 1px);
    background-size: 40px 40px;
    animation: gridMove 20s linear infinite;
    pointer-events: none;
    z-index: 0;
  }

  @keyframes gridMove {
    0% { transform: translateY(0); }
    100% { transform: translateY(40px); }
  }

  /* Floating orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.25;
    animation: float 8s ease-in-out infinite;
    pointer-events: none;
    z-index: 0;
  }
  .orb1 { width: 400px; height: 400px; background: var(--accent); top: -100px; left: -100px; animation-delay: 0s; }
  .orb2 { width: 300px; height: 300px; background: var(--accent2); bottom: 100px; right: -80px; animation-delay: -3s; }
  .orb3 { width: 200px; height: 200px; background: var(--accent3); top: 50%; left: 50%; animation-delay: -6s; }

  @keyframes float {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(-30px) scale(1.05); }
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px;
    position: relative;
    z-index: 1;
  }

  /* Header */
  .header {
    text-align: center;
    margin-bottom: 60px;
    animation: fadeInDown 0.8s ease forwards;
    opacity: 0;
  }

  @keyframes fadeInDown {
    from { opacity: 0; transform: translateY(-30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .wave {
    display: inline-block;
    font-size: 2.5rem;
    animation: wave 2s ease-in-out infinite;
    transform-origin: 70% 70%;
  }

  @keyframes wave {
    0%, 100% { transform: rotate(0deg); }
    20% { transform: rotate(25deg); }
    40% { transform: rotate(-10deg); }
    60% { transform: rotate(20deg); }
    80% { transform: rotate(-5deg); }
  }

  .name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.2rem, 5vw, 3.5rem);
    font-weight: 800;
    background: linear-gradient(135deg, #fff 0%, var(--accent2) 50%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1.1;
    margin: 12px 0 8px;
  }

  .tagline {
    font-family: 'Space Mono', monospace;
    color: var(--accent2);
    font-size: 1rem;
    letter-spacing: 0.05em;
  }

  .typing-cursor {
    display: inline-block;
    width: 2px;
    height: 1em;
    background: var(--accent2);
    margin-left: 2px;
    animation: blink 1s step-end infinite;
    vertical-align: text-bottom;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  /* Cards */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 32px;
    margin-bottom: 24px;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
    animation: fadeInUp 0.6s ease forwards;
    opacity: 0;
  }

  .card:hover {
    transform: translateY(-4px);
    border-color: var(--accent);
    box-shadow: 0 0 40px var(--glow);
  }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity 0.3s;
  }
  .card:hover::before { opacity: 1; }

  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .card:nth-child(1) { animation-delay: 0.2s; }
  .card:nth-child(2) { animation-delay: 0.35s; }
  .card:nth-child(3) { animation-delay: 0.5s; }
  .card:nth-child(4) { animation-delay: 0.65s; }
  .card:nth-child(5) { animation-delay: 0.8s; }

  .card-title {
    font-size: 0.7rem;
    font-family: 'Space Mono', monospace;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .card-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* Info list */
  .info-list { list-style: none; }

  .info-item {
    display: flex;
    align-items: flex-start;
    gap: 14px;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    font-size: 0.95rem;
    transition: color 0.2s;
  }

  .info-item:last-child { border-bottom: none; }
  .info-item:hover { color: #fff; }

  .info-emoji {
    font-size: 1.2rem;
    min-width: 28px;
    text-align: center;
    animation: pulse 3s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.15); }
  }

  .info-item:nth-child(1) .info-emoji { animation-delay: 0s; }
  .info-item:nth-child(2) .info-emoji { animation-delay: 0.4s; }
  .info-item:nth-child(3) .info-emoji { animation-delay: 0.8s; }
  .info-item:nth-child(4) .info-emoji { animation-delay: 1.2s; }
  .info-item:nth-child(5) .info-emoji { animation-delay: 1.6s; }
  .info-item:nth-child(6) .info-emoji { animation-delay: 2s; }

  .info-label { color: var(--muted); font-size: 0.8rem; margin-bottom: 2px; font-family: 'Space Mono', monospace; }
  .info-value { color: var(--text); }

  a {
    color: var(--accent2);
    text-decoration: none;
    transition: color 0.2s, text-shadow 0.2s;
  }
  a:hover {
    color: #fff;
    text-shadow: 0 0 12px var(--accent2);
  }

  /* Skills grid */
  .skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .skill-badge {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 14px;
    background: rgba(124,58,237,0.08);
    border: 1px solid rgba(124,58,237,0.25);
    border-radius: 8px;
    font-family: 'Space Mono', monospace;
    font-size: 0.78rem;
    color: var(--text);
    transition: all 0.3s ease;
    cursor: default;
    animation: popIn 0.4s ease backwards;
  }

  .skill-badge:hover {
    background: rgba(124,58,237,0.25);
    border-color: var(--accent);
    color: #fff;
    transform: scale(1.06) translateY(-2px);
    box-shadow: 0 4px 20px var(--glow);
  }

  .skill-badge img { width: 20px; height: 20px; object-fit: contain; }

  @keyframes popIn {
    from { opacity: 0; transform: scale(0.8); }
    to { opacity: 1; transform: scale(1); }
  }

  /* Connect section */
  .social-row {
    display: flex;
    gap: 14px;
    flex-wrap: wrap;
    align-items: center;
  }

  .social-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 12px 22px;
    border-radius: 10px;
    font-family: 'Space Mono', monospace;
    font-size: 0.82rem;
    font-weight: 700;
    text-decoration: none;
    transition: all 0.3s ease;
    border: 1px solid;
    position: relative;
    overflow: hidden;
  }

  .social-btn::after {
    content: '';
    position: absolute;
    inset: 0;
    background: white;
    opacity: 0;
    transition: opacity 0.2s;
  }

  .social-btn:hover::after { opacity: 0.06; }

  .linkedin-btn {
    background: rgba(10,102,194,0.15);
    border-color: rgba(10,102,194,0.5);
    color: #60a5fa;
  }
  .linkedin-btn:hover {
    border-color: #60a5fa;
    box-shadow: 0 4px 24px rgba(96,165,250,0.3);
    transform: translateY(-2px);
    color: #93c5fd;
    text-shadow: none;
  }

  .portfolio-btn {
    background: linear-gradient(135deg, rgba(124,58,237,0.2), rgba(6,182,212,0.2));
    border-color: var(--accent);
    color: #a78bfa;
  }
  .portfolio-btn:hover {
    background: linear-gradient(135deg, rgba(124,58,237,0.4), rgba(6,182,212,0.3));
    box-shadow: 0 4px 24px var(--glow);
    transform: translateY(-2px);
    color: #c4b5fd;
    text-shadow: none;
  }

  /* Stats */
  .stats-img {
    width: 100%;
    border-radius: 10px;
    border: 1px solid var(--border);
    transition: filter 0.3s, transform 0.3s;
    filter: saturate(1.2);
  }
  .stats-img:hover { filter: saturate(1.6) brightness(1.1); transform: scale(1.01); }

  /* Fun fact */
  .fun-fact {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 16px 20px;
    background: linear-gradient(135deg, rgba(245,158,11,0.1), rgba(124,58,237,0.1));
    border: 1px solid rgba(245,158,11,0.3);
    border-radius: 12px;
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    color: var(--accent3);
    margin-top: 16px;
    animation: shimmer 4s ease-in-out infinite;
  }

  @keyframes shimmer {
    0%, 100% { border-color: rgba(245,158,11,0.3); }
    50% { border-color: rgba(245,158,11,0.7); box-shadow: 0 0 20px rgba(245,158,11,0.15); }
  }

  /* Status badge */
  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 6px 14px;
    background: rgba(6,182,212,0.1);
    border: 1px solid rgba(6,182,212,0.3);
    border-radius: 999px;
    font-family: 'Space Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent2);
    margin-top: 12px;
  }

  .status-dot {
    width: 7px; height: 7px;
    background: var(--accent2);
    border-radius: 50%;
    animation: statusPulse 2s ease-in-out infinite;
  }

  @keyframes statusPulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(6,182,212,0.6); }
    50% { box-shadow: 0 0 0 6px rgba(6,182,212,0); }
  }

  /* Divider */
  .section-divider {
    display: flex;
    align-items: center;
    gap: 16px;
    margin: 8px 0 20px;
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
  }
  .section-divider::before, .section-divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* Responsive */
  @media (max-width: 600px) {
    .container { padding: 40px 16px; }
    .card { padding: 20px; }
    .name { font-size: 2rem; }
  }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<div class="container">

  <!-- HEADER -->
  <div class="header">
    <div><span class="wave">👋</span></div>
    <h1 class="name">Hi, I'm Praveen S</h1>
    <p class="tagline">A passionate Full Stack Developer from India<span class="typing-cursor"></span></p>
    <div class="status-badge">
      <span class="status-dot"></span>
      Open to opportunities &amp; collaborations
    </div>
  </div>

  <!-- ABOUT -->
  <div class="card">
    <div class="card-title">// about me</div>
    <ul class="info-list">
      <li class="info-item">
        <span class="info-emoji">🔭</span>
        <div>
          <div class="info-label">Currently Working On</div>
          <div class="info-value"><strong>AI Development</strong> and <strong>E-Commerce</strong></div>
        </div>
      </li>
      <li class="info-item">
        <span class="info-emoji">🌱</span>
        <div>
          <div class="info-label">Current Company</div>
          <div class="info-value"><strong>Treezenterprise Software Solutions</strong></div>
        </div>
      </li>
      <li class="info-item">
        <span class="info-emoji">👨‍💻</span>
        <div>
          <div class="info-label">Portfolio</div>
          <div class="info-value"><a href="https://praveenportfolio-omega.vercel.app/" target="_blank">praveenportfolio-omega.vercel.app ↗</a></div>
        </div>
      </li>
      <li class="info-item">
        <span class="info-emoji">💬</span>
        <div>
          <div class="info-label">Ask Me About</div>
          <div class="info-value">Java · SQL · JDBC · HTML5 · CSS3 · JavaScript · Shopify</div>
        </div>
      </li>
      <li class="info-item">
        <span class="info-emoji">📫</span>
        <div>
          <div class="info-label">Reach Me At</div>
          <div class="info-value"><a href="mailto:madivalp67@gmail.com">madivalp67@gmail.com</a></div>
        </div>
      </li>
      <li class="info-item">
        <span class="info-emoji">📄</span>
        <div>
          <div class="info-label">Resume / Experience</div>
          <div class="info-value"><a href="https://praveenportfolio-omega.vercel.app/updatedresume.pdf" target="_blank">View my resume ↗</a></div>
        </div>
      </li>
    </ul>
    <div class="fun-fact">
      <span>⚡</span>
      <span>Fun fact — I think I am funny 😄</span>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="card">
    <div class="card-title">// connect with me</div>
    <div class="social-row">
      <a href="https://www.linkedin.com/in/praveen-s-486903266/" target="_blank" class="social-btn linkedin-btn">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M19 0H5C2.24 0 0 2.24 0 5v14c0 2.76 2.24 5 5 5h14c2.76 0 5-2.24 5-5V5c0-2.76-2.24-5-5-5zM8 19H5V8h3v11zM6.5 6.73A1.77 1.77 0 1 1 6.5 3.2a1.77 1.77 0 0 1 0 3.53zM20 19h-3v-5.6c0-3.37-4-3.12-4 0V19h-3V8h3v1.77C14.4 7.08 20 6.88 20 12.3V19z"/></svg>
        LinkedIn
      </a>
      <a href="https://praveenportfolio-omega.vercel.app/" target="_blank" class="social-btn portfolio-btn">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
        Portfolio
      </a>
    </div>
  </div>

  <!-- LANGUAGES & TOOLS -->
  <div class="card">
    <div class="card-title">// languages &amp; tools</div>
    <div class="skills-grid" id="skillsGrid">
      <div class="skill-badge" style="animation-delay:0.1s"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="HTML5"> HTML5</div>
      <div class="skill-badge" style="animation-delay:0.15s"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="CSS3"> CSS3</div>
      <div class="skill-badge" style="animation-delay:0.2s"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="JavaScript"> JavaScript</div>
      <div class="skill-badge" style="animation-delay:0.25s"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="Java"> Java</div>
      <div class="skill-badge" style="animation-delay:0.3s"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="MySQL"> MySQL</div>
      <div class="skill-badge" style="animation-delay:0.35s"><img src="https://www.svgrepo.com/show/303229/microsoft-sql-server-logo.svg" alt="MSSQL"> MS SQL Server</div>
      <div class="skill-badge" style="animation-delay:0.4s"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="PostgreSQL"> PostgreSQL</div>
      <div class="skill-badge" style="animation-delay:0.45s"><img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="Git"> Git</div>
      <div class="skill-badge" style="animation-delay:0.5s">
        <svg width="20" height="20" viewBox="0 0 109.5 124.5" fill="#96bf48"><path d="M99.8 2.6C92.6-1.4 83.8.6 79 7.4L68.2 23.6C61.5 20.5 54.1 19 46.3 19.2 28.2 19.8 11.9 29.2 3 44.4L3 44.5c-9.1 16.1-7.7 35.9 3.5 50.4l.1.1.1.1c7.9 10.3 19.2 17.7 32 20.5 1.7.4 3.5.7 5.3.9.6.1 1.2.1 1.8.2 1.5.1 3 .2 4.6.2 9.5 0 18.7-2.5 26.7-7.1l18.2 11.1c7.3 4.4 16.6 1.8 20.6-5.8.7-1.3 1.2-2.7 1.5-4.2l7.1-95.3c.5-5.8-2.2-11.4-6.7-14.9z"/></svg>
        Shopify
      </div>
    </div>
  </div>

  <!-- GITHUB STATS -->
  <div class="card">
    <div class="card-title">// github stats</div>
    <img
      class="stats-img"
      src="https://github-readme-stats.vercel.app/api/top-langs?username=pavi14321&show_icons=true&locale=en&layout=compact&theme=tokyonight&hide_border=true&bg_color=111118"
      alt="Top Languages"
      loading="lazy"
    />
  </div>

</div>

<script>
  // Stagger card animations on scroll
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) e.target.style.animationPlayState = 'running';
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.card').forEach(c => {
    c.style.animationPlayState = 'paused';
    observer.observe(c);
  });

  // Typing effect for tagline
  const taglineEl = document.querySelector('.tagline');
  const fullText = 'A passionate Full Stack Developer from India';
  let i = 0;
  taglineEl.innerHTML = '<span class="typing-cursor"></span>';

  function type() {
    if (i < fullText.length) {
      taglineEl.innerHTML = fullText.slice(0, ++i) + '<span class="typing-cursor"></span>';
      setTimeout(type, 40 + Math.random() * 30);
    }
  }

  setTimeout(type, 800);

  // Skill badge stagger
  document.querySelectorAll('.skill-badge').forEach((b, i) => {
    b.style.animationDelay = `${0.65 + i * 0.06}s`;
  });
</script>
</body>
</html>
