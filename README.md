<!doctype html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Khozin Asror AI - Asisten Virtual Filsafat & Agama</title>
  <style>
    :root {
      --primary: #6a0dad;
      --secondary: #4b0082;
      --accent: #9c27b0;
      --dark: #121212;
      --text: #e0e0e0;
      --light: #1e1e1e;
      --gray: #333333;
      --success: #4CAF50;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    }

    body {
      background-color: var(--dark);
      color: var(--text);
    }

    /* Welcome Screen */
    .welcome-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background: linear-gradient(135deg, #000428, #004e92);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      animation: fadeOut 2s ease-in-out 3s forwards;
    }

    @keyframes fadeOut {
      to { opacity: 0; visibility: hidden; }
    }

    .welcome-title {
      font-size: 4rem;
      font-weight: 800;
      background: linear-gradient(to right, #00d2ff, #3a7bd5);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 0 20px rgba(0, 210, 255, 0.3);
      margin-bottom: 20px;
      letter-spacing: 2px;
      animation: glow 2s ease-in-out infinite alternate;
    }

    @keyframes glow {
      from { text-shadow: 0 0 10px rgba(0, 210, 255, 0.5); }
      to { text-shadow: 0 0 20px rgba(0, 210, 255, 0.8), 0 0 30px rgba(0, 210, 255, 0.4); }
    }

    .welcome-subtitle {
      font-size: 1.2rem;
      color: rgba(255, 255, 255, 0.8);
      margin-bottom: 40px;
      text-align: center;
      max-width: 600px;
      line-height: 1.6;
    }

    .loading-bar {
      width: 300px;
      height: 4px;
      background: rgba(255, 255, 255, 0.2);
      border-radius: 2px;
      overflow: hidden;
      margin-top: 30px;
    }

    .loading-progress {
      height: 100%;
      width: 0%;
      background: linear-gradient(to right, #00d2ff, #3a7bd5);
      animation: load 3s ease-in-out forwards;
    }

    @keyframes load {
      to { width: 100%; }
    }

    .app-container {
      max-width: 100%;
      margin: 0 auto;
      background-color: var(--dark);
      min-height: 100vh;
      position: relative;
      overflow-x: hidden;
    }

    /* Start Screen */
    .start-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background: linear-gradient(135deg, #1a1a2e, #16213e);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 999;
    }

    .start-title {
      font-size: 3.5rem;
      font-weight: 800;
      background: linear-gradient(to right, #fdc830, #f37335);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 30px;
      text-align: center;
    }

    .start-description {
      font-size: 1.1rem;
      color: rgba(255, 255, 255, 0.8);
      margin-bottom: 40px;
      text-align: center;
      max-width: 600px;
      line-height: 1.6;
      padding: 0 20px;
    }

    .start-button {
      padding: 15px 40px;
      background: linear-gradient(90deg, #f12711, #f5af19);
      color: white;
      border: none;
      border-radius: 50px;
      font-size: 1.2rem;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
    }

    .start-button:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
    }

    /* Login Screen */
    .login-container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      padding: 20px;
      background: linear-gradient(135deg, var(--dark), var(--secondary));
      text-align: center;
    }

    .login-box {
      background-color: var(--light);
      padding: 30px;
      border-radius: 10px;
      width: 100%;
      max-width: 400px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
      animation: slideUp 0.5s ease-out;
    }

    @keyframes slideUp {
      from { transform: translateY(50px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .login-title {
      font-size: 1.8rem;
      margin-bottom: 20px;
      color: var(--text);
    }

    .login-input {
      width: 100%;
      padding: 12px 15px;
      margin: 10px 0;
      border: none;
      border-radius: 5px;
      background-color: var(--gray);
      color: var(--text);
      font-size: 1em;
      transition: all 0.3s;
    }

    .login-input:focus {
      outline: none;
      box-shadow: 0 0 0 2px var(--accent);
    }

    .login-button {
      width: 100%;
      padding: 12px;
      margin-top: 20px;
      background: linear-gradient(90deg, var(--primary), var(--secondary));
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 1em;
      cursor: pointer;
      transition: all 0.3s;
    }

    .login-button:hover {
      background: linear-gradient(90deg, var(--secondary), var(--primary));
      transform: translateY(-2px);
    }

    .back-button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      background: transparent;
      color: var(--text);
      border: 1px solid var(--gray);
      border-radius: 5px;
      font-size: 0.9em;
      cursor: pointer;
      transition: all 0.3s;
    }

    .back-button:hover {
      background: rgba(255, 255, 255, 0.1);
    }

    .error-message {
      color: #ff6b6b;
      margin-top: 10px;
      font-size: 0.9em;
      min-height: 20px;
    }

    /* Header */
    .app-header {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      color: var(--text);
      padding: 15px 20px;
      text-align: center;
      font-size: 1.5em;
      font-weight: bold;
      letter-spacing: 1px;
      position: relative;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    }

    .app-header::after {
      content: "AI Assistant (Filsafat & Agama)";
      display: block;
      font-size: 0.6em;
      opacity: 0.8;
      margin-top: 5px;
    }

    .header-actions {
      display: flex;
      gap: 10px;
    }

    .header-btn {
      background: rgba(255, 255, 255, 0.1);
      border: none;
      color: white;
      padding: 8px 15px;
      border-radius: 5px;
      cursor: pointer;
      font-size: 0.8em;
      transition: all 0.3s;
      display: flex;
      align-items: center;
      gap: 5px;
    }

    .header-btn:hover {
      background: rgba(255, 255, 255, 0.2);
    }

    /* Chat Container */
    .chat-container {
      flex: 1;
      padding: 15px;
      overflow-y: auto;
      background-color: var(--dark);
      height: calc(100vh - 150px);
    }

    .message {
      margin-bottom: 15px;
      padding: 12px 18px;
      border-radius: 20px;
      max-width: 80%;
      word-wrap: break-word;
      animation: fadeIn 0.3s ease;
      line-height: 1.5;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .user-message {
      background: linear-gradient(135deg, rgba(106, 13, 173, 0.8), rgba(75, 0, 130, 0.8));
      align-self: flex-end;
      margin-left: auto;
      border-bottom-right-radius: 5px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
      color: white;
    }

    .bot-message {
      background-color: var(--light);
      align-self: flex-start;
      margin-right: auto;
      border-bottom-left-radius: 5px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
    }

    /* Input Area */
    .input-container {
      display: flex;
      padding: 15px;
      background-color: var(--light);
      border-top: 1px solid var(--gray);
      position: fixed;
      bottom: 0;
      width: 100%;
      max-width: 100%;
    }

    #user-input {
      flex: 1;
      padding: 12px 18px;
      border: none;
      border-radius: 25px;
      background-color: var(--gray);
      color: var(--text);
      outline: none;
      font-size: 1em;
      transition: all 0.3s;
    }

    #user-input:focus {
      box-shadow: 0 0 0 2px var(--primary);
    }

    #user-input::placeholder {
      color: rgba(255, 255, 255, 0.5);
    }

    .input-actions {
      display: flex;
      gap: 10px;
      margin-left: 10px;
    }

    .input-btn {
      padding: 12px;
      border: none;
      border-radius: 50%;
      background: var(--gray);
      color: white;
      cursor: pointer;
      transition: all 0.3s;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 44px;
      height: 44px;
    }

    .input-btn:hover {
      background: var(--accent);
      transform: scale(1.05);
    }

    /* Camera Modal */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      z-index: 1001;
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background-color: var(--light);
      padding: 20px;
      border-radius: 10px;
      width: 90%;
      max-width: 500px;
      text-align: center;
    }

    .modal-title {
      font-size: 1.5rem;
      margin-bottom: 15px;
      color: var(--text);
    }

    #camera-preview {
      width: 100%;
      background-color: var(--dark);
      border-radius: 5px;
      margin-bottom: 15px;
    }

    .modal-actions {
      display: flex;
      gap: 10px;
      justify-content: center;
    }

    .modal-btn {
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
    }

    .modal-btn-primary {
      background-color: var(--primary);
      color: white;
    }

    .modal-btn-secondary {
      background-color: var(--gray);
      color: white;
    }

    .modal-btn:hover {
      opacity: 0.9;
      transform: translateY(-2px);
    }

    /* Typing Indicator */
    .typing-indicator {
      display: inline-block;
      padding: 10px;
    }

    .typing-dot {
      display: inline-block;
      width: 8px;
      height: 8px;
      background: rgba(255, 255, 255, 0.7);
      border-radius: 50%;
      margin: 0 2px;
      animation: typingAnimation 1.4s infinite ease-in-out;
    }

    .typing-dot:nth-child(2) {
      animation-delay: 0.2s;
    }

    .typing-dot:nth-child(3) {
      animation-delay: 0.4s;
    }

    @keyframes typingAnimation {
      0%, 60%, 100% { transform: translateY(0); }
      30% { transform: translateY(-5px); }
    }

    /* Welcome Message */
    .welcome-message {
      text-align: center;
      padding: 20px;
      font-size: 0.9em;
      color: rgba(255, 255, 255, 0.7);
      line-height: 1.6;
    }

    /* Responsive Design */
    @media (min-width: 768px) {
      .app-container {
        max-width: 768px;
        margin: 0 auto;
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
      }
      
      .input-container {
        max-width: 768px;
      }
      
      .chat-container {
        height: calc(100vh - 160px);
      }
    }

    @media (max-width: 600px) {
      .welcome-title {
        font-size: 2.5rem;
      }
      
      .start-title {
        font-size: 2.5rem;
      }
      
      .welcome-subtitle, .start-description {
        font-size: 1rem;
        padding: 0 20px;
      }
      
      .login-box {
        padding: 20px;
      }
      
      .header-btn span {
        display: none;
      }
      
      .header-btn {
        padding: 8px;
      }
    }
  </style>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
  <!-- Welcome Screen -->
  <div class="welcome-screen">
    <h1 class="welcome-title">WELCOME TO KHOZIN ASROR AI</h1>
    <p class="welcome-subtitle">Asisten Virtual Filsafat, Logika & Agama Islam yang Canggih</p>
    <div class="loading-bar">
      <div class="loading-progress"></div>
    </div>
  </div>

  <!-- Start Screen -->
  <div class="start-screen" id="start-screen">
    <h1 class="start-title">Khozin Asror AI</h1>
    <p class="start-description">Platform canggih untuk eksplorasi filsafat, logika, dan agama Islam. Temukan jawaban mendalam dari asisten virtual berbasis AI.</p>
    <button class="start-button" id="start-button">MULAI SEKARANG</button>
  </div>

  <!-- Login Screen -->
  <div class="login-container" id="login-screen" style="display: none;">
    <div class="login-box">
      <h1 class="login-title">Khozin Asror AI</h1>
      <p>Asisten Virtual Filsafat, Logika & Agama</p>
      <input type="text" id="username" class="login-input" placeholder="Username" autocomplete="off">
      <input type="password" id="password" class="login-input" placeholder="Password" autocomplete="off">
      <button class="login-button" id="login-button">MASUK</button>
      <button class="back-button" id="back-button">KEMBALI</button>
      <div id="login-error" class="error-message"></div>
    </div>
  </div>

  <!-- Main App -->
  <div class="app-container" id="app-container" style="display: none;">
    <div class="app-header">
      <span>Khozin Asror AI</span>
      <div class="header-actions">
        <button class="header-btn" id="camera-button">
          <i class="fas fa-camera"></i>
          <span>Kamera</span>
        </button>
        <button class="header-btn" id="logout-button">
          <i class="fas fa-sign-out-alt"></i>
          <span>Keluar</span>
        </button>
      </div>
    </div>
    
    <div class="chat-container" id="chat">
      <div class="message bot-message">
        <div style="display: flex; align-items: center; gap: 10px;">
          <div style="width: 40px; height: 40px; border-radius: 50%; background: linear-gradient(135deg, var(--primary), var(--secondary)); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold;">AI</div>
          <div>
            <span>Assalamu'alaikum! Saya Khozin Asror AI, asisten virtual bidang filsafat, logika, dan agama. 🤖</span>
            <br>
            <span style="font-size: 0.8em; opacity: 0.8;">Saya diciptakan oleh Muhammad Khozin Asror untuk membantu diskusi keilmuan.</span>
          </div>
        </div>
      </div>
      <div class="welcome-message">
        <p>Anda bisa menanyakan tentang: filsafat, logika, agama Islam, atau tentang pencipta saya.</p>
        <p>Contoh pertanyaan filsafat: "Apa itu epistemologi?" atau "Jelaskan filsafat Plato"</p>
        <p>Contoh pertanyaan agama: "Apa itu thaharah?" atau "Jelaskan thaharah serta dalilnya tentang wudhu"</p>
        <p>Anda juga bisa bertanya dengan kata tanya: apa, bagaimana, mengapa, jelaskan, atau kenapa.</p>
      </div>
    </div>
    
    <div class="input-container">
      <input type="text" id="user-input" placeholder="Tulis pertanyaan tentang filsafat, logika, atau agama..." autocomplete="off">
      <div class="input-actions">
        <button class="input-btn" id="send-button"><i class="fas fa-paper-plane"></i></button>
        <button class="input-btn" id="attach-button"><i class="fas fa-paperclip"></i></button>
      </div>
    </div>
  </div>

  <!-- Camera Modal -->
  <div class="modal" id="camera-modal">
    <div class="modal-content">
      <h2 class="modal-title">Ambil Foto</h2>
      <video id="camera-preview" autoplay playsinline></video>
      <div class="modal-actions">
        <button class="modal-btn modal-btn-primary" id="capture-button"><i class="fas fa-camera"></i> Ambil Foto</button>
        <button class="modal-btn modal-btn-secondary" id="close-camera"><i class="fas fa-times"></i> Tutup</button>
      </div>
    </div>
  </div>

  <script>
    // DOM Elements
    const startScreen = document.getElementById('start-screen');
    const loginScreen = document.getElementById('login-screen');
    const appContainer = document.getElementById('app-container');
    const startButton = document.getElementById('start-button');
    const backButton = document.getElementById('back-button');
    const loginButton = document.getElementById('login-button');
    const logoutButton = document.getElementById('logout-button');
    const usernameInput = document.getElementById('username');
    const passwordInput = document.getElementById('password');
    const loginError = document.getElementById('login-error');
    const chatContainer = document.getElementById('chat');
    const userInput = document.getElementById('user-input');
    const sendButton = document.getElementById('send-button');
    const attachButton = document.getElementById('attach-button');
    const cameraButton = document.getElementById('camera-button');
    const cameraModal = document.getElementById('camera-modal');
    const cameraPreview = document.getElementById('camera-preview');
    const captureButton = document.getElementById('capture-button');
    const closeCamera = document.getElementById('close-camera');
    
    // Camera variables
    let stream = null;
    let capturedImage = null;

    // Credentials
    const CORRECT_USERNAME = "khozin";
    const CORRECT_PASSWORD = "ozin123";

    // Enhanced knowledge base with 100 philosophy questions and answers
    const knowledgeBase = {
      // General
      "assalamualaikum": "Wa'alaikumussalam! Ada yang bisa saya bantu mengenai filsafat, logika, atau agama?",
      "halo": "Wa'alaikumussalam! Ada yang bisa saya bantu mengenai filsafat, logika, atau agama?",
      "hai": "Wa'alaikumussalam! Mari berdiskusi tentang ilmu pengetahuan.",
      "apa kabar": "Alhamdulillah saya baik. Bagaimana dengan Anda hari ini?",
      "siapa kamu": "Saya Khozin Asror AI, asisten virtual yang diciptakan oleh Muhammad Khozin Asror untuk membantu diskusi filsafat, logika, dan agama.",
      "terima kasih": "Afwan, sama-sama! Semoga ilmu yang didapat bermanfaat.",
      "tolong": "Tentu, saya akan membantu semampu saya. Apa yang ingin Anda tanyakan?",
      
      // About Yayasan Al Ikhlas
      "dimana yayasan al ikhlas": "Alamat Yayasan Al Ikhlas: Jl Tambak Wedi Tengah GG 5 No 8, Kenjeran, Surabaya.",
      
      // Islam Basics
      "apa itu islam": "Islam adalah agama yang diturunkan Allah SWT kepada Nabi Muhammad SAW sebagai petunjuk hidup manusia agar selamat dunia dan akhirat.",
      "rukun islam ada berapa": "Rukun Islam ada lima: Syahadat, Shalat, Zakat, Puasa, dan Haji bagi yang mampu.",
      "rukun iman ada berapa": "Rukun Iman ada enam: Iman kepada Allah, Malaikat, Kitab, Rasul, Hari Akhir, dan Qada' dan Qadar.",
      
      // About Creator
      "siapakah khozin itu": "Khozin adalah nama panggilan, nama lengkap beliau adalah MUHAMMAD KHOZIN ASROR. Beliau menuntut ilmu di Kediri dan juga Lamongan, seorang santri dan guru pengajar yang kompeten dalam berbagai bidang keilmuan. Saya diciptakan oleh beliau sebagai asisten virtual.",
      "siapa penciptamu": "Saya diciptakan oleh Muhammad Khozin Asror, seorang guru dan penuntut ilmu dari Jawa Timur.",
      "muhammad khozin asror": "Beliau adalah pencipta saya, seorang pengajar yang mendalami berbagai bidang ilmu termasuk filsafat, logika, dan ilmu agama. Berasal dari Jawa Timur dan aktif dalam dunia pendidikan.",
      
      // Time
      "jam berapa sekarang": Sekarang jam ${new Date().toLocaleTimeString('id-ID')}.,
      "tanggal berapa hari ini": Hari ini tanggal ${new Date().toLocaleDateString('id-ID', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}.,
      
      // Schedule and Personal Info
      "sekarang waktunya matkul siapa": "Sekarang matkulnya Bu Risa pelajaran kewirausahaan. Beliau adalah dosen yang baik dan bijaksana. Semoga tuan khozin dapat nilai yang sangat baik dari Bu Risa.",
      "sekarang matkul siapa": "Sekarang matkulnya Bu Risa pelajaran kewirausahaan. Beliau adalah dosen yang baik dan bijaksana. Semoga tuan khozin dapat nilai yang sangat baik dari Bu Risa.",
      
      "siapa jodoh khozin": "Jodoh khozin adalah Zulfana Munjida yang biasa dipanggil Zulfa. Dia berasal dari Malang kecamatan Pujon. Dia sangat cantik dan comel, serta baik hati dan tidak pernah ngambek.",
      "jodoh khozin siapa": "Jodoh khozin adalah Zulfana Munjida (Zulfa) dari Malang, Pujon. Dia dikenal sebagai wanita yang cantik, comel, baik hati, dan penyayang.",
      
      "khozin tinggal dimana": "Khozin tinggal di kota Surabaya kecamatan Kenjeran.",
      "dimana tinggalnya khozin": "Khozin tinggal di Surabaya tepatnya di kecamatan Kenjeran.",
      
      "pendidikan khozin": "Khozin belajar di Kediri selama 3 tahun di bawah bimbingan Kyai yang sangat karismatik, yakni KH Ahmad Dain Arif Purwoasri Kediri. Kemudian melanjutkan mengajar di Yayasan Al Ikhlas (milik abahnya) selama 1 tahun. Selanjutnya nyantri di KH Abdul Ghofur Ponpes Sunan Drajat Lamongan sekaligus menjadi pengurus.",
      "belajar di mana saja khozin": "Riwayat pendidikan khozin: 3 tahun di Kediri (KH Ahmad Dain Arif), mengajar di Yayasan Al Ikhlas 1 tahun, kemudian nyantri di Ponpes Sunan Drajat Lamongan (KH Abdul Ghofur) sambil menjadi pengurus.",
      
      "siapa zulfa": "Zulfa adalah jodohnya tuan saya, yakni khozin. Nama lengkapnya Zulfana Munjida. Dia sangat cantik dan Sholehah, serta baik hati dan tidak pernah merajuk.",
      "zulfa itu siapa": "Zulfa (Zulfana Munjida) adalah pasangan hidup khozin. Wanita asal Malang (Pujon) yang dikenal cantik, sholehah, dan berhati baik.",
      
      "siapa orang tua khozin": "Orang tua khozin adalah KH Muhammad Fadil Uzeir (pengasuh Yayasan Al Ikhlas) berasal dari Wates Kediri bin KH Muhammad Uzeir.",
      "orang tua khozin siapa": "Ayah khozin adalah KH Muhammad Fadil Uzeir, pengasuh Yayasan Al Ikhlas, putra dari KH Muhammad Uzeir asal Wates Kediri.",
      
      "di mana yayasan al ikhlas": "Yayasan Al Ikhlas terletak di kota Surabaya, kecamatan Kenjeran, Jl Tambak Wedi Tengah GG 5 No 8.",
      "lokasi yayasan al ikhlas": "Alamat Yayasan Al Ikhlas: Jl Tambak Wedi Tengah GG 5 No 8, Kenjeran, Surabaya.",
      
      // Philosophy Questions (100 questions)
      "apa itu filsafat": "Filsafat adalah ilmu yang mempelajari hakikat keberadaan, pengetahuan, nilai-nilai, akal, dan bahasa. Berasal dari kata Yunani 'philosophia' yang berarti cinta kebijaksanaan.",
      "apa itu metafisika": "Metafisika adalah cabang filsafat yang mempelajari hakikat realitas, keberadaan, dan alam semesta. Membahas pertanyaan mendasar tentang apa yang ada di balik realitas fisik.",
      "apa itu epistemologi": "Epistemologi adalah cabang filsafat yang mempelajari tentang pengetahuan, mencakup asal-usul, sifat, metode, dan batasan pengetahuan manusia.",
      "apa itu etika": "Etika adalah cabang filsafat yang mempelajari tentang nilai baik-buruk, benar-salah dalam perilaku manusia. Terbagi menjadi etika normatif, metaetika, dan etika terapan.",
      "apa itu logika": "Logika adalah studi tentang penalaran yang valid dan argumen yang benar. Dibagi menjadi logika formal (silogisme) dan logika informal (analisis argumen).",
      "jelaskan filsafat plato": "Plato adalah filsuf Yunani yang mengembangkan teori dunia ide. Menurutnya, realitas sejati ada di dunia ide yang abadi, sementara dunia fisik hanyalah bayangan.",
      "jelaskan filsafat aristoteles": "Aristoteles, murid Plato, menekankan empirisme dan logika. Ia mengembangkan teori empat sebab (material, formal, efisien, final) dan konsep golden mean dalam etika.",
      "jelaskan filsafat descartes": "René Descartes dikenal dengan cogito ergo sum (aku berpikir maka aku ada). Ia bapak filsafat modern yang meragukan segala sesuatu untuk menemukan kepastian.",
      "jelaskan filsafat kant": "Immanuel Kant mengembangkan filsafat kritis yang menyatakan bahwa pengetahuan berasal dari sintesis pengalaman indrawi dan kategori pemikiran bawaan.",
      "apa itu rasionalisme": "Rasionalisme adalah aliran filsafat yang menekankan akal sebagai sumber utama pengetahuan. Tokohnya termasuk Descartes, Spinoza, dan Leibniz.",
      "apa itu empirisme": "Empirisme adalah aliran filsafat yang menyatakan pengetahuan berasal dari pengalaman indrawi. Tokohnya termasuk Locke, Berkeley, dan Hume.",
      "apa itu eksistensialisme": "Eksistensialisme menekankan kebebasan individu, pilihan, dan tanggung jawab dalam menentukan makna hidup. Tokohnya Sartre, Camus, Kierkegaard.",
      "apa itu stoisisme": "Stoisisme adalah aliran filsafat yang mengajarkan pengendalian diri, menerima apa yang tidak bisa diubah, dan hidup sesuai alam. Tokohnya Marcus Aurelius.",
      "apa itu utilitarianisme": "Utilitarianisme adalah teori etika yang menilai tindakan berdasarkan konsekuensinya, memaksimalkan kebahagiaan terbesar untuk jumlah terbanyak.",
      "apa itu dekonstruksi": "Dekonstruksi adalah metode filsafat Jacques Derrida untuk menganalisis oposisi biner dalam teks dan menunjukkan ketidakstabilan makna.",
      "apa itu fenomenologi": "Fenomenologi adalah metode filsafat Edmund Husserl yang mempelajari struktur kesadaran dan fenomena seperti yang dialami subjek.",
      "apa itu positivisme": "Positivisme adalah paham bahwa hanya pengetahuan yang berasal dari metode ilmiah yang valid. Dipelopori oleh Auguste Comte.",
      "apa itu postmodernisme": "Postmodernisme menolak narasi besar, kebenaran absolut, dan menekankan relativitas pengetahuan. Tokohnya Foucault, Lyotard.",
      "apa itu nihilisme": "Nihilisme adalah pandangan yang menolak makna, nilai, atau pengetahuan yang objektif. Sering dikaitkan dengan Nietzsche meski ia mengkritiknya.",
      "apa itu humanisme": "Humanisme menekankan nilai dan agensi manusia, rasionalitas, dan etika sekuler tanpa referensi ke yang transenden.",
      "apa itu materialisme": "Materialisme adalah pandangan bahwa hanya materi yang nyata dan fenomena mental berasal dari proses fisik.",
      "apa itu idealisme": "Idealisme berpendapat bahwa realitas pada dasarnya mental atau spiritual. Versi ekstrimnya menyatakan materi tidak ada.",
      "apa itu dualisme": "Dualisme Descartes membagi realitas menjadi dua substansi: pikiran (res cogitans) dan materi (res extensa).",
      "apa itu monisme": "Monisme adalah pandangan bahwa hanya ada satu substansi dasar realitas, bisa material (materialisme) atau spiritual (idealisme).",
      "apa itu skeptisisme": "Skeptisisme adalah pendirian filosofis yang meragukan kemungkinan pengetahuan tertentu atau semua pengetahuan.",
      "apa itu pragmatisme": "Pragmatisme menilai kebenaran berdasarkan konsekuensi praktis dan kegunaannya. Tokohnya William James, John Dewey.",
      "apa itu strukturalisme": "Strukturalisme menganalisis budaya melalui sistem tanda dan struktur yang mendasarinya. Tokohnya Saussure, Lévi-Strauss.",
      "apa itu hermeneutika": "Hermeneutika adalah teori interpretasi teks, terutama teks suci dan filosofis. Tokohnya Gadamer, Ricoeur.",
      "apa itu dialektika": "Dialektika adalah metode diskusi melalui tesis-antitesis-sintesis. Hegel mengembangkannya sebagai proses perkembangan sejarah.",
      "apa itu marxisme": "Marxisme adalah filsafat sosial Karl Marx yang menganalisis konflik kelas dan mendorong perubahan revolusioner menuju masyarakat tanpa kelas.",
      "apa itu feminisme filosofis": "Feminisme filosofis mengkritik bias gender dalam filsafat tradisional dan mengembangkan epistemologi feminis.",
      "apa itu filsafat analitik": "Filsafat analitik menekankan klarifikasi konsep melalui analisis bahasa dan logika. Berkembang di Inggris dan Amerika.",
      "apa itu filsafat kontinental": "Filsafat kontinental mencakup fenomenologi, eksistensialisme, postmodernisme yang berkembang di Eropa daratan.",
      "apa itu filsafat timur": "Filsafat Timur mencakup tradisi pemikiran Asia seperti Konfusianisme, Taoisme, Buddhisme, dan Hinduisme yang berbeda dengan Barat.",
      "apa itu filsafat islam": "Filsafat Islam mengembangkan pemikiran Yunani dalam konteks Islam dengan tokoh seperti Al-Farabi, Ibnu Sina, Al-Ghazali, Ibnu Rusyd.",
      "apa itu filsafat politik": "Filsafat politik mempelajari konsep seperti keadilan, kekuasaan, hak, dan bentuk pemerintahan yang ideal.",
      "apa itu filsafat bahasa": "Filsafat bahasa mempelajari hubungan antara bahasa, pemikiran, dan realitas. Tokohnya Wittgenstein, Austin.",
      "apa itu filsafat ilmu": "Filsafat ilmu mempelajari dasar-dasar, metode, dan implikasi ilmu pengetahuan, termasuk demarkasi antara sains dan non-sains.",
      "apa itu filsafat seni": "Filsafat seni (estetika) mempelajari konsep keindahan, seni, dan pengalaman estetis.",
      "apa itu filsafat sejarah": "Filsafat sejarah mempelajari makna dan pola dalam peristiwa sejarah, apakah ada tujuan atau kebetulan belaka.",
      "apa itu filsafat pendidikan": "Filsafat pendidikan mempertanyakan tujuan pendidikan, metode pembelajaran, dan hubungan antara pendidikan dan masyarakat.",
      "apa itu filsafat hukum": "Filsafat hukum mempelajari konsep keadilan, hak, dan hubungan antara hukum dengan moral.",
      "apa itu filsafat ekonomi": "Filsafat ekonomi mempelajari asumsi filosofis di balik teori ekonomi dan konsep seperti nilai, kerja, distribusi kekayaan.",
      "apa itu filsafat teknologi": "Filsafat teknologi mempelajari dampak teknologi pada manusia dan masyarakat, serta etika pengembangan teknologi.",
      "apa itu filsafat lingkungan": "Filsafat lingkungan mempelajari hubungan etis antara manusia dengan alam dan tanggung jawab ekologis.",
      "apa itu filsafat pikiran": "Filsafat pikiran mempelajari sifat kesadaran, hubungan pikiran-tubuh, dan masalah seperti qualia dan intentionality.",
      "apa itu filsafat agama": "Filsafat agama mempelajari konsep ketuhanan, argumen tentang keberadaan Tuhan, masalah kejahatan, dan pengalaman religius.",
      "apa itu filsafat matematika": "Filsafat matematika mempelajari status ontologis objek matematika dan dasar epistemologis pengetahuan matematika.",
      "apa itu filsafat fisika": "Filsafat fisika mempelajari interpretasi teori fisika seperti mekanika kuantum dan relativitas, serta konsep ruang dan waktu.",
      "apa itu filsafat biologi": "Filsafat biologi mempelajari konsep seperti seleksi alam, fungsi biologis, dan hubungan antara biologi dengan ilmu lain.",
      "apa itu filsafat psikologi": "Filsafat psikologi mempelajari asumsi filosofis dalam psikologi, seperti masalah kesadaran dan hubungan pikiran-otak.",
      "apa itu filsafat sosial": "Filsafat sosial mempelajari dasar-dasar masyarakat, hubungan individu-kelompok, dan konsep seperti alienasi dan pengakuan.",
      "jelaskan teori bentuk plato": "Teori Bentuk Plato menyatakan bahwa realitas sejati adalah dunia ide (form) yang abadi dan sempurna, sementara dunia fisik adalah bayangan yang berubah-ubah.",
      "jelaskan etika virtue aristoteles": "Etika Virtue Aristoteles menekankan pembentukan karakter yang baik melalui kebiasaan. Kebahagiaan (eudaimonia) dicapai dengan hidup sesuai dengan virtue (keutamaan).",
      "jelaskan cogito descartes": "Cogito ergo sum (Aku berpikir maka aku ada) adalah fondasi kepastian Descartes setelah meragukan segala sesuatu. Menunjukkan eksistensi diri sebagai pemikir.",
      "jelaskan imperatif kategoris kant": "Imperatif Kategoris Kant adalah prinsip moral universal: 'Bertindaklah hanya menurut maksim yang dapat kamu kehendaki menjadi hukum universal'. Dasar etika deontologis.",
      "jelaskan filsafat hegel": "Hegel mengembangkan sistem idealisme absolut dengan dialektika (tesis-antitesis-sintesis) sebagai motor perkembangan sejarah menuju kesadaran mutlak.",
      "jelaskan filsafat nietzsche": "Nietzsche mengkritik moralitas tradisional, mengumandangkan 'kematian Tuhan', dan menyerukan penciptaan nilai baru oleh Übermensch (manusia unggul).",
      "jelaskan filsafat marx": "Marx mengembangkan materialisme historis yang melihat sejarah sebagai perjuangan kelas dan meramalkan revolusi proletar menuju masyarakat tanpa kelas.",
      "jelaskan filsafat heidegger": "Heidegger menganalisis keberadaan (Dasein) manusia sebagai 'berada-di-dunia' yang temporal dan selalu sudah terlempar dalam jaringan makna.",
      "jelaskan filsafat wittgenstein": "Wittgenstein awal (Tractatus) melihat bahasa sebagai gambar fakta, sedangkan akhir (Investigasi) melihat bahasa sebagai permainan dalam bentuk kehidupan.",
      "jelaskan filsafat foucault": "Foucault menganalisis hubungan kekuasaan-pengetahuan dalam institusi seperti penjara dan rumah sakit jiwa, serta konsep wacana dan arkeologi pengetahuan.",
      "jelaskan filsafat derrida": "Derrida mengembangkan dekonstruksi untuk menunjukkan ketidakstabilan makna dalam teks dan membongkar oposisi biner yang hierarkis.",
      "jelaskan filsafat rousseau": "Rousseau mengkritik peradaban yang merusak sifat alami manusia dan mengusulkan kontrak sosial berdasarkan kehendak umum (volonté générale).",
      "jelaskan filsafat locke": "Locke mengembangkan empirisme dan teori tabula rasa (pikiran sebagai kertas kosong), serta membela hak alamiah seperti hidup, kebebasan, dan properti.",
      "jelaskan filsafat hume": "Hume adalah empirisis radikal yang meragukan kausalitas (hanya kebiasaan) dan membedakan antara 'is' dan 'ought' dalam etika.",
      "jelaskan filsafat spinoza": "Spinoza mengembangkan monisme bahwa Tuhan dan alam adalah satu substansi (Deus sive Natura), dan kebebasan adalah memahami determinasi alam.",
      "jelaskan filsafat leibniz": "Leibniz mengusulkan monadologi (realitas terdiri dari monad yang tidak berinteraksi) dan prinsip alasan cukup (nothing happens without a reason).",
      "jelaskan filsafat berkeley": "Berkeley mengembangkan idealisme subjektif bahwa 'esse est percipi' (ada adalah dipersepsikan), menolak materi yang independen dari persepsi.",
      "jelaskan filsafat schopenhauer": "Schopenhauer melihat kehendak buta sebagai esensi realitas, sumber penderitaan, dan jalan pembebasan melalui penolakan kehendak dan seni.",
      "jelaskan filsafat kierkegaard": "Kierkegaard, bapak eksistensialisme, menekankan lompatan iman, pilihan subjektif, dan tahap hidup (estetis, etis, religius).",
      "jelaskan filsafat camus": "Camus mengembangkan absurdisme bahwa manusia mencari makna di alam semesta yang diam, dengan pilihan memberontak secara bermartabat.",
      "jelaskan filsafat sartre": "Sartre menyatakan 'eksistensi mendahului esensi', manusia terkutuk untuk bebas dan sepenuhnya bertanggung jawab atas pilihannya.",
      "jelaskan filsafat russell": "Russell mengembangkan filsafat analitik, teori deskripsi, dan logika matematika bersama Whitehead dalam Principia Mathematica.",
      "jelaskan filsafat quine": "Quine mengkritik distingsi analitik-sintetik dan menyarankan holisme bahwa pengetahuan adalah jaringan kepercayaan yang saling terkait.",
      "jelaskan filsafat rawls": "Rawls mengembangkan teori keadilan sebagai fairness dengan prinsip kesetaraan dan perbedaan di balik 'veil of ignorance'.",
      "jelaskan filsafat nozick": "Nozick membela libertarianisme dan hak properti dalam Anarchy, State, and Utopia, mengkritik redistribusi sebagai pelanggaran hak.",
      "jelaskan filsafat habermas": "Habermas mengembangkan teori tindakan komunikatif dan etika diskursus yang mencari konsensus rasional melalui dialog bebas dominasi.",
      "jelaskan filsafat arendt": "Arendt menganalisis totalitarianisme, vita activa (kerja, karya, tindakan), dan konsep 'banalitas kejahatan' dalam laporan Eichmann.",
      "jelaskan filsafat chomsky": "Chomsky mengembangkan teori tata bahasa generatif dalam linguistik dan kritik terhadap media dan kebijakan luar negeri AS.",
      "jelaskan filsafat seni plato": "Plato mengkritik seni sebagai tiruan dari tiruan (dunia ide), berpotensi merusak moral, dan mengusung pengusiran penyair dari republik ideal.",
      "jelaskan filsafat seni aristoteles": "Aristoteles melihat seni sebagai mimesis (peniruan) yang memiliki nilai katarsis (pembersihan emosi) dalam tragedi.",
      "jelaskan filsafat seni kant": "Kant mengembangkan estetika formalis bahwa pengalaman indah adalah disinterested pleasure yang melibatkan imajinasi dan pemahaman.",
      "jelaskan filsafat seni hegel": "Hegel melihat seni sebagai manifestasi roh absolut dalam bentuk sensuous, dengan perkembangan dari simbolis-klasik-romantik.",
      "jelaskan filsafat seni nietzsche": "Nietzsche membedakan antara kecenderungan apollonian (rasional, bentuk) dan dionysian (irasional, ekstasi) dalam seni.",
      "jelaskan filsafat seni heidegger": "Heidegger melihat seni sebagai pembukaan (aletheia) keberadaan, seperti kuil Yunani yang mengungkapkan dunia historis suatu masyarakat.",
      "jelaskan filsafat seni benjamin": "Walter Benjamin menganalisis reproduksi mekanis seni yang menghilangkan aura karya seni yang unik dalam konteks ritual.",
      "jelaskan filsafat seni adorno": "Adorno mengkritik industri budaya yang menstandarisasi seni sebagai komoditas, dan membela seni otonom yang menolak rekonsiliasi palsu.",
      "jelaskan filsafat seni dewey": "Dewey melihat seni sebagai pengalaman (art as experience) yang terintegrasi dengan kehidupan sehari-hari, bukan terisolasi di museum.",
      "jelaskan filsafat seni danto": "Danto menyatakan 'akhir seni' dalam narasi besar, dan mengembangkan teori dunia seni (artworld) yang mengkonstitusi objek sebagai seni.",
      "jelaskan filsafat seni goodman": "Goodman mengembangkan pendekatan semiotik bahwa seni adalah simbol yang berfungsi secara estetis ketika dieksemplifikasi bukan secara denotatif.",
      "jelaskan filsafat seni merleau-ponty": "Merleau-Ponty melihat seni sebagai ekspresi persepsi tubuh (body-subject) yang mengungkapkan pengalaman hidup yang mendahului refleksi.",
      "jelaskan filsafat seni lyotard": "Lyotard membedakan antara seni modern yang mencari yang sublime yang takterpresentasikan dan postmodern yang bermain dengan konvensi.",
      "jelaskan filsafat seni deleuze": "Deleuze melihat seni sebagai blok sensasi yang menangkap kekuatan dan menjadi orang ketiga antara pencipta dan penikmat.",
      "jelaskan filsafat seni foucault": "Foucault menganalisis hubungan antara seni dan kekuasaan, seperti dalam konsep heterotopia sebagai ruang lain yang mengganggu tatanan normal.",
      "jelaskan filsafat seni derrida": "Derrida mendekonstruksi oposisi dalam estetika seperti bentuk-kandungan, asli-salinan, dan menekankan différance dalam interpretasi seni.",
      "jelaskan filsafat seni rancière": "Rancière mengembangkan konsep pembagian yang sensibel (partage du sensible) tentang siapa yang bisa berpartisipasi dalam dunia seni dan politik.",
      
      // Thaharah questions
      "jelaskan thaharah serta dalilnya": "Thaharah adalah bersuci dari hadas dan najis untuk melaksanakan ibadah. Dalilnya QS. Al-Maidah:6 'Hai orang-orang yang beriman, apabila kamu hendak mengerjakan shalat, maka basuhlah mukamu dan tanganmu sampai siku...'",
      "bagaimana thaharah": "Thaharah dilakukan dengan membersihkan diri dari hadas dan najis. Untuk hadas kecil dengan wudhu, hadas besar dengan mandi, dan jika tidak ada air bisa tayamum.",
      
      // Default
      "default": "Maaf, saya tidak sepenuhnya memahami pertanyaan Anda. Sebagai asisten bidang filsafat, logika, dan agama, saya bisa membantu menjawab pertanyaan terkait:<br>- Konsep filsafat<br>- Teori logika<br>- Pembahasan agama Islam<br>- Tentang pencipta saya<br>Silakan tanyakan dengan lebih spesifik."
    };

    // Initialize the app
    function initApp() {
      // Event listeners
      startButton.addEventListener('click', showLoginScreen);
      backButton.addEventListener('click', showStartScreen);
      loginButton.addEventListener('click', handleLogin);
      logoutButton.addEventListener('click', handleLogout);
      sendButton.addEventListener('click', sendMessage);
      attachButton.addEventListener('click', showCameraModal);
      cameraButton.addEventListener('click', showCameraModal);
      captureButton.addEventListener('click', captureImage);
      closeCamera.addEventListener('click', closeCameraModal);
      
      userInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') sendMessage();
      });
      
      // Check if already logged in
      if (localStorage.getItem('loggedIn') === 'true') {
        startScreen.style.display = 'none';
        loginScreen.style.display = 'none';
        showMainApp();
      } else {
        startScreen.style.display = 'flex';
      }
    }

    // Show login screen
    function showLoginScreen() {
      startScreen.style.display = 'none';
      loginScreen.style.display = 'flex';
      usernameInput.focus();
    }

    // Show start screen
    function showStartScreen() {
      loginScreen.style.display = 'none';
      startScreen.style.display = 'flex';
      usernameInput.value = '';
      passwordInput.value = '';
      loginError.textContent = '';
    }

    // Handle login
    function handleLogin() {
      const username = usernameInput.value.trim();
      const password = passwordInput.value.trim();
      
      if (!username || !password) {
        loginError.textContent = "Username dan password harus diisi!";
        return;
      }
      
      if (username === CORRECT_USERNAME && password === CORRECT_PASSWORD) {
        localStorage.setItem('loggedIn', 'true');
        showMainApp();
      } else {
        loginError.textContent = "Username atau password salah!";
        usernameInput.focus();
      }
    }

    // Handle logout
    function handleLogout() {
      localStorage.removeItem('loggedIn');
      loginScreen.style.display = 'none';
      appContainer.style.display = 'none';
      startScreen.style.display = 'flex';
      usernameInput.value = '';
      passwordInput.value = '';
      loginError.textContent = '';
    }

    // Show main app
    function showMainApp() {
      loginScreen.style.display = 'none';
      appContainer.style.display = 'block';
      userInput.focus();
      
      // Clear chat except first message
      const messages = chatContainer.querySelectorAll('.message');
      for (let i = 1; i < messages.length; i++) {
        messages[i].remove();
      }
    }

    // Show camera modal
    function showCameraModal() {
      cameraModal.style.display = 'flex';
      
      // Access camera
      if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
        navigator.mediaDevices.getUserMedia({ video: true })
          .then(function(mediaStream) {
            stream = mediaStream;
            cameraPreview.srcObject = mediaStream;
          })
          .catch(function(error) {
            console.error("Error accessing camera:", error);
            addMessage("Maaf, tidak dapat mengakses kamera. Pastikan Anda telah memberikan izin.", 'bot');
            closeCameraModal();
          });
      } else {
        addMessage("Browser Anda tidak mendukung akses kamera atau tidak memiliki kamera.", 'bot');
        closeCameraModal();
      }
    }

    // Close camera modal
    function closeCameraModal() {
      cameraModal.style.display = 'none';
      
      // Stop camera stream
      if (stream) {
        stream.getTracks().forEach(track => track.stop());
        stream = null;
      }
    }

    // Capture image from camera
    function captureImage() {
      if (!cameraPreview.srcObject) return;
      
      const canvas = document.createElement('canvas');
      canvas.width = cameraPreview.videoWidth;
      canvas.height = cameraPreview.videoHeight;
      const ctx = canvas.getContext('2d');
      ctx.drawImage(cameraPreview, 0, 0, canvas.width, canvas.height);
      
      capturedImage = canvas.toDataURL('image/png');
      
      // Add image to chat
      const messageDiv = document.createElement('div');
      messageDiv.classList.add('message', 'user-message');
      messageDiv.innerHTML = `
        <div style="display: flex; align-items: flex-end; justify-content: flex-end; gap: 10px;">
          <div>
            <img src="${capturedImage}" style="max-width: 200px; border-radius: 10px;">
            <p style="margin-top: 5px; font-size: 0.8em;">[Foto yang diambil]</p>
          </div>
          <div style="width: 40px; height: 40px; border-radius: 50%; background: linear-gradient(135deg, #3a7bd5, #00d2ff); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold;">KU</div>
        </div>
      `;
      
      chatContainer.appendChild(messageDiv);
      chatContainer.scrollTop = chatContainer.scrollHeight;
      
      // Respond to image
      setTimeout(() => {
        addMessage("Terima kasih telah mengirim foto. Saya adalah asisten teks, jadi saya tidak bisa menganalisis gambar. Namun, jika Anda memiliki pertanyaan tentang filsafat, logika, atau agama, saya akan dengan senang hati membantu!", 'bot');
      }, 1000);
      
      closeCameraModal();
    }

    // Add message to chat
    function addMessage(text, sender) {
      const messageDiv = document.createElement('div');
      messageDiv.classList.add('message', ${sender}-message);

      if (sender === 'bot') {
        messageDiv.innerHTML = `
          <div style="display: flex; align-items: flex-start; gap: 10px;">
            <div style="width: 40px; height: 40px; border-radius: 50%; background: linear-gradient(135deg, var(--primary), var(--secondary)); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold;">AI</div>
            <div>${text}</div>
          </div>
        `;
      } else {
        messageDiv.innerHTML = `
          <div style="display: flex; align-items: flex-end; justify-content: flex-end; gap: 10px;">
            <div>${text}</div>
            <div style="width: 40px; height: 40px; border-radius: 50%; background: linear-gradient(135deg, #3a7bd5, #00d2ff); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold;">KU</div>
          </div>
        `;
      }

      chatContainer.appendChild(messageDiv);
      chatContainer.scrollTop = chatContainer.scrollHeight;
    }

    // Show typing indicator
    function showTyping() {
      const typingDiv = document.createElement('div');
      typingDiv.classList.add('message', 'bot-message');
      typingDiv.id = 'typing-indicator';
      typingDiv.innerHTML = `
        <div style="display: flex; align-items: center; gap: 10px;">
          <div style="width: 40px; height: 40px; border-radius: 50%; background: linear-gradient(135deg, var(--primary), var(--secondary)); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold;">AI</div>
          <div class="typing-indicator">
            <div class="typing-dot"></div>
            <div class="typing-dot"></div>
            <div class="typing-dot"></div>
          </div>
        </div>
      `;
      chatContainer.appendChild(typingDiv);
      chatContainer.scrollTop = chatContainer.scrollHeight;
    }

    // Hide typing indicator
    function hideTyping() {
      const typingDiv = document.getElementById('typing-indicator');
      if (typingDiv) typingDiv.remove();
    }

    // Get AI response (offline version)
    function getAIResponse(message) {
      // Convert to lowercase and remove extra spaces and punctuation
      const cleanMessage = message.toLowerCase().trim().replace(/[^\w\s]/gi, '');
      
      // Check for exact matches
      if (knowledgeBase[cleanMessage]) {
        return knowledgeBase[cleanMessage];
      }
      
      // Check for partial matches
      for (const key in knowledgeBase) {
        if (cleanMessage.includes(key)) {
          return knowledgeBase[key];
        }
      }
      
      // Special cases for time/date
      if (cleanMessage.includes("jam") && (cleanMessage.includes("berapa") || cleanMessage.includes("sekarang"))) {
        return Sekarang jam ${new Date().toLocaleTimeString('id-ID')}.;
      }
      
      if (cleanMessage.includes("tanggal") && (cleanMessage.includes("berapa") || cleanMessage.includes("hari ini"))) {
        return Hari ini tanggal ${new Date().toLocaleDateString('id-ID', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}.;
      }
      
      // Check for khozin questions
      if (cleanMessage.includes("khozin") || cleanMessage.includes("asror")) {
        return knowledgeBase["siapakah khozin itu"];
      }
      
      // Check for creator questions
      if (cleanMessage.includes("pencipta") || cleanMessage.includes("pembuat") || cleanMessage.includes("pengembang")) {
        return knowledgeBase["siapa penciptamu"];
      }
      
      // Check for question words
      if (cleanMessage.startsWith("apa") || cleanMessage.startsWith("jelaskan") || 
          cleanMessage.startsWith("bagaimana") || cleanMessage.startsWith("mengapa") || 
          cleanMessage.startsWith("kenapa")) {
        
        // Try to find the most relevant answer
        const questionParts = cleanMessage.split(" ");
        for (let i = 1; i < questionParts.length; i++) {
          const partialQuestion = questionParts.slice(i).join(" ");
          for (const key in knowledgeBase) {
            if (key.includes(partialQuestion)) {
              return knowledgeBase[key];
            }
          }
        }
      }
      
      // Check for "jelaskan thaharah serta dalilnya" questions
      if (cleanMessage.startsWith("jelaskan thaharah serta dalilnya")) {
        const topic = cleanMessage.replace("jelaskan thaharah serta dalilnya", "").trim();
        if (topic) {
          return knowledgeBase["jelaskan thaharah serta dalilnya tentang " + topic] || 
                 "Maaf, saya belum memiliki informasi detail tentang topik tersebut dalam konteks thaharah dan dalilnya. Silakan tanyakan topik lain tentang thaharah.";
        }
        return knowledgeBase["jelaskan thaharah serta dalilnya"];
      }
      
      // Check for "bagaimana thaharah" questions
      if (cleanMessage.startsWith("bagaimana thaharah")) {
        const procedure = cleanMessage.replace("bagaimana thaharah", "").trim();
        if (procedure) {
          return knowledgeBase["bagaimana thaharah " + procedure] || 
                 "Maaf, saya belum memiliki informasi tentang prosedur thaharah tersebut. Silakan tanyakan cara thaharah yang lebih umum.";
        }
        return knowledgeBase["bagaimana thaharah"];
      }
      
      // Default response
      return knowledgeBase["default"];
    }

    // Send message
    function sendMessage() {
      const message = userInput.value.trim();
      if (!message) return;

      // Add user message
      addMessage(message, 'user');
      userInput.value = '';
      
      // Show typing indicator
      showTyping();
      
      // Simulate AI thinking
      setTimeout(() => {
        hideTyping();
        
        // Get AI response
        const response = getAIResponse(message);
        addMessage(response, 'bot');
      }, 1000 + Math.random() * 1000); // Random delay for more natural feel
    }

    // Initialize the app
    document.addEventListener('DOMContentLoaded', initApp);
  </script>
</body>
</html>
