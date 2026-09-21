[index.html](https://github.com/user-attachments/files/32480776/index.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>دعوة خطوبة | أدهم وإسراء</title>
  
  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Aref+Ruqaa:wght@400;700&family=Tajawal:wght@300;400;500;700&family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
  
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <!-- Canvas Confetti Library -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <style>
    :root {
      --bg-main: #f5ede4;
      --accent-gold: #c6a366;
      --accent-gold-light: #f8f3eb;
      --accent-burgundy: #5c1d28;
      --accent-burgundy-dark: #3a0d15;
      --text-main: #3a2e2b;
      --text-muted: #6e5f5d;
      --border-gold: rgba(198, 163, 102, 0.35);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      -webkit-text-size-adjust: 100%;
      text-size-adjust: 100%;
    }

    body {
      font-family: 'Tajawal', serif;
      background-color: #12090b;
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow-x: hidden;
      overflow-wrap: break-word;
      word-wrap: break-word;
    }

    .app-container {
      width: 100%;
      max-width: 450px;
      min-height: 100vh;
      background: var(--bg-main);
      position: relative;
      box-shadow: 0 15px 35px rgba(0,0,0,0.4);
      overflow-y: auto;
      overflow-x: hidden;
    }

    /* شاشة الكرت */
    #card-screen {
      position: fixed;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 100%;
      max-width: 450px;
      height: 100vh;
      background: #12090b;
      z-index: 100;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      transition: transform 0.9s cubic-bezier(0.77, 0, 0.175, 1), opacity 0.7s ease;
      overflow: hidden;
      cursor: pointer;
      padding: 20px;
    }

    #card-screen.opened {
      transform: translate(-50%, -100%);
      opacity: 0;
      pointer-events: none;
    }

    .card-image-wrapper {
      position: relative;
      width: 100%;
      max-width: 380px;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 20px 40px rgba(0,0,0,0.6);
      transition: transform 0.3s ease;
    }

    .card-image-wrapper:hover {
      transform: scale(1.02);
    }

    .card-image {
      width: 100%;
      height: auto;
      display: block;
      object-fit: cover;
    }

    .click-hint {
      position: absolute;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0, 0, 0, 0.65);
      color: #fff;
      padding: 8px 16px;
      border-radius: 20px;
      font-size: clamp(11px, 3.2vw, 13px);
      backdrop-filter: blur(4px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      white-space: nowrap;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 0.8; transform: translateX(-50%) scale(1); }
      50% { opacity: 1; transform: translateX(-50%) scale(1.05); }
    }

    .music-btn {
      position: fixed;
      bottom: 20px;
      left: 20px;
      width: 45px;
      height: 45px;
      border-radius: 50%;
      background: var(--accent-burgundy);
      color: #ffffff;
      border: 1px solid var(--accent-gold);
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 18px;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(0,0,0,0.25);
      z-index: 90;
      transition: transform 0.2s ease, opacity 0.2s ease;
    }

    .music-btn:active {
      transform: scale(0.92);
    }

    .content-wrapper {
      padding: 16px 16px 40px 16px;
      position: relative;
      z-index: 1;
      text-align: center;
    }

    .hero-frame-container {
      position: relative;
      width: 100%;
      border-radius: 20px;
      overflow: hidden;
      margin-bottom: 25px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
      background: #fff;
    }

    .hero-frame-img {
      width: 100%;
      height: auto;
      display: block;
    }

    .hero-frame-content {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 10% 6% 22% 6%;
      text-align: center;
      z-index: 2;
    }

    .bismillah {
      font-family: 'Amiri', serif;
      font-size: clamp(16px, 4.8vw, 21px);
      color: var(--accent-burgundy);
      margin-bottom: 8px;
      font-weight: 700;
    }

    .event-type-badge {
      display: inline-block;
      font-family: 'Aref Ruqaa', serif;
      font-size: clamp(15px, 4.3vw, 19px);
      color: var(--accent-burgundy);
      border-bottom: 1px dashed var(--accent-gold);
      padding-bottom: 2px;
      margin-bottom: 10px;
    }

    .invitation-quote {
      font-family: 'Amiri', serif;
      font-size: clamp(13px, 3.8vw, 17px);
      line-height: 1.6;
      color: #3d2429;
      margin: 4px 0 12px 0;
      font-weight: 600;
    }

    .couple-names-box {
      margin-top: 2px;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 8px;
      flex-wrap: wrap;
    }

    .couple-name {
      font-family: 'Aref Ruqaa', serif;
      font-size: clamp(26px, 7.5vw, 38px);
      font-weight: 700;
      color: var(--accent-burgundy);
      line-height: 1.2;
    }

    .couple-ampersand {
      font-family: 'Amiri', serif;
      font-size: clamp(18px, 5.5vw, 26px);
      color: var(--accent-gold);
    }

    /* أقسام الكروت */
    .section-card {
      background-color: transparent;
      border: none;
      border-radius: 0;
      padding: 35px 20px;
      margin-bottom: 25px;
      box-shadow: none;
      position: relative;
      background-size: 100% 100%;
      background-repeat: no-repeat;
      background-position: center;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    .paper-type-1 {
      background-image: url('p3.png');
    }

    .paper-type-2 {
      background-image: url('p4.png');
    }

    .section-title {
      font-family: 'Aref Ruqaa', serif;
      font-size: clamp(18px, 5.2vw, 23px);
      color: var(--accent-burgundy);
      margin-bottom: 12px;
      display: inline-block;
    }

    .event-date-box {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
    }

    .date-day {
      font-family: 'Aref Ruqaa', serif;
      font-size: clamp(17px, 5vw, 23px);
      color: var(--accent-burgundy);
      font-weight: bold;
    }

    .date-time {
      font-size: clamp(13px, 3.5vw, 15px);
      color: var(--text-muted);
      font-weight: 600;
    }

    .countdown-container {
      display: flex;
      justify-content: center;
      gap: 6px;
      margin-top: 8px;
      direction: ltr;
      width: 100%;
    }

    .time-block {
      background: rgba(255, 255, 255, 0.65);
      border: 1px solid rgba(198, 163, 102, 0.4);
      border-radius: 8px;
      padding: 6px 4px;
      flex: 1;
      max-width: 65px;
      backdrop-filter: blur(2px);
    }

    .time-number {
      font-size: clamp(15px, 4.5vw, 19px);
      font-weight: 700;
      color: var(--accent-burgundy);
      display: block;
    }

    .time-label {
      font-size: clamp(9px, 2.8vw, 11px);
      color: var(--text-muted);
      display: block;
    }

    .location-name {
      font-size: clamp(14px, 4vw, 17px);
      font-weight: 700;
      color: var(--accent-burgundy);
      margin-bottom: 4px;
    }

    .location-address {
      font-size: clamp(12px, 3.2vw, 13px);
      color: var(--text-muted);
      margin-bottom: 14px;
    }

    .map-preview-btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(255, 255, 255, 0.8);
      border: 1px solid var(--accent-gold);
      color: var(--text-main);
      padding: 8px 18px;
      border-radius: 25px;
      text-decoration: none;
      font-size: clamp(12px, 3.2vw, 13px);
      font-weight: 600;
      transition: background 0.3s ease;
    }

    .map-preview-btn:hover {
      background: #ffffff;
    }

    .congratulations-form {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 10px;
      width: 100%;
      max-width: 320px;
    }

    .congrats-input, .congrats-textarea {
      width: 100%;
      padding: 10px 12px;
      border: 1px solid rgba(198, 163, 102, 0.5);
      border-radius: 10px;
      font-family: 'Tajawal', sans-serif;
      font-size: clamp(13px, 3.5vw, 14px);
      background: rgba(255, 255, 255, 0.85);
      color: var(--text-main);
      outline: none;
      transition: border-color 0.3s, background-color 0.3s;
    }

    .congrats-input:focus, .congrats-textarea:focus {
      border-color: var(--accent-burgundy);
      background: #ffffff;
    }

    .congrats-textarea {
      resize: vertical;
      min-height: 80px;
    }

    .submit-congrats-btn {
      background: linear-gradient(135deg, var(--accent-burgundy), var(--accent-burgundy-dark));
      color: #ffffff;
      border: none;
      padding: 10px;
      border-radius: 25px;
      font-family: 'Tajawal', sans-serif;
      font-size: clamp(13px, 3.8vw, 15px);
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 6px 18px rgba(74, 24, 32, 0.25);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      transition: opacity 0.2s ease, transform 0.2s ease;
    }

    .submit-congrats-btn:hover {
      opacity: 0.95;
    }

    .submit-congrats-btn:active {
      transform: scale(0.98);
    }

    .footer-note {
      font-family: 'Amiri', serif;
      font-size: clamp(15px, 4.5vw, 19px);
      color: var(--accent-burgundy);
      margin-top: 10px;
      margin-bottom: 25px;
      font-weight: bold;
    }

    .made-in-love {
      display: block;
      margin-top: 14px;
      font-family: 'Montserrat', sans-serif;
      font-size: clamp(10px, 3vw, 12px);
      font-weight: 500;
      color: var(--text-muted);
      letter-spacing: 1px;
      direction: ltr;
    }

    .made-in-love .names {
      font-weight: 700;
      color: var(--accent-burgundy);
      letter-spacing: 0.5px;
    }

    .made-in-love .heart {
      color: #c0392b;
      display: inline-block;
      margin: 0 2px;
    }

    @media (max-width: 360px) {
      .content-wrapper {
        padding: 10px 10px 30px 10px;
      }
      .section-card {
        padding: 28px 14px;
      }
    }
  </style>
