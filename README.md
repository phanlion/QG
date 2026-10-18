<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gửi Quỳnh Giang - 20/10</title>

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&family=Dancing+Script:wght@600;700&family=Playfair+Display:ital,wght@0,600;0,700;0,800;1,600&display=swap" rel="stylesheet">
    
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Canvas Confetti CDN -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.2/dist/confetti.browser.min.js"></script>

    <!-- Tailwind Config -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: {
                            100: '#FFF9E5',
                            200: '#F7E5A9',
                            300: '#EBD06A',
                            400: '#D4AF37', // Champagne Gold
                            500: '#B59021',
                            600: '#8C6C11',
                        },
                        amber: {
                            soft: '#F8E8D5',
                            warm: '#D97706',
                            sunset: '#B45309'
                        },
                        rosegold: {
                            DEFAULT: '#B76E79',
                            light: '#E8B4B8',
                            soft: '#F5DCDD'
                        },
                        burgundy: {
                            800: '#3D040F',
                            900: '#260209',
                            950: '#140105'
                        }
                    },
                    fontFamily: {
                        serif: ['Playfair Display', 'serif'],
                        sans: ['Be Vietnam Pro', 'sans-serif'],
                        handwriting: ['Dancing Script', 'cursive']
                    }
                }
            }
        }
    </script>

    <style>
        /* Touch & Visual Defaults */
        * {
            -webkit-tap-highlight-color: transparent;
            box-sizing: border-box;
        }

        html, body {
            min-height: 100%;
            width: 100%;
            margin: 0;
            padding: 0;
            background-color: #140105;
            color: #f1f5f9;
            overflow-x: hidden;
        }

        /* Typography & Gradient Text */
        .text-gold-gradient {
            background: linear-gradient(135deg, #FFF9E5 0%, #D4AF37 50%, #B59021 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .text-rose-gradient {
            background: linear-gradient(135deg, #FFF9E5 0%, #E8B4B8 50%, #B76E79 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Glassmorphism Cards */
        .glass-card {
            background: rgba(38, 2, 9, 0.78);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(212, 175, 55, 0.3);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.6), inset 0 0 15px rgba(212, 175, 55, 0.08);
        }

        /* Gold Glow Button */
        .btn-gold {
            background: linear-gradient(135deg, #D4AF37 0%, #B59021 100%);
            color: #140105;
            box-shadow: 0 4px 18px rgba(212, 175, 55, 0.35);
            transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .btn-gold:hover {
            background: linear-gradient(135deg, #EBD06A 0%, #D4AF37 100%);
            box-shadow: 0 6px 24px rgba(212, 175, 55, 0.55);
            transform: translateY(-2px);
        }
        .btn-gold:active {
            transform: scale(0.96);
        }

        /* Polaroid Memory Cards Styling */
        .polaroid-card {
            background: #FFFDF7;
            color: #260209;
            padding: 12px 12px 20px 12px;
            box-shadow: 0 12px 30px rgba(0,0,0,0.55), 0 0 12px rgba(212,175,55,0.2);
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
        }
        .polaroid-card:hover {
            transform: scale(1.05) rotate(0deg) !important;
            z-index: 20;
            box-shadow: 0 20px 40px rgba(212,175,55,0.45);
        }
        .polaroid-tape {
            position: absolute;
            top: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 75px;
            height: 22px;
            background: rgba(255, 255, 255, 0.5);
            border: 1px solid rgba(212, 175, 55, 0.35);
            backdrop-filter: blur(3px);
            z-index: 10;
        }

        /* 3D Wax Seal Envelope */
        .envelope-wrapper {
            perspective: 1000px;
            width: 100%;
            display: flex;
            justify-content: center;
        }

        .envelope {
            position: relative;
            width: 320px;
            height: 210px;
            background: #3D040F;
            border-radius: 16px;
            box-shadow: 0 20px 45px rgba(0, 0, 0, 0.85), 0 0 30px rgba(212, 175, 55, 0.25);
            border: 1.5px solid #D4AF37;
            cursor: pointer;
            transition: transform 0.4s ease;
            margin: 0 auto;
        }

        @media (max-width: 400px) {
            .envelope {
                width: 280px;
                height: 185px;
            }
        }

        .envelope-flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 0;
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            border-top: 120px solid #5C061C;
            transform-origin: top;
            transition: transform 0.5s 0.2s ease-in-out, z-index 0.2s 0.2s;
            z-index: 5;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.5));
        }

        @media (max-width: 400px) {
            .envelope-flap {
                border-left-width: 140px;
                border-right-width: 140px;
                border-top-width: 105px;
            }
        }

        .envelope.open .envelope-flap {
            transform: rotateX(180deg);
            z-index: 1;
            transition: transform 0.5s ease-in-out, z-index 0.1s 0.2s;
        }

        .envelope-pocket {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #3D040F 0%, #260209 100%);
            clip-path: polygon(0 0, 50% 50%, 100% 0, 100% 100%, 0 100%);
            z-index: 3;
            border-bottom-left-radius: 14px;
            border-bottom-right-radius: 14px;
        }

        .wax-seal {
            position: absolute;
            top: 108px;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 56px;
            height: 56px;
            background: radial-gradient(circle, #D4AF37 0%, #8C6C11 100%);
            border-radius: 50%;
            box-shadow: 0 4px 14px rgba(0,0,0,0.8), inset 0 2px 4px rgba(255,255,255,0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 6;
            transition: all 0.4s ease;
            border: 2px solid #FFF9E5;
        }

        @media (max-width: 400px) {
            .wax-seal {
                top: 95px;
                width: 48px;
                height: 48px;
            }
        }

        .envelope.open .wax-seal {
            opacity: 0;
            transform: translate(-50%, -50%) scale(1.5);
            pointer-events: none;
        }

        .letter-preview {
            position: absolute;
            bottom: 12px;
            left: 5%;
            width: 90%;
            height: 82%;
            background: #FFFDF7;
            border-radius: 10px;
            padding: 14px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.35);
            z-index: 2;
            transition: transform 0.6s 0.4s cubic-bezier(0.34, 1.4, 0.64, 1);
            color: #260209;
            border: 1px solid #D4AF37;
        }

        .envelope.open .letter-preview {
            transform: translateY(-110px) scale(1.05);
            z-index: 4;
        }

        /* Pulse Animations */
        @keyframes goldPulse {
            0%, 100% { box-shadow: 0 0 12px rgba(212, 175, 55, 0.3); }
            50% { box-shadow: 0 0 28px rgba(212, 175, 55, 0.75); }
        }
        .glow-pulse { animation: goldPulse 2.5s infinite ease-in-out; }

        .no-scrollbar::-webkit-scrollbar { display: none; }
        .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }

        .break-words-custom {
            overflow-wrap: anywhere;
            word-break: break-word;
        }
    </style>
</head>
<body class="bg-burgundy-950 font-sans antialiased min-h-dvh flex flex-col justify-between relative overflow-x-hidden">

    <!-- 60fps Canvas Background (Falling Petals & Gold Dust Particles) -->
    <canvas id="bgCanvas" class="fixed inset-0 pointer-events-none z-0 w-full h-full"></canvas>

    <!-- HEADER / NAVIGATION BAR -->
    <header class="w-full bg-burgundy-900/90 backdrop-blur-md border-b border-gold-400/30 px-4 py-3 z-40 sticky top-0 shadow-lg">
        <div class="max-w-6xl mx-auto flex items-center justify-between">
            
            <!-- Branding -->
            <div class="flex items-center gap-3">
                <div class="w-9 h-9 rounded-full bg-gradient-to-tr from-gold-500 to-gold-300 text-burgundy-950 font-serif font-bold text-sm flex items-center justify-center shadow-md shrink-0">
                    20
                </div>
                <div>
                    <h1 class="font-serif text-base sm:text-lg font-bold text-gold-gradient leading-tight">Gửi Quỳnh Giang</h1>
                    <p class="text-[10px] sm:text-xs text-rosegold-light tracking-wide uppercase font-medium">Người Bạn Thanh Xuân • 20 Tháng 10</p>
                </div>
            </div>

            <!-- Global Action Controls -->
            <div class="flex items-center gap-2 sm:gap-3">
                <button onclick="toggleAudio()" id="globalAudioBtn" class="px-3 py-1.5 rounded-full bg-burgundy-800 border border-gold-400/40 text-gold-300 flex items-center gap-2 text-xs font-medium hover:bg-burgundy-700 active:scale-95 transition-all shadow-md">
                    <i id="globalAudioIcon" class="fa-solid fa-music"></i>
                    <span id="globalAudioLabel" class="hidden sm:inline">Nhạc Piano</span>
                </button>
                <button onclick="triggerFireworks()" class="btn-gold px-3.5 py-1.5 rounded-full text-xs font-bold flex items-center gap-1.5 shadow-md">
                    <i class="fa-solid fa-sparkles"></i>
                    <span class="hidden sm:inline">Bắn Pháo Hoa</span>
                </button>
            </div>

        </div>
    </header>

    <!-- MAIN CONTENT CONTAINER -->
    <main class="w-full max-w-6xl mx-auto px-4 py-6 sm:py-10 space-y-10 sm:space-y-14 z-10 flex-1">

        <!-- 1. HERO SECTION -->
        <section class="glass-card rounded-3xl p-6 sm:p-10 text-center relative overflow-hidden border border-gold-400/35">
            <div class="absolute -top-20 -right-20 w-56 h-56 bg-gold-400/10 rounded-full blur-3xl pointer-events-none"></div>
            <div class="absolute -bottom-20 -left-20 w-56 h-56 bg-rose-500/10 rounded-full blur-3xl pointer-events-none"></div>

            <span class="inline-flex items-center gap-1.5 px-4 py-1.5 rounded-full bg-gold-400/15 border border-gold-400/35 text-gold-300 text-xs font-semibold tracking-wider uppercase mb-4">
                <i class="fa-solid fa-sparkles text-gold-400"></i> TÔN VINH NGƯỜI BẠN THANH XUÂN
            </span>

            <h2 class="font-serif text-3xl sm:text-5xl lg:text-6xl font-extrabold text-gold-gradient leading-tight mb-4 break-words-custom">
                Thanh Xuân Rực Rỡ & Nụ Cười Quỳnh Giang
            </h2>

            <p class="text-sm sm:text-base lg:text-lg text-slate-200 max-w-3xl mx-auto font-light leading-relaxed mb-8 break-words-custom">
                Cảm ơn <strong class="text-gold-300 font-semibold">Quỳnh Giang</strong> vì đã luôn là một mảnh ghép dịu dàng, chân thành và tỏa sáng rạng rỡ trong những năm tháng đẹp nhất của tuổi trẻ!
            </p>

            <div class="flex flex-wrap items-center justify-center gap-4">
                <button onclick="scrollToSection('section-wishes')" class="btn-gold px-6 py-3 rounded-2xl font-bold text-xs sm:text-sm flex items-center gap-2 glow-pulse">
                    <i class="fa-solid fa-pen-nib"></i>
                    <span>LỜI CHÚC DÀNH TẶNG QUỲNH GIANG</span>
                </button>
                <button onclick="scrollToSection('section-envelope')" class="px-6 py-3 rounded-2xl bg-burgundy-900 border border-gold-400/40 text-gold-200 text-xs sm:text-sm font-semibold hover:bg-burgundy-800 transition-colors flex items-center gap-2">
                    <i class="fa-solid fa-envelope-open-text"></i>
                    <span>MỞ THƯ SÁP 3D</span>
                </button>
            </div>
        </section>

        <!-- 2. POLAROID MEMORY GALLERY -->
        <section class="space-y-6">
            <div class="text-center">
                <h3 class="font-serif text-2xl sm:text-3xl font-bold text-gold-gradient flex items-center justify-center gap-2">
                    <i class="fa-solid fa-camera-retro text-gold-400"></i>
                    <span>Thanh Xuân Ký Ức Cùng Quỳnh Giang</span>
                </h3>
                <p class="text-xs sm:text-sm text-slate-300 mt-1.5 font-light">Những góc nhỏ lưu giữ khoảnh khắc hồn nhiên, tươi đẹp và ấm áp</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 pt-4">
                <div class="polaroid-card rounded-2xl -rotate-2">
                    <div class="polaroid-tape"></div>
                    <div class="w-full h-44 sm:h-48 bg-gradient-to-tr from-amber-200 via-rose-200 to-gold-200 rounded-xl flex flex-col items-center justify-center text-burgundy-900 p-4 text-center relative overflow-hidden">
                        <i class="fa-solid fa-graduation-cap text-burgundy-800/20 text-6xl absolute"></i>
                        <span class="font-handwriting font-bold text-2xl text-burgundy-900 z-10">Nụ Cười Rạng Rỡ</span>
                        <span class="text-[11px] text-burgundy-800/80 z-10 mt-1 font-sans">Góc sân trường ngày ấy</span>
                    </div>
                    <p class="font-handwriting text-center text-base text-burgundy-950 font-bold mt-3">
                        Tuổi trẻ rực rỡ nắng vàng ✨
                    </p>
                </div>

                <div class="polaroid-card rounded-2xl rotate-2">
                    <div class="polaroid-tape"></div>
                    <div class="w-full h-44 sm:h-48 bg-gradient-to-tr from-rose-200 via-pink-200 to-gold-200 rounded-xl flex flex-col items-center justify-center text-burgundy-900 p-4 text-center relative overflow-hidden">
                        <i class="fa-solid fa-mug-hot text-burgundy-800/20 text-6xl absolute"></i>
                        <span class="font-handwriting font-bold text-2xl text-burgundy-900 z-10">Trà Chiều Kỷ Niệm</span>
                        <span class="text-[11px] text-burgundy-800/80 z-10 mt-1 font-sans">Những câu chuyện dài</span>
                    </div>
                    <p class="font-handwriting text-center text-base text-burgundy-950 font-bold mt-3">
                        Sự lắng nghe ấm áp ❤️
                    </p>
                </div>

                <div class="polaroid-card rounded-2xl -rotate-1">
                    <div class="polaroid-tape"></div>
                    <div class="w-full h-44 sm:h-48 bg-gradient-to-tr from-gold-200 via-amber-200 to-yellow-300 rounded-xl flex flex-col items-center justify-center text-burgundy-900 p-4 text-center relative overflow-hidden">
                        <i class="fa-solid fa-sun text-burgundy-800/20 text-6xl absolute"></i>
                        <span class="font-handwriting font-bold text-2xl text-burgundy-900 z-10">Tỏa Sáng Tích Cực</span>
                        <span class="text-[11px] text-burgundy-800/80 z-10 mt-1 font-sans">Năng lượng yêu thương</span>
                    </div>
                    <p class="font-handwriting text-center text-base text-burgundy-950 font-bold mt-3">
                        Quỳnh Giang luôn tỏa sáng 🌟
                    </p>
                </div>

                <div class="polaroid-card rounded-2xl rotate-3">
                    <div class="polaroid-tape"></div>
                    <div class="w-full h-44 sm:h-48 bg-gradient-to-tr from-pink-200 via-rose-300 to-gold-200 rounded-xl flex flex-col items-center justify-center text-burgundy-900 p-4 text-center relative overflow-hidden">
                        <i class="fa-solid fa-heart text-burgundy-800/20 text-6xl absolute"></i>
                        <span class="font-handwriting font-bold text-2xl text-burgundy-900 z-10">Tri Kỷ Mãi Mãi</span>
                        <span class="text-[11px] text-burgundy-800/80 z-10 mt-1 font-sans">Gắn kết bền lâu</span>
                    </div>
                    <p class="font-handwriting text-center text-base text-burgundy-950 font-bold mt-3">
                        Thanh xuân có bạn tuyệt nhất! 💖
                    </p>
                </div>
            </div>
        </section>

        <!-- 3. TYPEWRITER WISH GENERATOR & TOPICS -->
        <section id="section-wishes" class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">
            <div class="lg:col-span-5 space-y-4">
                <div class="glass-card rounded-2xl p-5 sm:p-6 border border-gold-400/30 space-y-5">
                    <div class="border-b border-gold-400/20 pb-3">
                        <h3 class="font-serif text-lg font-bold text-gold-gradient flex items-center gap-2">
                            <i class="fa-solid fa-heart text-gold-400"></i>
                            <span>Chủ Đề Lời Chúc Thanh Xuân</span>
                        </h3>
                        <p class="text-xs text-slate-300 mt-1 font-light">Chọn cảm xúc muốn gửi gắm tới Quỳnh Giang</p>
                    </div>

                    <div class="grid grid-cols-2 gap-2.5">
                        <button onclick="selectCategory('youth')" id="btn-cat-youth" class="cat-pill active p-3 rounded-xl border border-gold-400/40 text-xs font-semibold flex items-center gap-2.5 transition-all text-left">
                            <div class="w-7 h-7 rounded-full bg-amber-400/20 text-amber-300 flex items-center justify-center text-xs shrink-0"><i class="fa-solid fa-sparkles"></i></div>
                            <span class="truncate">✨ Tuổi Trẻ Tươi Đẹp</span>
                        </button>

                        <button onclick="selectCategory('kindred')" id="btn-cat-kindred" class="cat-pill p-3 rounded-xl border border-gold-400/20 text-slate-300 text-xs font-medium flex items-center gap-2.5 transition-all text-left">
                            <div class="w-7 h-7 rounded-full bg-rose-500/20 text-rose-300 flex items-center justify-center text-xs shrink-0"><i class="fa-solid fa-hand-holding-heart"></i></div>
                            <span class="truncate">❤️ Tri Kỷ Chân Thành</span>
                        </button>

                        <button onclick="selectCategory('brilliant')" id="btn-cat-brilliant" class="cat-pill p-3 rounded-xl border border-gold-400/20 text-slate-300 text-xs font-medium flex items-center gap-2.5 transition-all text-left">
                            <div class="w-7 h-7 rounded-full bg-yellow-400/20 text-yellow-300 flex items-center justify-center text-xs shrink-0"><i class="fa-solid fa-sun"></i></div>
                            <span class="truncate">🌟 Tỏa Sáng Rạng Rỡ</span>
                        </button>

                        <button onclick="selectCategory('growth')" id="btn-cat-growth" class="cat-pill p-3 rounded-xl border border-gold-400/20 text-slate-300 text-xs font-medium flex items-center gap-2.5 transition-all text-left">
                            <div class="w-7 h-7 rounded-full bg-purple-400/20 text-purple-300 flex items-center justify-center text-xs shrink-0"><i class="fa-solid fa-gem"></i></div>
                            <span class="truncate">💎 Bình An & Thành Công</span>
                        </button>
                    </div>

                    <div class="space-y-2 pt-3 border-t border-gold-400/20">
                        <label for="recipientInput" class="block text-xs font-bold text-gold-300 uppercase tracking-wider">
                            <i class="fa-solid fa-user-pen mr-1"></i> Tên người nhận
                        </label>
                        <div class="relative">
                            <input type="text" id="recipientInput" value="Quỳnh Giang" 
                                class="w-full bg-burgundy-900/90 border border-gold-400/40 rounded-xl px-4 py-2.5 text-slate-100 font-semibold focus:outline-none focus:border-gold-300 text-sm pr-9"
                                placeholder="Nhập tên người nhận...">
                            <button onclick="clearRecipientInput()" class="absolute right-3 top-1/2 -translate-y-1/2 text-slate-400 hover:text-slate-200 text-xs p-1">
                                <i class="fa-solid fa-xmark"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <div class="lg:col-span-7 space-y-4">
                <div class="glass-card rounded-2xl p-6 sm:p-7 border border-gold-400/35 relative min-h-[280px] flex flex-col justify-between">
                    <div class="flex items-center justify-between border-b border-gold-400/20 pb-3 mb-3">
                        <span class="text-xs font-bold text-gold-gradient uppercase tracking-wider flex items-center gap-2">
                            <i class="fa-solid fa-quote-left text-gold-400"></i> Lời Chúc Gõ Chữ Tự Động
                        </span>
                        <span id="categoryTagLabel" class="px-3 py-1 rounded-full bg-gold-400/15 border border-gold-400/30 text-xs font-bold text-gold-300">
                            Tuổi Trẻ Tươi Đẹp
                        </span>
                    </div>

                    <div id="typewriterWishOutput" class="text-slate-100 text-sm sm:text-base leading-relaxed font-sans my-3 min-h-[130px] break-words-custom relative z-10"></div>

                    <div class="pt-4 border-t border-gold-400/20 flex flex-wrap items-center justify-between gap-3 relative z-10">
                        <button onclick="retypeWish()" class="px-3.5 py-2 rounded-xl bg-burgundy-900 border border-gold-400/35 text-gold-300 text-xs font-semibold hover:bg-burgundy-800 active:scale-95 transition-all flex items-center gap-2">
                            <i class="fa-solid fa-rotate-right"></i>
                            <span>Gõ Lại Lời Chúc</span>
                        </button>

                        <div class="flex items-center gap-2.5 ml-auto">
                            <button onclick="copyWishText()" class="px-4 py-2 rounded-xl bg-burgundy-800 text-gold-200 border border-gold-400/35 text-xs font-semibold hover:bg-burgundy-700 active:scale-95 transition-all flex items-center gap-2">
                                <i class="fa-solid fa-copy"></i>
                                <span>Sao Chép</span>
                            </button>
                            <button onclick="shareViaZaloMessenger()" class="btn-gold px-4 py-2 rounded-xl text-burgundy-950 font-bold text-xs flex items-center gap-2 shadow-md">
                                <i class="fa-solid fa-paper-plane"></i>
                                <span>Gửi Zalo / Messenger</span>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 4. 3D WAX SEAL ENVELOPE SECTION -->
        <section id="section-envelope" class="glass-card rounded-3xl p-6 sm:p-10 border border-gold-400/35 space-y-8 text-center">
            <div class="max-w-2xl mx-auto space-y-2">
                <span class="px-3.5 py-1 rounded-full bg-gold-400/15 border border-gold-400/30 text-gold-300 text-xs font-bold uppercase tracking-wider inline-block">
                    <i class="fa-solid fa-envelope-open mr-1"></i> THÔNG ĐIỆP BẢO MẬT
                </span>
                <h3 class="font-serif text-2xl sm:text-4xl font-bold text-gold-gradient">
                    Bức Thư Hoàng Gia Gửi Quỳnh Giang
                </h3>
                <p class="text-xs sm:text-sm text-slate-300 font-light">Chạm vào con dấu sáp vàng 20/10 để mở thông điệp viết riêng từ trái tim</p>
            </div>

            <div class="py-4 flex justify-center items-center">
                <div class="envelope-wrapper">
                    <div id="envelope3D" onclick="handleEnvelopeTap()" class="envelope">
                        <div class="envelope-flap"></div>
                        
                        <div class="wax-seal">
                            <span class="font-serif font-extrabold text-xs text-burgundy-950 tracking-tighter">20/10</span>
                        </div>

                        <div class="letter-preview flex flex-col justify-center text-center">
                            <h4 class="font-serif text-xs sm:text-sm font-bold text-burgundy-900 mb-1 truncate">
                                Gửi <span id="envNamePreview" class="underline text-burgundy-950">Quỳnh Giang</span>
                            </h4>
                            <p class="font-handwriting text-xs sm:text-sm text-burgundy-800 leading-tight break-words-custom">
                                "Chúc Quỳnh Giang một đời bình an, rạng rỡ tỏa sáng và mãi tràn ngập hạnh phúc!"
                            </p>
                            <div class="mt-2 pt-1 border-t border-gold-400/40 text-[10px] font-serif text-gold-700 italic">
                                Chạm để mở bức thư ✨
                            </div>
                        </div>

                        <div class="envelope-pocket"></div>
                    </div>
                </div>
            </div>

            <div class="pt-2 max-w-sm mx-auto">
                <button onclick="handleEnvelopeTap(true)" class="btn-gold w-full py-3.5 rounded-2xl font-bold text-burgundy-950 text-xs sm:text-sm shadow-xl flex items-center justify-center gap-2">
                    <i class="fa-solid fa-envelope-open"></i>
                    <span>MỞ THƯ & NỔ PHÁO HOA CÁNH HOA</span>
                </button>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="w-full border-t border-gold-400/20 py-8 px-4 text-center space-y-2 relative z-10 bg-burgundy-950/80">
        <p class="font-serif text-sm sm:text-base font-bold text-gold-gradient">
            Tôn Vinh Ngày Phụ Nữ Việt Nam 20/10 • Dành Tặng Quỳnh Giang
        </p>
        <p class="text-xs text-slate-400 font-light max-w-md mx-auto">
            Trân trọng và thương gửi người bạn thanh xuân tuyệt vời! Mãi mãi rạng rỡ và tràn ngập niềm vui ❤️
        </p>
    </footer>

    <!-- FULL-SCREEN LETTER MODAL -->
    <div id="letterModal" class="fixed inset-0 z-50 bg-burgundy-950/85 backdrop-blur-md flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        <div class="glass-card max-w-lg w-full rounded-3xl p-6 sm:p-8 border border-gold-400/40 relative shadow-2xl max-h-[90vh] flex flex-col justify-between">
            
            <button onclick="closeModal()" class="absolute top-4 right-4 w-9 h-9 rounded-full bg-burgundy-900 border border-gold-400/35 text-gold-300 flex items-center justify-center text-sm hover:bg-burgundy-800 transition-colors">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <div class="text-center space-y-4 overflow-y-auto pt-2 no-scrollbar">
                <div class="w-16 h-16 rounded-full bg-gold-400/20 border border-gold-400/40 flex items-center justify-center text-gold-300 mx-auto text-2xl shadow-inner">
                    <i class="fa-solid fa-envelope-open-text"></i>
                </div>

                <h3 class="font-serif text-2xl sm:text-3xl font-bold text-gold-gradient">Thư Gửi Quỳnh Giang</h3>
                
                <div class="bg-burgundy-900/80 rounded-2xl p-5 sm:p-6 border border-gold-400/25 text-left space-y-3.5 text-slate-100 text-xs sm:text-sm leading-relaxed">
                    <p class="font-serif text-base text-gold-300 font-semibold">
                        Gửi <span id="modalRecipientTitle" class="underline text-white">Quỳnh Giang</span> - Người bạn thanh xuân thân yêu,
                    </p>
                    <p>
                        Nhân ngày Phụ nữ Việt Nam 20/10, mình muốn gửi tới Quỳnh Giang những lời chúc chân thành, ấm áp và trân trọng nhất từ đáy lòng.
                    </p>
                    <p>
                        Cảm ơn Quỳnh Giang vì đã luôn xuất hiện dịu dàng, nồng ấm và đem lại biết bao nụ cười, nguồn năng lượng tích cực cho những năm tháng thanh xuân của chúng mình. Cảm ơn sự chân thành, bao dung và sự đồng hành quý giá của Quỳnh Giang.
                    </p>
                    <p>
                        Chúc Quỳnh Giang luôn xinh đẹp, bình an trong tâm hồn, kiên định với những mục tiêu của bản thân và gặt hái thêm muôn vàn thành công rực rỡ!
                    </p>
                    <p class="text-right font-handwriting text-2xl text-rosegold-light pt-2">
                        Trân trọng & Yêu thương rất nhiều!
                    </p>
                </div>
            </div>

            <div class="pt-5 flex items-center gap-3">
                <button onclick="shareViaZaloMessenger(); closeModal();" class="btn-gold w-full py-3.5 rounded-xl font-bold text-burgundy-950 text-xs sm:text-sm shadow-lg flex items-center justify-center gap-2">
                    <i class="fa-solid fa-paper-plane"></i>
                    <span>Chia Sẻ Lời Chúc Tới Quỳnh Giang</span>
                </button>
            </div>
        </div>
    </div>

    <!-- TOAST NOTIFICATION -->
    <div id="toast" class="fixed top-16 left-1/2 -translate-x-1/2 z-50 bg-burgundy-900 border border-gold-400/50 text-gold-200 px-5 py-2.5 rounded-full shadow-2xl flex items-center gap-2.5 transition-all duration-300 transform -translate-y-10 opacity-0 text-xs sm:text-sm font-medium whitespace-nowrap pointer-events-none">
        <i class="fa-solid fa-circle-check text-gold-400"></i>
        <span id="toastMsg">Đã sao chép thành công!</span>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        let currentCategory = 'youth';
        let audioCtx = null;
        let isAudioPlaying = false;
        let audioTimer = null;
        let typingTimer = null;

        const wishesDB = {
            youth: "Gửi {NAME} - Mảnh ghép thanh xuân tuyệt vời!\n\nNhân ngày 20/10, chúc {NAME} luôn giữ trọn nụ cười hồn nhiên, trái tim ấm áp và sự tự tin rạng rỡ. Mong rằng mọi ước mơ và dự định của {NAME} đều sẽ cập bến thành công rực rỡ!",
            kindred: "{NAME} thân yêu!\n\nCảm ơn {NAME} vì đã luôn là người bạn tri kỷ tuyệt vời, luôn lắng nghe và đồng hành cùng mình qua bao kỷ niệm. Chúc {NAME} ngày 20/10 ngập tràn hoa tươi, quà đẹp và những niềm vui ngọt ngào nhất!",
            brilliant: "Chúc {NAME} ngày 20/10 thật rực rỡ và tỏa sáng!\n\nHãy luôn kiên định, tự tin bước đi trên con đường mình đã chọn nhé. {NAME} luôn là một phiên bản tuyệt vời, ấm áp và vô cùng đặc biệt!",
            growth: "Gửi {NAME} yêu quý!\n\nDù thời gian trôi qua và chúng mình ngày càng trưởng thành, bận rộn hơn, chúc {NAME} luôn giữ được sự bình an trong tâm hồn, luôn hạnh phúc và gặt hái thêm muôn vàn thành công mới!"
        };

        const categoryNames = {
            youth: "Tuổi Trẻ Tươi Đẹp",
            kindred: "Tri Kỷ Chân Thành",
            brilliant: "Tỏa Sáng Rạng Rỡ",
            growth: "Bình An & Thành Công"
        };

        function selectCategory(cat) {
            currentCategory = cat;
            document.querySelectorAll('.cat-pill').forEach(btn => {
                btn.classList.remove('active', 'border-gold-400/40', 'font-semibold');
                btn.classList.add('border-gold-400/20', 'text-slate-300');
            });

            const activePill = document.getElementById(`btn-cat-${cat}`);
            if (activePill) {
                activePill.classList.add('active', 'border-gold-400/40', 'font-semibold');
                activePill.classList.remove('text-slate-300');
            }

            document.getElementById('categoryTagLabel').innerText = categoryNames[cat] || "Lời Chúc 20/10";
            updateWishText();
        }

        function getRecipientName() {
            const input = document.getElementById('recipientInput').value.trim();
            return input || 'Quỳnh Giang';
        }

        function clearRecipientInput() {
            document.getElementById('recipientInput').value = '';
            updateWishText();
        }

        function syncRecipientUI() {
            const name = getRecipientName();
            document.getElementById('envNamePreview').innerText = name;
            document.getElementById('modalRecipientTitle').innerText = name;
        }

        function typeWriter(text) {
            const output = document.getElementById('typewriterWishOutput');
            output.innerHTML = '';
            let i = 0;

            if (typingTimer) clearTimeout(typingTimer);

            function step() {
                if (i < text.length) {
                    const char = text.charAt(i);
                    output.innerHTML += (char === '\n') ? '<br/>' : char;
                    i++;
                    typingTimer = setTimeout(step, 18);
                }
            }
            step();
        }

        function updateWishText() {
            syncRecipientUI();
            const name = getRecipientName();
            const template = wishesDB[currentCategory];
            const formatted = template.replace(/{NAME}/g, name);
            typeWriter(formatted);
        }

        function retypeWish() {
            updateWishText();
        }

        document.getElementById('recipientInput').addEventListener('input', () => {
            updateWishText();
        });

        function handleEnvelopeTap(forceOpen = false) {
            const env = document.getElementById('envelope3D');
            if (forceOpen || !env.classList.contains('open')) {
                env.classList.add('open');
                playChimeSound();
                triggerFireworks();
                setTimeout(() => {
                    openModal();
                }, 1100);
            } else {
                env.classList.remove('open');
            }
        }

        function openModal() {
            syncRecipientUI();
            const modal = document.getElementById('letterModal');
            modal.classList.remove('opacity-0', 'pointer-events-none');
            modal.classList.add('opacity-100');
        }

        function closeModal() {
            const modal = document.getElementById('letterModal');
            modal.classList.remove('opacity-100');
            modal.classList.add('opacity-0', 'pointer-events-none');
        }

        function scrollToSection(id) {
            const el = document.getElementById(id);
            if (el) el.scrollIntoView({ behavior: 'smooth' });
        }

        function initAudio() {
            if (!audioCtx) {
                const AudioCtx = window.AudioContext || window.webkitAudioContext;
                audioCtx = new AudioCtx();
            }
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }
        }

        function playNote(freq, delay, duration = 3) {
            if (!audioCtx) return;
            const now = audioCtx.currentTime + delay;
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();

            osc.type = 'sine';
            osc.frequency.setValueAtTime(freq, now);

            gain.gain.setValueAtTime(0, now);
            gain.gain.linearRampToValueAtTime(0.12, now + 0.04);
            gain.gain.exponentialRampToValueAtTime(0.0001, now + duration);

            osc.connect(gain);
            gain.connect(audioCtx.destination);

            osc.start(now);
            osc.stop(now + duration);
        }

        function playChimeSound() {
            initAudio();
            const notes = [523.25, 659.25, 783.99, 1046.50];
            notes.forEach((f, idx) => playNote(f, idx * 0.08, 1.8));
        }

        function playAmbientLoop() {
            const chords = [
                [261.63, 329.63, 392.00],
                [220.00, 261.63, 329.63],
                [174.61, 220.00, 261.63],
                [196.00, 246.94, 293.66]
            ];
            let step = 0;

            function next() {
                if (!isAudioPlaying) return;
                chords[step % chords.length].forEach((f, i) => playNote(f, i * 0.28, 3.2));
                step++;
                audioTimer = setTimeout(next, 2500);
            }
            next();
        }

        function toggleAudio() {
            initAudio();
            const icon = document.getElementById('globalAudioIcon');
            const label = document.getElementById('globalAudioLabel');

            if (!isAudioPlaying) {
                isAudioPlaying = true;
                playAmbientLoop();
                if (icon) icon.className = 'fa-solid fa-compact-disc animate-spin text-gold-300';
                if (label) label.innerText = 'Đang Phát...';
                showToast('Đã bật nhạc nền piano du dương!');
            } else {
                isAudioPlaying = false;
                if (audioTimer) clearTimeout(audioTimer);
                if (icon) icon.className = 'fa-solid fa-music';
                if (label) label.innerText = 'Nhạc Piano';
                showToast('Đã tắt nhạc nền.');
            }
        }

        const canvas = document.getElementById('bgCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Petal {
            constructor() {
                this.reset();
            }
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = -20;
                this.size = Math.random() * 6 + 3;
                this.speedY = Math.random() * 1.2 + 0.5;
                this.speedX = Math.random() * 0.6 - 0.3;
                this.opacity = Math.random() * 0.6 + 0.3;
                this.isGold = Math.random() > 0.65;
            }
            update() {
                this.y += this.speedY;
                this.x += Math.sin(this.y * 0.012) + this.speedX;
                if (this.y > canvas.height + 20) this.reset();
            }
            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.globalAlpha = this.opacity;
                ctx.fillStyle = this.isGold ? '#D4AF37' : '#E8B4B8';
                ctx.beginPath();
                ctx.arc(0, 0, this.size * 0.45, 0, Math.PI * 2);
                ctx.fill();
                ctx.restore();
            }
        }

        function initParticles() {
            particles = [];
            for (let i = 0; i < 40; i++) {
                const p = new Petal();
                p.y = Math.random() * canvas.height;
                particles.push(p);
            }
        }
        initParticles();

        function renderParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(renderParticles);
        }
        renderParticles();

        function triggerFireworks() {
            if (typeof confetti === 'function') {
                confetti({
                    particleCount: 75,
                    spread: 85,
                    origin: { y: 0.65 },
                    colors: ['#D4AF37', '#E8B4B8', '#FF1493', '#FFFFFF']
                });
            }
        }

        function shareViaZaloMessenger() {
            const name = getRecipientName();
            const wish = document.getElementById('typewriterWishOutput').innerText;
            const fullMsg = `✨ Lời Chúc 20/10 Dành Tặng ${name}:\n\n"${wish}"\n\nChúc mừng Ngày Phụ nữ Việt Nam 20/10! 🌹`;

            copyToClipboard(fullMsg, 'Đã sao chép lời chúc! Hãy dán gửi qua Zalo/Messenger.');
        }

        function copyWishText() {
            const wish = document.getElementById('typewriterWishOutput').innerText;
            copyToClipboard(wish, 'Đã sao chép lời chúc!');
        }

        function copyToClipboard(text, msg) {
            if (navigator.clipboard && window.isSecureContext) {
                navigator.clipboard.writeText(text).then(() => showToast(msg)).catch(() => fallbackCopy(text, msg));
            } else {
                fallbackCopy(text, msg);
            }
        }

        function fallbackCopy(text, msg) {
            const ta = document.createElement('textarea');
            ta.value = text;
            document.body.appendChild(ta);
            ta.select();
            try {
                document.execCommand('copy');
                showToast(msg);
            } catch (e) {
                showToast('Không thể tự động sao chép.');
            }
            document.body.removeChild(ta);
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toastMsg').innerText = msg;
            toast.classList.remove('-translate-y-10', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('-translate-y-10', 'opacity-0');
            }, 2800);
        }

        selectCategory('youth');
        window.addEventListener('touchstart', () => initAudio(), { once: true });
        window.addEventListener('click', () => initAudio(), { once: true });
    </script>
</body>
</html>
