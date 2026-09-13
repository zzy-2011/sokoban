(() => {
  'use strict';
  const cv = document.getElementById('game'); const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  const dpr = Math.max(1, Math.min(3, window.devicePixelRatio || 1));
  cv.width = W * dpr; cv.height = H * dpr; ctx.scale(dpr, dpr);
  const movesEl = document.getElementById('moves'), timeEl = document.getElementById('time');
  const overlay = document.getElementById('overlay'), ovTitle = document.getElementById('ov-title'), ovSub = document.getElementById('ov-sub');
  const COLS = 4, ROWS = 5, CELL = Math.min(Math.floor(W / COLS), Math.floor(H / ROWS));
  const ox = (W - COLS * CELL) / 2, oy = (H - ROWS * CELL) / 2;
  let pieces, sel, over, moves, timer, secs;

  function initPieces() {
    pieces = [
      { id: 'cao', x: 1, y: 0, w: 2, h: 2, color: '#ff5c7a', name: '曹操' },
      { id: 'v1', x: 0, y: 0, w: 1, h: 2, color: '#4fd1ff', name: '将' },
      { id: 'v2', x: 3, y: 0, w: 1, h: 2, color: '#4fd1ff', name: '将' },
      { id: 'v3', x: 0, y: 2, w: 1, h: 2, color: '#4fd1ff', name: '将' },
      { id: 'v4', x: 3, y: 2, w: 1, h: 2, color: '#4fd1ff', name: '将' },
      { id: 'h1', x: 1, y: 2, w: 2, h: 1, color: '#ffd23f', name: '关' },
      { id: 's1', x: 0, y: 4, w: 1, h: 1, color: '#43d97a', name: '兵' },
      { id: 's2', x: 1, y: 4, w: 1, h: 1, color: '#43d97a', name: '兵' },
      { id: 's3', x: 2, y: 4, w: 1, h: 1, color: '#43d97a', name: '兵' },
      { id: 's4', x: 3, y: 4, w: 1, h: 1, color: '#43d97a', name: '兵' }
    ];
  }
  function occupied() {
    const g = Array(ROWS * COLS).fill(null);
    for (const p of pieces) for (let yy = 0; yy < p.h; yy++) for (let xx = 0; xx < p.w; xx++) g[(p.y + yy) * COLS + (p.x + xx)] = p.id;
    return g;
  }
  function canMove(p, dx, dy) {
    const g = occupied();
    for (let yy = 0; yy < p.h; yy++) for (let xx = 0; xx < p.w; xx++) {
      const nx = p.x + xx + dx, ny = p.y + yy + dy;
      if (nx < 0 || nx >= COLS || ny < 0 || ny >= ROWS) return false;
      if (g[ny * COLS + nx] && g[ny * COLS + nx] !== p.id) return false;
    }
    return true;
  }
  function moveSel(dx, dy) {
    if (over || !sel) return;
    const p = pieces.find(x => x.id === sel); if (!p) return;
    if (canMove(p, dx, dy)) { p.x += dx; p.y += dy; moves++; movesEl.textContent = moves; if (p.id === 'cao' && p.x === 1 && p.y === 3) win(); }
  }
  function win() { over = true; if (timer) clearInterval(timer); ovTitle.textContent = '过关！'; ovSub.textContent = '步数 ' + moves + ' · 用时 ' + secs + ' 秒'; overlay.classList.remove('hidden'); }
  function draw() {
    ctx.fillStyle = '#1a1c3a'; ctx.fillRect(0, 0, W, H);
    ctx.fillStyle = 'rgba(255,255,255,0.06)'; ctx.fillRect(ox, oy, COLS * CELL, ROWS * CELL);
    for (const p of pieces) {
      const x = ox + p.x * CELL, y = oy + p.y * CELL;
      ctx.fillStyle = p.id === sel ? '#fff' : p.color;
      ctx.fillRect(x + 2, y + 2, p.w * CELL - 4, p.h * CELL - 4);
      ctx.fillStyle = '#10122a'; ctx.font = 'bold ' + (p.h > 1 ? 18 : 14) + 'px sans-serif'; ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
      ctx.fillText(p.name, x + p.w * CELL / 2, y + p.h * CELL / 2);
    }
    // 出口提示
    ctx.fillStyle = 'rgba(67,217,122,0.5)'; ctx.fillRect(ox + 1 * CELL, oy + 3 * CELL, 2 * CELL, 2 * CELL);
  }
  function pieceAt(px, py) {
    const c = Math.floor((px - ox) / CELL), r = Math.floor((py - oy) / CELL);
    if (c < 0 || c >= COLS || r < 0 || r >= ROWS) return null;
    return occupied()[r * COLS + c];
  }
  cv.addEventListener('click', e => { const rect = cv.getBoundingClientRect(); const px = (e.clientX - rect.left) / rect.width * W, py = (e.clientY - rect.top) / rect.height * H; sel = pieceAt(px, py); });
  cv.addEventListener('touchend', e => { const t = e.changedTouches[0]; const rect = cv.getBoundingClientRect(); const px = (t.clientX - rect.left) / rect.width * W, py = (t.clientY - rect.top) / rect.height * H; sel = pieceAt(px, py); }, { passive: true });
  const KM = { ArrowUp: [0, -1], ArrowDown: [0, 1], ArrowLeft: [-1, 0], ArrowRight: [1, 0], w: [0, -1], s: [0, 1], a: [-1, 0], d: [1, 0], W: [0, -1], S: [0, 1], A: [-1, 0], D: [1, 0] };
  window.addEventListener('keydown', e => { if (KM[e.key]) { e.preventDefault(); const [dx, dy] = KM[e.key]; moveSel(dx, dy); } });
  let sx = 0, sy = 0;
  cv.addEventListener('touchstart', e => { const t = e.changedTouches[0]; sx = t.clientX; sy = t.clientY; }, { passive: true });
  cv.addEventListener('touchend', e => {
    if (sel) { const t = e.changedTouches[0]; const dx = t.clientX - sx, dy = t.clientY - sy; if (Math.max(Math.abs(dx), Math.abs(dy)) > 16) { if (Math.abs(dx) > Math.abs(dy)) moveSel(dx > 0 ? 1 : -1, 0); else moveSel(0, dy > 0 ? 1 : -1); } }
  }, { passive: true });
  function reset() { initPieces(); sel = null; over = false; moves = 0; secs = 0; movesEl.textContent = '0'; timeEl.textContent = '0'; if (timer) clearInterval(timer); timer = setInterval(() => { if (!over) { secs++; timeEl.textContent = secs; } }, 1000); overlay.classList.add('hidden'); }
  document.getElementById('new').addEventListener('click', reset);
  document.getElementById('ov-btn').addEventListener('click', reset);
  function loop() { draw(); requestAnimationFrame(loop); }
  reset(); requestAnimationFrame(loop);
})();
