# mew.github.io
[Uploading surprise_website (2).html…]()
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>Surprise 🎉</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      color: #fff;
      text-align: center;
    }
    .card {
      background: rgba(0,0,0,0.25);
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.3);
      animation: pop 1s ease;
    }
    h1 {
      font-size: 3rem;
      margin-bottom: 10px;
    }
    .mascot {
      font-size: 4rem;
      margin-bottom: 10px;
      animation: wiggle 2s infinite;
    }
    .mascot img {
      width: 100%;
      height: auto;
    }
    @keyframes wiggle {
      0% { transform: rotate(0deg); }
      25% { transform: rotate(5deg); }
      50% { transform: rotate(0deg); }
      75% { transform: rotate(-5deg); }
      100% { transform: rotate(0deg); }
    }
    p {
      font-size: 1.3rem;
    }
    button {
      margin-top: 25px;
      padding: 12px 30px;
      border: none;
      border-radius: 30px;
      background: #ff5f6d;
      color: white;
      font-size: 1.1rem;
      cursor: pointer;
      transition: transform 0.2s, background 0.2s;
    }
    button:hover {
      transform: scale(1.1);
      background: #ffc371;
      color: #000;
    }
    .heart {
      position: absolute;
      font-size: 24px;
      animation: float 5s linear infinite;
      opacity: 0.8;
    }
    @keyframes float {
      0% { transform: translateY(100vh) scale(0.5); opacity: 0; }
      50% { opacity: 1; }
      100% { transform: translateY(-10vh) scale(1.2); opacity: 0; }
    }
    @keyframes pop {
      0% { transform: scale(0.5); opacity: 0; }
      60% { transform: scale(1.2); opacity: 1; }
      100% { transform: scale(1); opacity: 1; }
    }
    @keyframes bounce {
      0% { transform: scale(0.3); opacity: 0; }
      50% { transform: scale(1.15); opacity: 1; }
      70% { transform: scale(0.95); }
      100% { transform: scale(1); }
    }
      to { transform: scale(1); opacity: 1; }
    }
  </style>
</head>
<body>
  <div class="card" id="lock">
    <div class="mascot">🐰💕</div>
    <h1>🔒 สำหรับมิ้วคนเดียว</h1>
    <p>กรุณาใส่รหัสผ่านวันครบรอบ 💕</p>
    <input type="password" id="password" placeholder="รหัสผ่าน" style="padding:10px 20px;border-radius:20px;border:none;font-size:1.1rem;text-align:center;" />
    <br />
    <button onclick="checkPassword()">ยืนยัน</button>
    <p id="error" style="color:#ffd1d1;margin-top:15px;"></p>
  </div>

  <div class="card" id="content" style="display:none;">
    <div class="mascot">🐰💕</div>
    <h1>💖 สุขสันต์วันครบรอบ 💖</h1>
    <p style="font-size:1.3rem;">มิ้วรักเรามั้ย 🥺</p>
    <div style="margin-top:20px;">
      <button onclick="loveYes()">รัก 💕</button>
      <button onclick="loveNo()" style="background:#555;margin-left:10px;">ไม่รัก 😢</button>
    </div>
  </div>

  <div class="card" id="noLove" style="display:none;">
    <div class="mascot">🐰💕</div>
    <h1>🥺 ลองคิดใหม่</h1>
    <button onclick="loveYes()" style="font-size:2rem;padding:20px 50px;border-radius:50px;">รัก 💖</button>
  </div>

  <div class="card" id="loveContent" style="display:none;">
    <div class="mascot">🐰💕</div>
    <h1>💘 มีไรจะบอก</h1>
    <button id="showBtn" onclick="showMessage()">ลองกดดูสิ</button>
    <p id="msg" style="margin-top:20px;font-size:1.4rem;"></p>
  </div>

  <script>
    function checkPassword() {
      const pass = document.getElementById('password').value;
      if (pass === '19112568') {
        document.getElementById('lock').style.display = 'none';
        document.getElementById('content').style.display = 'block';
        const v = document.getElementById('anniVideo');
        if (v) { v.play(); }
      } else {
        document.getElementById('error').innerText = 'รหัสผ่านไม่ถูกต้อง 💔';
      }
    }

    function loveYes() {
      document.getElementById('content').style.display = 'none';
      document.getElementById('noLove').style.display = 'none';
      document.getElementById('loveContent').style.display = 'block';
    }

    function loveNo() {
      document.getElementById('content').style.display = 'none';
      document.getElementById('noLove').style.display = 'block';
    }

    function showMessage() {
      const btn = document.getElementById('showBtn');
      btn.disabled = true; // กดได้แค่ครั้งเดียว
      btn.style.opacity = '0.6';
      btn.style.cursor = 'default';

      const messages = [
        "สุขสันต์วันครบรอบ 2 เดือนน่าาา 💕",
        "อยู่กันแบบนี้ไปนานๆน่ะ",
        "ขอโทษที่ชวนรบบ่อยๆ",
        "แล้วก็ รักมากๆน่าาา",
        "รู้ไว้ด้วย ถึงจะไม่ค่อยบอก 💖"
      ];

      const msgBox = document.getElementById('msg');
      msgBox.innerHTML = "";

      let i = 0;
      const interval = setInterval(() => {
        if (i < messages.length) {
          const p = document.createElement('p');
          p.style.margin = '10px 0';
          p.style.animation = 'bounce 0.8s ease';
          p.innerText = messages[i];
          msgBox.appendChild(p);
          i++;
        } else {
          clearInterval(interval);
        }
      }, 2500); // ห่างกัน 2.5 วินาที
    }

    const hearts = ['💖','💘','💕','💗','💝'];
    setInterval(() => {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.innerText = hearts[Math.floor(Math.random()*hearts.length)];
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = 3 + Math.random()*3 + 's';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 400);
  </script>
</body>
</html>
