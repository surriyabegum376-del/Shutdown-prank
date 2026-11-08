<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Shutdown Prank</title>
<style>
  * { box-sizing: border-box; }
  body {
    margin: 0; min-height: 100vh; background: #050505; color: white;
    font-family: Arial, sans-serif; display: grid; place-items: center;
    overflow: hidden;
  }
  .screen { text-align: center; padding: 24px; width: 100%; }
  .logo { font-size: 42px; margin-bottom: 24px; }
  .message { font-size: 19px; letter-spacing: .4px; }
  .sub { color: #888; font-size: 13px; margin-top: 12px; }
  .bar { width: 150px; height: 3px; background: #333; margin: 30px auto; overflow: hidden; }
  .bar span { display: block; height: 100%; width: 0; background: white; animation: load 3s ease-in forwards; }
  @keyframes load { to { width: 100%; } }
  .hidden { display: none; }
  button {
    margin-top: 28px; border: 1px solid #666; color: white; background: #171717;
    border-radius: 24px; padding: 12px 22px; font-size: 15px;
  }
  .hint { position: fixed; bottom: 18px; color: #666; font-size: 11px; }
</style>
</head>
<body>
<div class="screen" id="start">
  <div class="logo">⏻</div>
  <div class="message">Shutting down…</div>
  <div class="bar"><span></span></div>
  <div class="sub">Please wait</div>
</div>
<div class="screen hidden" id="off">
  <div class="logo">⏻</div>
  <div class="message">Device is powered off</div>
  <div class="sub">This is only a prank screen.</div>
  <button onclick="restart()">Turn screen back on</button>
</div>
<div class="hint">Tap anywhere to reveal the prank controls</div>
<script>
  const start = document.getElementById('start');
  const off = document.getElementById('off');
  setTimeout(() => { start.classList.add('hidden'); off.classList.remove('hidden'); }, 3200);
  function restart() {
    off.classList.add('hidden');
    start.classList.remove('hidden');
    document.querySelector('.bar span').style.animation = 'none';
    void document.querySelector('.bar span').offsetWidth;
    document.querySelector('.bar span').style.animation = 'load 3s ease-in forwards';
    setTimeout(() => { start.classList.add('hidden'); off.classList.remove('hidden'); }, 3200);
  }
  document.addEventListener('keydown', e => { if (e.key === 'Escape') restart(); });
</script>
</body>
</html># Shutdown-prank
