<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Dream Journey - Deep Analyzer</title>
<style>
body{
  margin:0;
  font-family:Arial, Helvetica, sans-serif;
  background:#060816;
  color:white;
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  padding:20px;
}
.card{
  width:100%;
  max-width:820px;
  background:rgba(255,255,255,0.08);
  border:1px solid rgba(255,255,255,0.14);
  border-radius:26px;
  padding:28px;
  backdrop-filter: blur(14px);
  box-shadow:0 0 40px rgba(124,77,255,.25);
}
h1{
  text-align:center;
  margin-top:0;
  font-size:2.3rem;
}
textarea{
  width:100%;
  min-height:140px;
  border:none;
  border-radius:18px;
  padding:16px;
  font-size:1rem;
  box-sizing:border-box;
  resize:vertical;
  background:rgba(255,255,255,.95);
}
button{
  width:100%;
  margin-top:16px;
  border:none;
  border-radius:16px;
  padding:16px;
  font-size:1rem;
  font-weight:bold;
  cursor:pointer;
  background:linear-gradient(90deg,#7c4dff,#00d4ff);
  color:white;
}
.grid{
  display:grid;
  gap:16px;
  margin-top:22px;
}
.box{
  background:rgba(255,255,255,0.05);
  border-radius:18px;
  padding:18px;
  line-height:1.7;
}
.box h3{
  margin-top:0;
}
.footer{
  text-align:center;
  opacity:.7;
  margin-top:16px;
}
</style>
</head>
<body>
<div class="card">
  <h1>🧠 AI Dream Journey</h1>
  <p>Write down your dream, and the AI will provide <b>psychological analysis, detected emotions, potential triggers, and advice</b>.</p>

  <textarea id="dream" placeholder="Example: I dreamed I was being chased by a monster in a dark alley, then I fell and couldn't run..."></textarea>
  <button onclick="analyze()">🔮 Deep Analysis</button>

  <div class="grid">
    <div class="box"><h3>🌙 General Meaning</h3><div id="meaning">Not analyzed yet.</div></div>
    <div class="box"><h3>❤️ Detected Emotions</h3><div id="emotion">Not analyzed yet.</div></div>
    <div class="box"><h3>⚠️ Possible Triggers</h3><div id="trigger">Not analyzed yet.</div></div>
    <div class="box"><h3>💡 AI Advice</h3><div id="advice">Not analyzed yet.</div></div>
  </div>

  <div class="footer"><a href="https://www.google.com" style="color:white; text-decoration:none;">Deep Analyzer Version for VS Code + Live Server</a></div>
</div>

<script>
function setResult(m, e, t, a) {
  meaning.textContent = m;
  emotion.textContent = e;
  trigger.textContent = t;
  advice.textContent = a;
}

// Generates a consistent hash value from text
function getHash(str) {
  let hash = 0;
  for (let i = 0; i < str.length; i++) {
    hash = (hash << 5) - hash + str.charCodeAt(i);
    hash |= 0;
  }
  return Math.abs(hash);
}

// Selects array element deterministically based on text hash
function getDeterministicItem(arr, hash, offset = 0) {
  const index = (hash + offset) % arr.length;
  return arr[index];
}

function analyze() {
  const d = dream.value.toLowerCase().trim();

  if (d === "") {
    setResult("Please write down your dream first.", "-", "-", "-");
    return;
  }

  const hash = getHash(d);

  if (d.includes("setan") || d.includes("hantu") || d.includes("dikejar") || d.includes("ghost") || d.includes("monster") || d.includes("chased")) {
    const meanings = [
      "This dream is often a symbol of fear, pressure, or problems you are currently trying to avoid.",
      "Your subconscious mind is processing threats or feelings of pressure from real-life situations.",
      "Indicates unresolved internal conflict that is causing deep anxiety."
    ];
    const emotions = [
      "Scared, anxious, panicked, and feeling threatened.",
      "Restless, tense, and cornered by circumstances.",
      "Excessively worried and hyper-vigilant."
    ];
    const triggers = [
      "Stress, school/work workload, conflicts with others, or watching horror content.",
      "Lack of sleep, physical exhaustion, and an overly active mind before bedtime.",
      "Anxiety about new responsibilities or avoided personal issues."
    ];
    const advices = [
      "Try to relax before sleeping, cut back on horror content, and face the main issue weighing on you.",
      "Practice relaxation or deep breathing exercises before sleep to lower stress levels.",
      "Write down your anxieties in a journal before bed to help clear your mind."
    ];

    setResult(
      getDeterministicItem(meanings, hash, 1),
      getDeterministicItem(emotions, hash, 2),
      getDeterministicItem(triggers, hash, 3),
      getDeterministicItem(advices, hash, 4)
    );
  }
  else if (d.includes("jatuh") || d.includes("fall") || d.includes("falling")) {
    const meanings = [
      "Dreams about falling are often linked to a sense of losing control or fear of failure.",
      "Reflects life uncertainty or insecurity you are currently experiencing.",
      "Indicates disappointment or fear of not meeting expectations."
    ];
    const emotions = [
      "Insecure, worried, and nervous.",
      "Lost, overwhelmed, and anxious.",
      "Sudden panic and feeling vulnerable."
    ];
    const triggers = [
      "Academic/career pressure, sudden life changes, or fear of failure.",
      "Lack of support from your environment or setting unrealistically high personal goals.",
      "Physical fatigue and rapid transitions between sleep cycles."
    ];
    const advices = [
      "Focus on what you can control and avoid being too hard on yourself.",
      "Re-evaluate your targets and take small steps forward slowly.",
      "Trust your abilities and express negative emotions in a healthy way."
    ];

    setResult(
      getDeterministicItem(meanings, hash, 1),
      getDeterministicItem(emotions, hash, 2),
      getDeterministicItem(triggers, hash, 3),
      getDeterministicItem(advices, hash, 4)
    );
  }
  else if (d.includes("ular") || d.includes("snake")) {
    const meanings = [
      "Snakes can symbolize change, alertness, or strong suppressed emotions.",
      "Signifies hidden threats, deception, or a major transformation in your life.",
      "A symbol of self-healing or your intuition trying to send you a warning."
    ];
    const emotions = [
      "Alert, curious, hesitant, or fearful.",
      "Threatened, suspicious, and full of tension.",
      "Torn between holding back or facing a situation."
    ];
    const triggers = [
      "Changes in social relationships, a new environment, or unresolved conflicts.",
      "A lack of trust in someone currently around you.",
      "Adapting to new situations or responsibilities."
    ];
    const advices = [
      "Pay attention to uncomfortable situations and address them gradually.",
      "Trust your instincts and set firm boundaries with others if necessary.",
      "Don't ignore your feelings; communicate issues honestly."
    ];

    setResult(
      getDeterministicItem(meanings, hash, 1),
      getDeterministicItem(emotions, hash, 2),
      getDeterministicItem(triggers, hash, 3),
      getDeterministicItem(advices, hash, 4)
    );
  }
  else if (d.includes("air") || d.includes("banjir") || d.includes("laut") || d.includes("water") || d.includes("flood") || d.includes("sea") || d.includes("ocean")) {
    const meanings = [
      "Water is closely tied to your emotional state and overflowing feelings.",
      "Floods or swift water indicate feeling overwhelmed by current circumstances.",
      "A symbol of emotional cleansing or the need to release mental burdens."
    ];
    const emotions = [
      "Sad, confused, stressed, or overly emotional.",
      "Resigned, anxious, and losing control over your feelings.",
      "Emotionally exhausted and in need of tranquility."
    ];
    const triggers = [
      "Overthinking, personal problems, or accumulated mental fatigue.",
      "Drastic mood swings or emotional conflicts with someone.",
      "Holding in too many emotions without finding an outlet."
    ];
    const advices = [
      "Get enough rest, talk about your feelings with someone you trust, and lighten your mental load.",
      "Give yourself time to release emotions without feeling guilty.",
      "Try stress-relieving activities like listening to music or practicing meditation."
    ];

    setResult(
      getDeterministicItem(meanings, hash, 1),
      getDeterministicItem(emotions, hash, 2),
      getDeterministicItem(triggers, hash, 3),
      getDeterministicItem(advices, hash, 4)
    );
  }
  else {
    const meanings = [
      "This dream is likely a blend of your everyday experiences, thoughts, and emotions.",
      "Your subconscious consolidating memories from recent real-life events.",
      "A reflection of hopes, imagination, or conversations that recently crossed your mind."
    ];
    const emotions = [
      "A mix of emotions active in your brain.",
      "Neutral, curious, or slightly confused.",
      "Varies depending on your mood over the past few days."
    ];
    const triggers = [
      "Pre-bedtime activities, frequently pondered topics, and recent experiences.",
      "Media or information consumed throughout the day.",
      "Daily routine patterns and nighttime comfort levels."
    ];
    const advices = [
      "Try keeping a dream journal to track recurring dream patterns.",
      "Maintain a regular sleep schedule to maximize your sleep quality.",
      "Use this dream as a simple reflection of what you are currently focusing on."
    ];

    setResult(
      getDeterministicItem(meanings, hash, 1),
      getDeterministicItem(emotions, hash, 2),
      getDeterministicItem(triggers, hash, 3),
      getDeterministicItem(advices, hash, 4)
    );
  }
}
</script>
</body>
</html>
