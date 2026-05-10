<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🌟 Akademia Ułamków PRO 🌟</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;900&family=Pacifico&display=swap" rel="stylesheet">
<style>
  :root {
    --pink: #FF6EB4; --purple: #C77DFF; --mint: #7DE8D5; 
    --yellow: #FFE566; --coral: #FF8C69; --dark: #3D2B56;
    --light-purple: #E5BAFF; --card-bg: rgba(255,255,255,0.95);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'Nunito', sans-serif; min-height: 100vh;
    background: linear-gradient(135deg, #FFD6F0 0%, #E8C8FF 35%, #C8E8FF 70%);
    background-attachment: fixed; color: var(--dark);
  }

  .nav-tabs {
    display: flex; justify-content: center; background: white; padding: 10px; gap: 10px; flex-wrap: wrap;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  }
  .tab-btn {
    padding: 12px 20px; border: none; background: #f0f0f0; border-radius: 12px;
    cursor: pointer; font-weight: 800; font-family: 'Nunito'; transition: 0.3s; font-size: 1rem;
  }
  .tab-btn.active { background: var(--purple); color: white; transform: translateY(-2px); }

  header { text-align: center; padding: 1rem 1rem 0.5rem; }
  .logo { font-family: 'Pacifico', cursive; font-size: 2.2rem; color: var(--dark); text-shadow: 2px 2px 0 var(--pink); }

  .game-container { max-width: 850px; margin: 0 auto; padding: 1rem; }

  .progress-wrap { background: rgba(255,255,255,0.6); border-radius: 10px; height: 14px; margin-bottom: 15px; overflow: hidden; border: 2px solid white; }
  .progress-fill { height: 100%; background: linear-gradient(90deg, var(--pink), var(--purple)); transition: width 0.4s ease; border-radius: 10px; }

  .level-selector { display: flex; gap: 10px; justify-content: center; margin-bottom: 1rem; }
  .lvl-btn { padding: 8px 15px; border-radius: 10px; border: 2px solid var(--purple); background: white; cursor: pointer; font-weight: 700; transition: 0.2s; }
  .lvl-btn.active { background: var(--purple); color: white; }

  .card { background: var(--card-bg); border-radius: 24px; padding: 2rem; box-shadow: 0 10px 25px rgba(0,0,0,0.08); border: 3px solid white; text-align: center; }

  .fraction-row { display: flex; align-items: center; justify-content: center; gap: 1.5rem; flex-wrap: wrap; margin: 1.5rem 0; }
  .fraction-box { display: flex; flex-direction: column; align-items: center; min-width: 50px; }
  .num, .den { font-size: 2.5rem; font-weight: 900; line-height: 1; }
  .num { color: var(--pink); } .den { color: var(--purple); }
  .line { width: 100%; height: 5px; background: var(--dark); margin: 6px 0; border-radius: 3px; min-width: 50px; }
  
  .mixed-frac { display: flex; align-items: center; gap: 8px; }
  .whole-num { font-size: 3.5rem; font-weight: 900; color: var(--dark); }
  
  .symbol-box { width: 70px; height: 70px; border-radius: 50%; border: 3px dashed var(--purple); display: flex; align-items: center; justify-content: center; font-size: 2rem; font-weight: 900; background: rgba(255,255,255,0.5); }

  .options-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; margin-top: 1.5rem; }
  .opt-btn { padding: 15px; background: white; border: 2px solid var(--light-purple); border-radius: 15px; cursor: pointer; font-size: 1.5rem; font-weight: 800; transition: 0.2s; }
  .opt-btn:hover { background: var(--light-purple); transform: scale(1.02); }

  /* INPUT AREA - NAPRAWIONE DOMYŚLNE WARTOŚCI */
  .input-area { display: flex; justify-content: center; align-items: center; gap: 15px; margin-top: 1.5rem; background: rgba(229,186,255,0.2); padding: 20px; border-radius: 20px; border: 2px dashed var(--purple); flex-wrap: wrap; }
  .in-num, .in-den, .in-whole { text-align: center; font-weight: 900; border: 3px solid var(--light-purple); border-radius: 12px; outline: none; font-family: 'Nunito'; background: white; transition: 0.2s; }
  .in-num:focus, .in-den:focus, .in-whole:focus { border-color: var(--pink); box-shadow: 0 0 10px rgba(255,110,180,0.3); }
  .in-whole { width: 80px; height: 80px; font-size: 2.2rem; color: var(--dark); }
  .in-num, .in-den { width: 70px; height: 50px; font-size: 1.8rem; }
  .frac-input-col { display: flex; flex-direction: column; align-items: center; gap: 6px; }
  
  .check-btn { background: var(--mint); color: var(--dark); padding: 15px 30px; font-size: 1.2rem; border: none; border-radius: 15px; font-weight: 900; cursor: pointer; transition: 0.2s; box-shadow: 0 4px 10px rgba(125,232,213,0.4); }

  .compare-btns { display: flex; justify-content: center; gap: 15px; }
  .comp-btn { width: 75px; height: 75px; border-radius: 50%; border: none; font-size: 2.2rem; color: white; font-weight: 900; cursor: pointer; transition: 0.2s; }

  .hint-trigger-btn { background: var(--yellow); border: none; padding: 10px 20px; border-radius: 20px; font-weight: 800; cursor: pointer; margin-bottom: 10px; font-family: 'Nunito'; }

  .status-bar { display: flex; justify-content: space-between; margin-bottom: 5px; font-weight: 900; }
  .next-btn { margin-top: 1.5rem; padding: 12px 30px; border-radius: 50px; border: none; background: linear-gradient(135deg, var(--pink), var(--purple)); color: white; font-weight: 900; cursor: pointer; }

  .op-symbol { font-size: 3rem; font-weight: 900; color: var(--dark); margin: 0 10px; }