</head>
<body>

  <!-- صوت خلفية -->
  <audio id="wedding-music" loop preload="auto">
    <source src="music.mpeg" type="audio/mpeg">
  </audio>

  <!-- زر الموسيقى -->
  <button id="music-toggle-btn" class="music-btn" title="تشغيل / إيقاف الموسيقى">
    <i class="fa-solid fa-music" id="music-icon"></i>
  </button>

  <div class="app-container">

    <!-- شاشة صورة الكرت -->
    <div id="card-screen">
      <div class="card-image-wrapper">
        <img src="p.jpg" alt="كرت الدعوة" class="card-image">
        <div class="click-hint">
          <i class="fa-solid fa-hand-pointer"></i> اضغط هنا لفتح الدعوة
        </div>
      </div>
    </div>

    <!-- المحتوى الرئيسي -->
    <div class="content-wrapper">

      <!-- بطاقة الصورة الرئيسية -->
      <div class="hero-frame-container">
        <img src="p2.jpg" alt="إطار الدعوة" class="hero-frame-img">

        <div class="hero-frame-content">
          <div class="bismillah">بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيمِ</div>
          <div class="event-type-badge">دعوة حفل خطوبة</div>

          <p class="invitation-quote">
            كان حلمًا، فأصبح موعدًا…<br>
            وكان دعاءً، فأصبح نصيبًا 🤍
          </p>

          <div class="couple-names-box">
            <span class="couple-name">أدهم</span>
            <span class="couple-ampersand">&</span>
            <span class="couple-name">إسراء</span>
          </div>
        </div>
      </div>

      <!-- موعد الحفل -->
      <div class="section-card paper-type-1">
        <div class="section-title">موعد الحفل</div>
        <div class="event-date-box">
          <div class="date-day">السبت، 24 أكتوبر 2026</div>
          <div class="date-time">
            <i class="fa-regular fa-clock" style="color: var(--accent-gold);"></i>
            الساعة 6:00 مساءً
          </div>
        </div>
      </div>

      <!-- العداد التنازلي -->
      <div class="section-card paper-type-2">
        <div class="section-title">يبدأ العد التنازلي</div>
        <div class="countdown-container">
          <div class="time-block">
            <span class="time-number" id="seconds">00</span>
            <span class="time-label">ثانية</span>
          </div>
          <div class="time-block">
            <span class="time-number" id="minutes">00</span>
            <span class="time-label">دقيقة</span>
          </div>
          <div class="time-block">
            <span class="time-number" id="hours">00</span>
            <span class="time-label">ساعة</span>
          </div>
          <div class="time-block">
            <span class="time-number" id="days">00</span>
            <span class="time-label">يوم</span>
          </div>
        </div>
      </div>

      <!-- موقع الحفل -->
      <div class="section-card paper-type-1">
        <div class="section-title">موقع الحفل</div>
        <div class="location-name">قاعة المناسبات السعيدة</div>
        <div class="location-address">اسم الشارع، المدينة</div>
        <a href="https://maps.google.com" target="_blank" rel="noopener noreferrer" class="map-preview-btn">
          <i class="fa-solid fa-location-dot" style="color: var(--accent-burgundy);"></i>
          فتح في خرائط جوجل
        </a>
      </div>

      <!-- قسم تهنئة العرسان -->
      <div class="section-card paper-type-2">
        <div class="section-title">اتركلنا أثر بكلمه حلوة ✍️</div>
        <p style="font-size: clamp(11px, 3.2vw, 13px); color: var(--text-muted); margin-bottom: 12px;">
          قبل أن نبدأ فصلنا الجديد 
          اتركوا لنا منكم كلمةً نحتفظ بها للأبد 🤍
        </p>
        
        <form class="congratulations-form" id="congrats-form">
          <input type="text" name="name" class="congrats-input" placeholder="الاسم" required>
          <textarea name="message" class="congrats-textarea" placeholder="اكتب تهنئتك هنا..." required></textarea>
          <button type="submit" class="submit-congrats-btn">
            <i class="fa-solid fa-paper-plane"></i>
            إرسال التهنئة
          </button>
        </form>
      </div>

      <div class="footer-note">
        ننتظركم بشوق لتكتمل فرحتنا بكُم ...<br>
        <span class="made-in-love">
          <small>Made in love for</small> <span class="names"><small>Adham & Esraa</small></span>
        </span>
      </div>

    </div>

  </div>

  <script>
    const GOOGLE_SHEETS_URL = 'https://script.google.com/macros/s/AKfycbwWdzMkZGgMkaLahfcV_hFZbQQKIZGV6VTxpOoAIlvHlnpp_tNkM7jGAL7z-B3sn0rQTw/exec';

    const cardScreen = document.getElementById('card-screen');
    const bgMusic = document.getElementById('wedding-music');
    const musicBtn = document.getElementById('music-toggle-btn');
    const musicIcon = document.getElementById('music-icon');

    function triggerConfetti() {
      if (typeof confetti === 'function') {
        const count = 200;
        const defaults = {
          origin: { y: 0.7 },
          colors: ['#c6a366', '#f8f3eb', '#5c1d28', '#ffffff']
        };

        function fire(particleRatio, opts) {
          confetti({ ...defaults, ...opts, particleCount: Math.floor(count * particleRatio) });
        }

        fire(0.25, { spread: 26, startVelocity: 55 });
        fire(0.2, { spread: 60 });
        fire(0.35, { spread: 100, decay: 0.91, scalar: 0.8 });
        fire(0.1, { spread: 120, startVelocity: 25, decay: 0.92, scalar: 1.2 });
        fire(0.1, { spread: 120, startVelocity: 45 });
      }
    }

    cardScreen.addEventListener('click', () => {
      cardScreen.classList.add('opened');
      triggerConfetti();

      if (bgMusic) {
        // تحديد لبدء الأغنية من الثانية 27
        bgMusic.currentTime = 27;
        bgMusic.play().then(() => {
          musicIcon.className = "fa-solid fa-music";
          musicBtn.style.opacity = '1';
        }).catch(err => {
          console.log("Audio autoplay prevented:", err);
          musicIcon.className = "fa-solid fa-volume-xmark";
          musicBtn.style.opacity = '0.6';
        });
      }
    });

    musicBtn.addEventListener('click', () => {
      if (bgMusic.paused) {
        // إذا كانت الأغنية متوقفة تماماً أو في البداية، ابدأ من الثانية 27
        if (bgMusic.currentTime < 27) {
          bgMusic.currentTime = 27;
        }
        bgMusic.play().then(() => {
          musicIcon.className = "fa-solid fa-music";
          musicBtn.style.opacity = '1';
        }).catch(err => console.error(err));
      } else {
        bgMusic.pause();
        musicIcon.className = "fa-solid fa-volume-xmark";
        musicBtn.style.opacity = '0.6';
      }
    });

    const targetDate = new Date('2026-10-24T18:00:00');

    function updateCountdown() {
      const now = new Date().getTime();
      const difference = targetDate.getTime() - now;

      if (difference > 0) {
        document.getElementById('days').innerText = String(Math.floor(difference / (1000 * 60 * 60 * 24))).padStart(2, '0');
        document.getElementById('hours').innerText = String(Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))).padStart(2, '0');
        document.getElementById('minutes').innerText = String(Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60))).padStart(2, '0');
        document.getElementById('seconds').innerText = String(Math.floor((difference % (1000 * 60)) / 1000)).padStart(2, '0');
      } else {
        document.getElementById('days').innerText = '00';
        document.getElementById('hours').innerText = '00';
        document.getElementById('minutes').innerText = '00';
        document.getElementById('seconds').innerText = '00';
      }
    }
    setInterval(updateCountdown, 1000);
    updateCountdown();

    document.getElementById('congrats-form').addEventListener('submit', function(e) {
      e.preventDefault();

      const nameInput = this.querySelector('[name="name"]');
      const messageInput = this.querySelector('[name="message"]');
      const submitBtn = this.querySelector('.submit-congrats-btn');

      const name = nameInput.value.trim();
      const message = messageInput.value.trim();

      if (!name || !message) return;

      submitBtn.disabled = true;
      submitBtn.innerHTML = '<i class="fa-solid fa-spinner fa-spin"></i> جاري الإرسال...';

      fetch(GOOGLE_SHEETS_URL, {
        method: 'POST',
        mode: 'no-cors',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ name: name, message: message })
      })
      .then(() => {
        alert('وصلت تهنئتك المعطرة، شكراً لك لمشاركتك ! 🤍');
        this.reset();
      })
      .catch(error => {
        alert('حدث خطأ أثناء الإرسال، يرجى المحاولة مرة أخرى.');
        console.error('Error submitting form:', error);
      })
      .finally(() => {
        submitBtn.disabled = false;
        submitBtn.innerHTML = '<i class="fa-solid fa-paper-plane"></i> إرسال التهنئة';
      });
    });
  </script>
</body>
</html>
