<!-- Intro 
<h3 align="center">
        <samp>&gt; Hey There!, I am
                <b><a target="_blank" href="https://usmimukherjee.github.io/">Usmi Mukherjee</a></b> 
        </samp>
</h3>


<p align="center"> 
  <samp>
    <a href="https://www.google.com/search?q=Usmi+Mukherjee">「 Google Me 」</a>
    <br>
     I am a PhD student from <b>India</b> studying at Dalhousie University at <a href="https://github.com/RAISEDAL">「 RAISE Lab」</a>
    <br>
    <br>
        My Research Areas are - Software Engineering, NLP, and Simulation Modelling
  </samp>
</p>
<br />
 -->

 <!-- Interactive Intro -->
<div class="intro-wrap" role="region" aria-label="Intro">
  <h3 class="intro-title" aria-live="polite">
    <span class="prompt">&gt;</span>
    <span id="typewriter"></span>
    <span class="cursor" aria-hidden="true"></span>
  </h3>

  <p class="intro-sub">
    <a class="link-btn" href="https://www.google.com/search?q=Usmi+Mukherjee" rel="noopener">Google Me</a>
    <span class="dot">•</span>
    I am a PhD student from <b>India</b> studying at Dalhousie University at
    <a class="link-underline" href="https://github.com/RAISEDAL" rel="noopener">RAISE Lab</a>
  </p>

  <div class="chips" aria-label="Research areas">
    <button class="chip" data-words='["Software Engineering","NLP","Simulation Modelling"]' id="rotating-chip" type="button" aria-live="polite">
      Software Engineering
    </button>
    <button class="chip" id="copy-email" type="button" title="Copy email to clipboard">Copy Email</button>
    <a class="chip link-chip" href="https://usmimukherjee.github.io/" rel="noopener">Portfolio</a>
  </div>
</div>

<style>
  .intro-wrap { 
    --fg:#e5e7eb; --muted:#a1a1aa; --accent:#38bdf8;
    --chip-bg: rgba(255,255,255,0.06);
    --chip-brd: rgba(255,255,255,0.15);
    text-align:center; margin: 28px auto; max-width: 820px; padding: 0 12px;
    font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Inter, "Helvetica Neue", Arial, "Noto Sans", "Apple Color Emoji", "Segoe UI Emoji";
    color: var(--fg);
  }
  .intro-title { 
    display:inline-block; margin: 0 0 12px; font-weight: 700; 
    font-size: clamp(20px, 3.2vw, 30px); letter-spacing: .2px;
  }
  .prompt { color: var(--muted); margin-right: 6px }
  .cursor { display:inline-block; width: .6ch; height: 1.1em; translate: 0 .15em; 
            background: currentColor; opacity: .8; animation: blink 1s steps(1,end) infinite }
  @keyframes blink { 50% { opacity: 0; } }

  .intro-sub { 
    margin: 6px auto 14px; color: var(--muted); line-height: 1.6; 
    font-size: clamp(14px, 2.4vw, 16px);
  }
  .dot { margin: 0 8px; opacity: .6 }

  .link-underline {
    color: var(--fg); position: relative; text-decoration: none;
  }
  .link-underline::after {
    content:""; position:absolute; left:0; bottom:-2px; height:2px; width:100%;
    transform: scaleX(0); transform-origin:left; background: linear-gradient(90deg, var(--accent), #a78bfa);
    transition: transform .28s ease;
  }
  .link-underline:hover::after { transform: scaleX(1); }

  .link-btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 6px 12px; border-radius: 999px; border: 1px solid var(--chip-brd);
    background: var(--chip-bg); color: var(--fg); text-decoration: none; 
    font-size: 14px; transition: transform .06s ease, background .25s ease, border-color .25s ease;
  }
  .link-btn:hover { background: rgba(56,189,248,.12); border-color: rgba(56,189,248,.45); }
  .link-btn:active { transform: translateY(1px) scale(.98); }

  .chips { display:flex; justify-content:center; gap: 10px; flex-wrap: wrap; margin-top: 8px; }
  .chip, .link-chip {
    display:inline-flex; align-items:center; gap:8px; cursor:pointer;
    padding: 8px 14px; border-radius: 999px; border: 1px solid var(--chip-brd);
    background: var(--chip-bg); color: var(--fg); font-size: 14px;
    transition: transform .08s ease, background .25s ease, border-color .25s ease, box-shadow .25s ease;
    text-decoration:none;
  }
  .chip:hover, .link-chip:hover { 
    background: rgba(167,139,250,.12); border-color: rgba(167,139,250,.45);
    box-shadow: 0 6px 18px rgba(167,139,250,.12);
  }
  .chip:active { transform: translateY(1px) scale(.98); }

  /* Respect users who prefer reduced motion */
  @media (prefers-reduced-motion: reduce) {
    .cursor { animation: none; }
    .link-underline::after { transition: none; }
    .chip, .link-chip, .link-btn { transition: none; }
  }
</style>

<script>
  // --- Typewriter for the greeting line ---
  (function typewriter(elId, text, speed){
    const el = document.getElementById(elId);
    if(!el) return;
    let i = 0;
    const tick = () => {
      el.textContent = text.slice(0, i++);
      if (i <= text.length) {
        setTimeout(tick, speed);
      }
    };
    // Fallback for users with reduced motion: print instantly
    const reduced = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    if (reduced) { el.textContent = text; return; }
    tick();
  })('typewriter', 'Hey there, I am Usmi Mukherjee', 28);

  // --- Rotating research areas on a chip ---
  (function rotateWords(btnId){
    const el = document.getElementById(btnId);
    if(!el) return;
    const words = JSON.parse(el.getAttribute('data-words') || '[]');
    if(!words.length) return;
    let idx = 0;
    const reduced = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    // Click to advance immediately; otherwise auto-rotate every 2.2s
    const next = () => { idx = (idx + 1) % words.length; el.textContent = words[idx]; };
    el.addEventListener('click', next);
    if (!reduced) setInterval(next, 2200);
  })('rotating-chip');

  // --- Copy email button ---
  (function setupCopy(btnId, email){
    const btn = document.getElementById(btnId);
    if(!btn) return;
    const original = 'Copy Email';
    btn.addEventListener('click', async () => {
      try {
        await navigator.clipboard.writeText(email);
        btn.textContent = 'Copied!';
        setTimeout(() => (btn.textContent = original), 1200);
      } catch (e) {
        btn.textContent = email; // fallback: reveal the email
        setTimeout(() => (btn.textContent = original), 3000);
      }
    });
  })('copy-email', 'usmimukherjee@dal.ca');
</script>