</style>
</head>
<body>

<div class="nav-tabs">
  <button class="tab-btn active" onclick="switchMode('compare')">⚖️ Porównywanie</button>
  <button class="tab-btn" onclick="switchMode('addsub')">➕➖ Dodawanie</button>
  <button class="tab-btn" onclick="switchMode('multdiv')">✖️➗ Mnożenie</button>
</div>

<header>
  <div class="logo">🌟 Akademia Ułamków 🌟</div>
</header>

<div class="game-container">
  <div class="status-bar">
    <div id="scoreLabel">⭐ Punkty: 0</div>
    <div id="qCountLabel">Zadanie: 1/10</div>
    <div id="livesLabel">❤️❤️❤️</div>
  </div>
  
  <div class="progress-wrap">
    <div class="progress-fill" id="progressBar" style="width: 0%"></div>
  </div>

  <div id="gameContent"></div>
</div>

<script>
let mode = 'compare';
let difficulty = 1;
let score = 0;
let lives = 3;
let questionNum = 1;
const totalQuestions = 10;
let currentQ = null;
let answered = false;
let hintStage = 0;

function gcd(a, b) { return b === 0 ? a : gcd(b, a % b); }
function simplify(n, d) { 
  if(d < 0) { n = -n; d = -d; }
  const g = gcd(Math.abs(n), d); 
  return [n/g, d/g]; 
}

const DECIMALS = [
  {v: 0.5, text: '0,5', n: 1, d: 2}, {v: 0.25, text: '0,25', n: 1, d: 4},
  {v: 0.75, text: '0,75', n: 3, d: 4}, {v: 0.2, text: '0,2', n: 1, d: 5},
  {v: 0.4, text: '0,4', n: 2, d: 5}, {v: 0.1, text: '0,1', n: 1, d: 10}
];

function getRandomOperand(maxD) {
  const r = Math.random();
  if (r < 0.2) { 
    const dec = DECIMALS[Math.floor(Math.random()*DECIMALS.length)];
    return { val: dec.v, n: dec.n, d: dec.d, html: `<div class="whole-num">${dec.text}</div>` };
  } else if (r < 0.45) { 
    const w = 1 + Math.floor(Math.random()*2);
    const d = 2 + Math.floor(Math.random()*(maxD-1));
    const num = 1 + Math.floor(Math.random()*(d-1));
    return { 
      val: w + (num/d), n: (w*d)+num, d: d, 
      html: `<div class="mixed-frac"><div class="whole-num">${w}</div><div class="fraction-box"><div class="num">${num}</div><div class="line"></div><div class="den">${d}</div></div></div>` 
    };
  } else { 
    const d = 2 + Math.floor(Math.random()*(maxD-1));
    let maxNum = Math.random() < 0.3 ? d*2 : d-1;
    if (maxNum < 1) maxNum = 1;
    const num = 1 + Math.floor(Math.random()*maxNum);
    return { 
      val: num/d, n: num, d: d, 
      html: `<div class="fraction-box"><div class="num">${num}</div><div class="line"></div><div class="den">${d}</div></div>` 
    };
  }
}

function switchMode(m) {
  mode = m; questionNum = 1;
  document.querySelectorAll('.tab-btn').forEach(b => {
    b.classList.toggle('active', b.innerText.toLowerCase().includes(m.substring(0,3)));
  });
  resetGame(true);
}

function resetGame(keepScore = false) {
  if(!keepScore) score = 0; 
  lives = 3; questionNum = 1;
  nextQuestion();
}

function updateStatus() {
  document.getElementById('scoreLabel').innerText = `⭐ Punkty: ${score}`;
  document.getElementById('livesLabel').innerText = '❤️'.repeat(lives);
  document.getElementById('qCountLabel').innerText = `Zadanie: ${Math.min(questionNum, totalQuestions)}/${totalQuestions}`;
  document.getElementById('progressBar').style.width = `${((questionNum-1)/totalQuestions)*100}%`;
}

function nextQuestion() {
  if (lives <= 0 || questionNum > totalQuestions) { render(); return; }
  answered = false; hintStage = 0;
  const maxD = (score < 50) ? 10 : (score < 120) ? 25 : 100;
  
  if (mode === 'compare') generateCompare(maxD);
  else if (mode === 'addsub') generateAddSub(maxD);
  else generateMultDiv(maxD);
  
  updateStatus();
  render();
}

function generateCompare(maxD) {
  const op1 = getRandomOperand(maxD);
  let op2 = getRandomOperand(maxD);
  if(Math.random() < 0.1) op2 = op1;
  currentQ = { op1, op2, correct: op1.val < op2.val ? '<' : op1.val > op2.val ? '>' : '=' };
}

function generateAddSub(maxD) {
  let op1 = getRandomOperand(maxD);
  let op2 = getRandomOperand(maxD);
  let opType = Math.random() > 0.5 ? '+' : '-';
  if (opType === '-' && op1.val < op2.val) [op1, op2] = [op2, op1];
  let resN = (opType === '+') ? (op1.n*op2.d + op2.n*op1.d) : (op1.n*op2.d - op2.n*op1.d);
  let resD = op1.d*op2.d;
  const [sN, sD] = simplify(resN, resD);
  currentQ = { op1, op2, operator: opType, resN: sN, resD: sD, resVal: sN/sD };
  generateOptions();
}

function generateMultDiv(maxD) {
  let op1 = getRandomOperand(maxD);
  let op2 = getRandomOperand(maxD);
  let opType = Math.random() > 0.5 ? '×' : '÷';
  let resN = (opType === '×') ? (op1.n*op2.n) : (op1.n*op2.d);
  let resD = (opType === '×') ? (op1.d*op2.d) : (op1.d*op2.n);
  const [sN, sD] = simplify(resN, resD);
  currentQ = { op1, op2, operator: opType, resN: sN, resD: sD, resVal: sN/sD };
  generateOptions();
}

function generateOptions() {
  const format = (n, d) => {
    if (n % d === 0) return `${n/d}`;
    if (n > d) return `${Math.floor(n/d)} ${n%d}/${d}`;
    return `${n}/${d}`;
  };
  let correct = format(currentQ.resN, currentQ.resD);
  let opts = [correct];
  while(opts.length < 4) {
    let fN = currentQ.resN + Math.floor(Math.random()*5-2);
    let fD = currentQ.resD + Math.floor(Math.random()*5-2);
    if(fN < 1) fN = 1; if(fD < 2) fD = 2;
    let s = format(fN, fD);
    if(!opts.includes(s)) opts.push(s);
  }
  currentQ.options = opts.sort(() => Math.random() - 0.5);
  currentQ.correctOpt = correct;
}

function render() {
  const container = document.getElementById('gameContent');
  if (lives <= 0 || questionNum > totalQuestions) {
    document.getElementById('progressBar').style.width = `100%`;
    container.innerHTML = `<div class="card"><h2>Koniec! 🏆</h2><p>Punkty: ${score}</p><button class="next-btn" onclick="resetGame(false)">Jeszcze raz</button></div>`;
    return;
  }

  let html = `<div class="level-selector">
    <button class="lvl-btn ${difficulty===1?'active':''}" onclick="setDiff(1)">Łatwy</button>
    <button class="lvl-btn ${difficulty===2?'active':''}" onclick="setDiff(2)">Trudny</button>
  </div><div class="card">`;

  if (mode === 'compare') html += renderCompareUI();
  else html += renderOpsUI();

  html += `<div id="feedback" style="margin-top:20px; font-weight:900; min-height:30px;"></div></div>`;
  container.innerHTML = html;
}

function renderCompareUI() {
  const { op1, op2 } = currentQ;
  return `
    <div class="fraction-row">
      <div>${op1.html}</div>
      <div class="symbol-box" id="symBox">?</div>
      <div>${op2.html}</div>
    </div>
    <div class="compare-btns">
      <button class="comp-btn" style="background:var(--coral)" onclick="checkComp('<')">&lt;</button>
      <button class="comp-btn" style="background:var(--yellow); color:var(--dark)" onclick="checkComp('=')">=</button>
      <button class="comp-btn" style="background:var(--mint); color:var(--dark)" onclick="checkComp('>')">&gt;</button>
    </div>`;
}

function renderOpsUI() {
  const { op1, op2, operator, options } = currentQ;
  let html = `<div class="fraction-row">${op1.html}<div class="op-symbol">${operator}</div>${op2.html}<div class="op-symbol">=</div><div class="symbol-box">?</div></div>`;

  if (difficulty === 1) {
    html += `<div class="options-grid">${options.map(o => `<button class="opt-btn" onclick="checkOp('${o}')">${o}</button>`).join('')}</div>`;
  } else {
    // NAPRAWIONE: value="0" dla całości i licznika, pusty placeholder dla mianownika
    html += `
      <div class="input-area">
        <input type="number" id="inW" class="in-whole" value="0">
        <div class="frac-input-col">
          <input type="number" id="inN" class="in-num" value="0">
          <div class="line"></div>
          <input type="number" id="inD" class="in-den" placeholder="Mianownik">
        </div>
        <button class="check-btn" onclick="checkInputOp()">Sprawdź!</button>
      </div>`;
  }
  return html;
}

function setDiff(d) { difficulty = d; render(); }

function checkComp(val) {
  if (answered) return; answered = true;
  document.getElementById('symBox').innerText = val;
  finishTurn(val === currentQ.correct);
}

function checkOp(val) {
  if (answered) return; answered = true;
  finishTurn(val === currentQ.correctOpt);
}

function checkInputOp() {
  if (answered) return;
  const w = parseFloat(document.getElementById('inW').value) || 0;
  const n = parseFloat(document.getElementById('inN').value) || 0;
  const d = parseFloat(document.getElementById('inD').value) || 1; 

  if (d === 0) { alert('Mianownik nie może być zerem!'); return; }
  const userVal = w + (n/d);
  answered = true;
  finishTurn(Math.abs(userVal - currentQ.resVal) < 0.001);
}

function finishTurn(isCorrect) {
  const fb = document.getElementById('feedback');
  if (isCorrect) {
    score += (difficulty * 10);
    fb.innerHTML = "✅ SUPER!"; fb.style.color = "green";
  } else {
    lives--;
    fb.innerHTML = `❌ Wynik: ${currentQ.correctOpt || currentQ.correct}`; 
    fb.style.color = "red";
  }
  questionNum++;
  updateStatus();
  const btn = document.createElement('button');
  btn.className = 'next-btn';
  btn.innerText = "Dalej →";
  btn.onclick = nextQuestion;
  document.querySelector('.card').appendChild(btn);
}

nextQuestion();
</script>
</body>
</html>
