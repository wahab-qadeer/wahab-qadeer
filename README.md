<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wahab Qadeer | BS AI Portfolio @ BIIT</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        heading: ['"Space Grotesk"', 'sans-serif'],
                        body: ['Inter', 'sans-serif'],
                        code: ['"Fira Code"', 'monospace'],
                    },
                    colors: {
                        obsidian: {
                            900: '#06090e',
                            800: '#0a0f18',
                            700: '#0f172a',
                            600: '#1e293b'
                        },
                        neon: {
                            cyan: '#00f2fe',
                            purple: '#8b5cf6',
                            emerald: '#10b981',
                            pink: '#ec4899',
                            amber: '#f59e0b'
                        }
                    },
                    animation: {
                        'spin-slow': 'spin 10s linear infinite',
                        'float': 'float 5s ease-in-out infinite',
                        'pulse-glow': 'pulseGlow 3s infinite alternate',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-12px)' },
                        },
                        pulseGlow: {
                            '0%': { boxShadow: '0 0 15px rgba(0, 242, 254, 0.2)' },
                            '100%': { boxShadow: '0 0 35px rgba(139, 92, 246, 0.5)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #06090e;
            color: #f1f5f9;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
        }

        h1, h2, h3, h4, .font-heading {
            font-family: 'Space Grotesk', sans-serif;
        }

        /* Neural Canvas Background */
        #neural-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
            pointer-events: none;
        }

        /* Ambient Orbs */
        .ambient-orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(140px);
            z-index: -9;
            opacity: 0.25;
            pointer-events: none;
        }
        .orb-cyan { top: -10%; left: -10%; width: 50vw; height: 50vw; background: #00f2fe; }
        .orb-purple { bottom: -15%; right: -10%; width: 60vw; height: 60vw; background: #8b5cf6; }

        /* Glassmorphism Cards */
        .glass-card {
            background: rgba(15, 23, 42, 0.55);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.07);
            box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.5);
            transition: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-card:hover {
            background: rgba(30, 41, 59, 0.65);
            border-color: rgba(0, 242, 254, 0.25);
            box-shadow: 0 20px 40px -15px rgba(0, 242, 254, 0.15);
            transform: translateY(-4px);
        }

        /* Gradient Text Effects */
        .gradient-text-cyan-purple {
            background: linear-gradient(135deg, #00f2fe 0%, #8b5cf6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gradient-text-emerald {
            background: linear-gradient(135deg, #10b981 0%, #00f2fe 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Profile Ring Avatar */
        .profile-avatar-container {
            position: relative;
            width: 260px;
            height: 260px;
            margin: 0 auto;
            border-radius: 50%;
        }

        .profile-avatar-container::before {
            content: '';
            position: absolute;
            inset: -6px;
            border-radius: 50%;
            background: conic-gradient(from 0deg, #00f2fe, #8b5cf6, #10b981, #00f2fe);
            animation: spin 8s linear infinite;
            filter: blur(10px);
            opacity: 0.8;
        }

        .profile-avatar-container::after {
            content: '';
            position: absolute;
            inset: -3px;
            border-radius: 50%;
            background: conic-gradient(from 0deg, #00f2fe, #8b5cf6, #10b981, #00f2fe);
            animation: spin 8s linear infinite;
            z-index: 1;
        }

        .profile-img-wrap {
            position: relative;
            z-index: 2;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: #0a0f18;
            padding: 5px;
            overflow: hidden;
        }

        .profile-img-wrap img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .profile-avatar-container:hover .profile-img-wrap img {
            transform: scale(1.06);
        }

        /* Scroll Reveal Utility */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #06090e; }
        ::-webkit-scrollbar-thumb { background: #1e293b; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #00f2fe; }

        /* Typing Caret */
        .typing-cursor::after {
            content: '|';
            animation: blink 1s step-end infinite;
            color: #00f2fe;
            margin-left: 2px;
        }

        @keyframes blink {
            from, to { opacity: 1; }
            50% { opacity: 0; }
        }
    </style>
</head>
<body class="selection:bg-neon-cyan selection:text-obsidian-900">

    <canvas id="neural-canvas"></canvas>
    <div class="ambient-orb orb-cyan"></div>
    <div class="ambient-orb orb-purple"></div>

    <header class="fixed top-0 left-0 w-full z-50 transition-all duration-300 px-4 sm:px-8 py-4" id="main-header">
        <div class="max-w-7xl mx-auto">
            <div class="glass-card rounded-2xl px-6 py-3 flex items-center justify-between border border-white/10">
                <!-- Logo -->
                <a href="#" class="font-heading font-bold text-2xl tracking-wider text-white flex items-center gap-2 group">
                    <span class="w-8 h-8 rounded-lg bg-gradient-to-br from-neon-cyan to-neon-purple flex items-center justify-center text-obsidian-900 font-bold text-sm shadow-lg shadow-neon-cyan/20">WQ</span>
                    <span class="group-hover:text-neon-cyan transition-colors">Wahab<span class="text-neon-cyan">.ai</span></span>
                </a>

                <!-- Desktop Nav -->
                <nav class="hidden md:flex items-center space-x-8 text-sm font-medium text-slate-300">
                    <a href="#about" class="hover:text-neon-cyan transition-colors">About</a>
                    <a href="#skills" class="hover:text-neon-cyan transition-colors">Skills</a>
                    <a href="#projects" class="hover:text-neon-cyan transition-colors">Projects</a>
                    <a href="#focus" class="hover:text-neon-cyan transition-colors">AI Focus</a>
                    <a href="#connect" class="hover:text-neon-cyan transition-colors">Connect</a>
                </nav>

                <!-- CTA Button -->
                <a href="#connect" class="px-5 py-2 rounded-xl bg-gradient-to-r from-neon-cyan to-neon-purple text-obsidian-900 font-semibold text-xs uppercase tracking-wider hover:opacity-90 transition-all shadow-md shadow-neon-cyan/20 flex items-center gap-2">
                    <i class="fa-solid fa-paper-plane"></i> Get In Touch
                </a>
            </div>
        </div>
    </header>

    <main class="relative pt-28">

        <section class="min-h-[90vh] flex items-center justify-center px-4 sm:px-6 lg:px-8 py-12 relative">
            <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                
                <!-- Left Content -->
                <div class="lg:col-span-7 space-y-6 text-center lg:text-left reveal">
                    <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full glass-card border-neon-cyan/30 text-neon-cyan text-xs font-code uppercase tracking-wider">
                        <span class="w-2 h-2 rounded-full bg-neon-emerald animate-ping"></span>
                        BS Artificial Intelligence @ BIIT
                    </div>

                    <h1 class="text-4xl sm:text-6xl font-bold tracking-tight text-white leading-tight">
                        Hi, I'm <span class="gradient-text-cyan-purple">Wahab Qadeer</span> 👋
                    </h1>

                    <div class="text-xl sm:text-2xl font-medium text-slate-300 h-10 flex items-center justify-center lg:justify-start">
                        <span id="typing-text" class="typing-cursor font-code text-neon-cyan"></span>
                    </div>

                    <p class="text-slate-400 text-base sm:text-lg leading-relaxed max-w-2xl">
                        Undergraduate Computer Science & Artificial Intelligence student passionate about Machine Learning algorithms, Data Structures, OOP architectures, and automated hardware-software ecosystems.
                    </p>

                    <!-- Quote Card -->
                    <div class="glass-card p-4 rounded-2xl border-l-4 border-l-neon-cyan text-left text-sm text-slate-300 italic relative my-6">
                        <i class="fa-solid fa-quote-left text-neon-cyan/40 text-2xl absolute top-3 left-3"></i>
                        <p class="pl-6">
                            "In a world of infinite data, pattern recognition and artificial intelligence are the ultimate levers of human potential."
                        </p>
                    </div>

                    <!-- CTA Buttons -->
                    <div class="flex flex-wrap justify-center lg:justify-start gap-4 pt-2">
                        <a href="#projects" class="px-7 py-3.5 rounded-xl bg-neon-cyan text-obsidian-900 font-bold text-sm tracking-wide hover:bg-white transition-all shadow-lg shadow-neon-cyan/25 flex items-center gap-2">
                            <i class="fa-solid fa-rocket"></i> Explore Projects
                        </a>
                        <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="px-7 py-3.5 rounded-xl glass-card text-white font-medium text-sm hover:border-neon-purple/50 transition-all flex items-center gap-2">
                            <i class="fa-brands fa-linkedin text-neon-cyan text-base"></i> Connect on LinkedIn
                        </a>
                    </div>
                </div>

                <!-- Right Profile Avatar -->
                <div class="lg:col-span-5 flex justify-center reveal">
                    <div class="profile-avatar-container animate-float">
                        <div class="profile-img-wrap">
                            <img 
                                src="WhatsApp Image 2026-08-13 at 1.09.24 PM_2.jpeg" 
                                alt="Wahab Qadeer" 
                                onerror="this.src='https://placehold.co/400x400/0f172a/00f2fe?text=Wahab+Qadeer+BS(AI)'"
                            >
                        </div>
                    </div>
                </div>

            </div>
        </section>

        <section id="about" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
            <div class="text-center mb-16 reveal">
                <h2 class="text-3xl sm:text-4xl font-bold text-white mb-3">About <span class="gradient-text-cyan-purple">Wahab Qadeer</span></h2>
                <div class="w-20 h-1 bg-gradient-to-r from-neon-cyan to-neon-purple mx-auto rounded-full"></div>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <!-- Bio Card -->
                <div class="lg:col-span-2 glass-card p-8 rounded-3xl relative overflow-hidden reveal">
                    <div class="absolute -right-12 -bottom-12 w-48 h-48 bg-neon-purple/10 rounded-full blur-3xl pointer-events-none"></div>
                    <h3 class="text-2xl font-bold text-white mb-4 flex items-center gap-3">
                        <i class="fa-solid fa-graduation-cap text-neon-cyan"></i> Academic Profile
                    </h3>
                    <p class="text-slate-300 leading-relaxed mb-4">
                        I am currently pursuing my bachelor’s degree in <strong class="text-white">BS Artificial Intelligence (BS AI)</strong> at <strong class="text-white">BIIT (Barani Institute of Information Technology)</strong>. My academic journey combines deep theoretical knowledge with rigorous hands-on programming.
                    </p>
                    <p class="text-slate-400 leading-relaxed mb-6">
                        I thrive at the intersection of logical problem solving, relational database management, object-oriented software engineering, and intelligent hardware automation (Arduino/IoT). My ultimate goal is to architect scalable software and smart AI solutions that solve practical real-world problems.
                    </p>

                    <div class="grid grid-cols-2 sm:grid-cols-3 gap-4 pt-4 border-t border-white/10">
                        <div>
                            <span class="block text-xs text-slate-500 uppercase tracking-wider">Degree</span>
                            <span class="text-sm font-semibold text-neon-cyan">BS (AI) Student</span>
                        </div>
                        <div>
                            <span class="block text-xs text-slate-500 uppercase tracking-wider">Institute</span>
                            <span class="text-sm font-semibold text-white">BIIT</span>
                        </div>
                        <div>
                            <span class="block text-xs text-slate-500 uppercase tracking-wider">Primary Focus</span>
                            <span class="text-sm font-semibold text-neon-purple">Software & AI</span>
                        </div>
                    </div>
                </div>

                <!-- Highlight Cards -->
                <div class="space-y-6 reveal">
                    <div class="glass-card p-6 rounded-2xl border-l-4 border-neon-cyan">
                        <div class="w-10 h-10 rounded-xl bg-neon-cyan/10 flex items-center justify-center text-neon-cyan text-lg mb-3">
                            <i class="fa-solid fa-brain"></i>
                        </div>
                        <h4 class="text-lg font-bold text-white mb-1">AI & Neural Thinking</h4>
                        <p class="text-xs text-slate-400">Applying Machine Learning concepts, data structures, and mathematical logic to create intelligent computational models.</p>
                    </div>

                    <div class="glass-card p-6 rounded-2xl border-l-4 border-neon-purple">
                        <div class="w-10 h-10 rounded-xl bg-neon-purple/10 flex items-center justify-center text-neon-purple text-lg mb-3">
                            <i class="fa-solid fa-code text-lg"></i>
                        </div>
                        <h4 class="text-lg font-bold text-white mb-1">Object-Oriented Mastery</h4>
                        <p class="text-xs text-slate-400">Designing modular, maintainable software systems using standard OOP paradigms in Java and C++.</p>
                    </div>

                    <div class="glass-card p-6 rounded-2xl border-l-4 border-neon-emerald">
                        <div class="w-10 h-10 rounded-xl bg-neon-emerald/10 flex items-center justify-center text-neon-emerald text-lg mb-3">
                            <i class="fa-solid fa-microchip"></i>
                        </div>
                        <h4 class="text-lg font-bold text-white mb-1">Hardware & IoT Synergy</h4>
                        <p class="text-xs text-slate-400">Combining microcontroller circuits (Arduino) with software logic for real-time sensor control systems.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="skills" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
            <div class="text-center mb-16 reveal">
                <h2 class="text-3xl sm:text-4xl font-bold text-white mb-3">Technical <span class="gradient-text-emerald">Skills Matrix</span></h2>
                <p class="text-slate-400 text-sm max-w-xl mx-auto">Core competencies across Computer Science, Artificial Intelligence, Databases, and Software Architecture.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                
                <!-- Category 1: AI & Core CS -->
                <div class="glass-card p-6 rounded-3xl reveal">
                    <div class="flex items-center gap-3 mb-6 pb-4 border-b border-white/10">
                        <div class="w-12 h-12 rounded-2xl bg-neon-cyan/10 flex items-center justify-center text-neon-cyan text-xl">
                            <i class="fa-solid fa-network-wired"></i>
                        </div>
                        <div>
                            <h3 class="text-lg font-bold text-white">AI & Core CS</h3>
                            <span class="text-xs text-slate-400">Fundamental Systems</span>
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Artificial Intelligence</span>
                                <span class="text-neon-cyan">85%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-cyan to-neon-purple h-full rounded-full" style="width: 85%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Machine Learning Fundamentals</span>
                                <span class="text-neon-cyan">80%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-cyan to-neon-purple h-full rounded-full" style="width: 80%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Data Structures & Algorithms</span>
                                <span class="text-neon-cyan">90%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-cyan to-neon-purple h-full rounded-full" style="width: 90%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Computer Networks</span>
                                <span class="text-neon-cyan">82%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-cyan to-neon-purple h-full rounded-full" style="width: 82%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Software Engineering</span>
                                <span class="text-neon-cyan">88%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-cyan to-neon-purple h-full rounded-full" style="width: 88%;"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Category 2: Programming & Logic -->
                <div class="glass-card p-6 rounded-3xl reveal">
                    <div class="flex items-center gap-3 mb-6 pb-4 border-b border-white/10">
                        <div class="w-12 h-12 rounded-2xl bg-neon-purple/10 flex items-center justify-center text-neon-purple text-xl">
                            <i class="fa-solid fa-code"></i>
                        </div>
                        <div>
                            <h3 class="text-lg font-bold text-white">Languages & OOP</h3>
                            <span class="text-xs text-slate-400">Software Development</span>
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Java & OOP</span>
                                <span class="text-neon-purple">92%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-purple to-neon-pink h-full rounded-full" style="width: 92%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">C++ Programming</span>
                                <span class="text-neon-purple">88%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-purple to-neon-pink h-full rounded-full" style="width: 88%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">SQL & Database Queries</span>
                                <span class="text-neon-purple">90%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-purple to-neon-pink h-full rounded-full" style="width: 90%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">HTML5 & CSS3</span>
                                <span class="text-neon-purple">85%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-purple to-neon-pink h-full rounded-full" style="width: 85%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Kotlin (Mobile Dev)</span>
                                <span class="text-neon-amber">In Progress</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-amber to-neon-pink h-full rounded-full" style="width: 60%;"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Category 3: Embedded & Systems -->
                <div class="glass-card p-6 rounded-3xl reveal">
                    <div class="flex items-center gap-3 mb-6 pb-4 border-b border-white/10">
                        <div class="w-12 h-12 rounded-2xl bg-neon-emerald/10 flex items-center justify-center text-neon-emerald text-xl">
                            <i class="fa-solid fa-microchip"></i>
                        </div>
                        <div>
                            <h3 class="text-lg font-bold text-white">Database & Embedded</h3>
                            <span class="text-xs text-slate-400">Hardware & Relational Data</span>
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Database Systems (Relational)</span>
                                <span class="text-neon-emerald">90%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-emerald to-neon-cyan h-full rounded-full" style="width: 90%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Arduino Microcontrollers</span>
                                <span class="text-neon-emerald">85%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-emerald to-neon-cyan h-full rounded-full" style="width: 85%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Digital Logic Design (DLD)</span>
                                <span class="text-neon-emerald">86%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-emerald to-neon-cyan h-full rounded-full" style="width: 86%;"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between text-xs font-medium mb-1">
                                <span class="text-slate-200">Sensor Systems Integration</span>
                                <span class="text-neon-emerald">84%</span>
                            </div>
                            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                                <div class="bg-gradient-to-r from-neon-emerald to-neon-cyan h-full rounded-full" style="width: 84%;"></div>
                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </section>

        <section id="projects" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
            <div class="text-center mb-12 reveal">
                <h2 class="text-3xl sm:text-4xl font-bold text-white mb-3">Featured <span class="gradient-text-cyan-purple">Projects</span></h2>
                <p class="text-slate-400 text-sm max-w-xl mx-auto">Demonstrating practical implementation across Java OOP, SQL, C++, Arduino, and Web tech.</p>
                
                <!-- Filter Buttons -->
                <div class="flex flex-wrap justify-center gap-3 mt-8" id="project-filters">
                    <button class="filter-btn active px-5 py-2 rounded-xl text-xs font-semibold glass-card border-neon-cyan text-neon-cyan transition-all" data-filter="all">All Projects</button>
                    <button class="filter-btn px-5 py-2 rounded-xl text-xs font-semibold glass-card text-slate-300 hover:text-white transition-all" data-filter="software">Software & AI</button>
                    <button class="filter-btn px-5 py-2 rounded-xl text-xs font-semibold glass-card text-slate-300 hover:text-white transition-all" data-filter="hardware">Hardware & IoT</button>
                    <button class="filter-btn px-5 py-2 rounded-xl text-xs font-semibold glass-card text-slate-300 hover:text-white transition-all" data-filter="webdb">Web & DB</button>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" id="projects-grid">
                
                <!-- Project 1 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal" data-category="software">
                    <div>
                        <div class="w-12 h-12 rounded-2xl bg-blue-500/10 border border-blue-500/20 flex items-center justify-center text-blue-400 text-2xl mb-5">
                            <i class="fa-solid fa-hospital"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-2">Smart Hospital Management System</h3>
                        <p class="text-slate-400 text-xs leading-relaxed mb-6">
                            A complete desktop hospital management solution developed in Java using object-oriented principles and JDBC database connectivity for managing patients, doctors, and medical appointments.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 mb-4 font-code text-[11px]">
                            <span class="px-2.5 py-1 rounded-md bg-blue-500/10 text-blue-300 border border-blue-500/20">Java</span>
                            <span class="px-2.5 py-1 rounded-md bg-purple-500/10 text-purple-300 border border-purple-500/20">OOP</span>
                            <span class="px-2.5 py-1 rounded-md bg-emerald-500/10 text-emerald-300 border border-emerald-500/20">SQL</span>
                        </div>
                    </div>
                </div>

                <!-- Project 2 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal" data-category="webdb">
                    <div>
                        <div class="w-12 h-12 rounded-2xl bg-indigo-500/10 border border-indigo-500/20 flex items-center justify-center text-indigo-400 text-2xl mb-5">
                            <i class="fa-solid fa-plane-departure"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-2">Flight Reservation System</h3>
                        <p class="text-slate-400 text-xs leading-relaxed mb-6">
                            A relational database project demonstrating complex SQL schema design, normalized tables, joins, transactions, and indexing to simulate a robust flight booking infrastructure.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 mb-4 font-code text-[11px]">
                            <span class="px-2.5 py-1 rounded-md bg-indigo-500/10 text-indigo-300 border border-indigo-500/20">SQL</span>
                            <span class="px-2.5 py-1 rounded-md bg-blue-500/10 text-blue-300 border border-blue-500/20">Relational DB</span>
                            <span class="px-2.5 py-1 rounded-md bg-purple-500/10 text-purple-300 border border-purple-500/20">DBMS</span>
                        </div>
                    </div>
                </div>

                <!-- Project 3 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal" data-category="hardware">
                    <div>
                        <div class="w-12 h-12 rounded-2xl bg-emerald-500/10 border border-emerald-500/20 flex items-center justify-center text-emerald-400 text-2xl mb-5">
                            <i class="fa-solid fa-seedling"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-2">Smart Irrigation System</h3>
                        <p class="text-slate-400 text-xs leading-relaxed mb-6">
                            A logic-driven automation project implemented in C++ to model smart soil moisture checking, automated water valve triggering, and resource conservation protocols.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 mb-4 font-code text-[11px]">
                            <span class="px-2.5 py-1 rounded-md bg-emerald-500/10 text-emerald-300 border border-emerald-500/20">C++</span>
                            <span class="px-2.5 py-1 rounded-md bg-teal-500/10 text-teal-300 border border-teal-500/20">Logic Design</span>
                            <span class="px-2.5 py-1 rounded-md bg-cyan-500/10 text-cyan-300 border border-cyan-500/20">Automation</span>
                        </div>
                    </div>
                </div>

                <!-- Project 4 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal" data-category="hardware">
                    <div>
                        <div class="w-12 h-12 rounded-2xl bg-red-500/10 border border-red-500/20 flex items-center justify-center text-red-400 text-2xl mb-5">
                            <i class="fa-solid fa-fire-extinguisher"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-2">Smart Auto Fire Brigade</h3>
                        <p class="text-slate-400 text-xs leading-relaxed mb-6">
                            An Arduino-powered embedded project combining flame detection sensors, digital logic control, motor drivers, and automated alarms for immediate fire response.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 mb-4 font-code text-[11px]">
                            <span class="px-2.5 py-1 rounded-md bg-red-500/10 text-red-300 border border-red-500/20">Arduino</span>
                            <span class="px-2.5 py-1 rounded-md bg-amber-500/10 text-amber-300 border border-amber-500/20">DLD</span>
                            <span class="px-2.5 py-1 rounded-md bg-rose-500/10 text-rose-300 border border-rose-500/20">Sensors</span>
                        </div>
                    </div>
                </div>

                <!-- Project 5 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal" data-category="webdb">
                    <div>
                        <div class="w-12 h-12 rounded-2xl bg-cyan-500/10 border border-cyan-500/20 flex items-center justify-center text-cyan-400 text-2xl mb-5">
                            <i class="fa-solid fa-cloud-sun"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-2">Weather Website</h3>
                        <p class="text-slate-400 text-xs leading-relaxed mb-6">
                            A modern, responsive multi-page weather dashboard built with standard HTML5 and CSS3, presenting styled atmospheric forecast components cleanly.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 mb-4 font-code text-[11px]">
                            <span class="px-2.5 py-1 rounded-md bg-cyan-500/10 text-cyan-300 border border-cyan-500/20">HTML</span>
                            <span class="px-2.5 py-1 rounded-md bg-blue-500/10 text-blue-300 border border-blue-500/20">CSS</span>
                            <span class="px-2.5 py-1 rounded-md bg-indigo-500/10 text-indigo-300 border border-indigo-500/20">Responsive UI</span>
                        </div>
                    </div>
                </div>

            </div>
        </section>

        <section id="focus" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
            <div class="glass-card rounded-3xl p-8 sm:p-12 relative overflow-hidden reveal">
                <div class="absolute -left-16 -top-16 w-64 h-64 bg-neon-cyan/10 rounded-full blur-3xl pointer-events-none"></div>
                
                <div class="text-center max-w-2xl mx-auto mb-10">
                    <span class="text-xs font-code text-neon-cyan uppercase tracking-widest block mb-2">Continuous Growth</span>
                    <h2 class="text-3xl font-bold text-white">Currently <span class="gradient-text-cyan-purple">Learning & Expanding</span></h2>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                    <div class="p-5 rounded-2xl bg-slate-900/60 border border-white/5 flex items-start gap-4">
                        <div class="w-10 h-10 rounded-xl bg-neon-cyan/10 flex items-center justify-center text-neon-cyan shrink-0">
                            <i class="fa-brands fa-java text-lg"></i>
                        </div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Advanced Java</h4>
                            <p class="text-xs text-slate-400 mt-1">Multi-threading, design patterns, and enterprise frameworks.</p>
                        </div>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-900/60 border border-white/5 flex items-start gap-4">
                        <div class="w-10 h-10 rounded-xl bg-neon-purple/10 flex items-center justify-center text-neon-purple shrink-0">
                            <i class="fa-solid fa-mobile-screen-button text-lg"></i>
                        </div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Kotlin Development</h4>
                            <p class="text-xs text-slate-400 mt-1">Modern Android app design & reactive logic.</p>
                        </div>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-900/60 border border-white/5 flex items-start gap-4">
                        <div class="w-10 h-10 rounded-xl bg-neon-emerald/10 flex items-center justify-center text-neon-emerald shrink-0">
                            <i class="fa-solid fa-diagram-project text-lg"></i>
                        </div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Advanced DSA</h4>
                            <p class="text-xs text-slate-400 mt-1">Graph theory, dynamic programming, and optimization algorithms.</p>
                        </div>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-900/60 border border-white/5 flex items-start gap-4">
                        <div class="w-10 h-10 rounded-xl bg-neon-pink/10 flex items-center justify-center text-neon-pink shrink-0">
                            <i class="fa-solid fa-server text-lg"></i>
                        </div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Backend Engineering</h4>
                            <p class="text-xs text-slate-400 mt-1">RESTful API creation, database scaling, and microservices.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="connect" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                
                <!-- Contact Info -->
                <div class="lg:col-span-5 reveal space-y-6">
                    <h2 class="text-3xl sm:text-4xl font-bold text-white">Connect With <span class="gradient-text-cyan-purple">Wahab</span></h2>
                    <p class="text-slate-400 text-sm leading-relaxed">
                        Interested in collaborating on software projects, AI research, or discussing computer science concepts? Feel free to reach out directly through any platform below.
                    </p>

                    <div class="space-y-4 pt-2">
                        <!-- LinkedIn Link -->
                        <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="flex items-center gap-4 p-4 rounded-2xl glass-card hover:border-neon-cyan/40 group transition-all">
                            <div class="w-12 h-12 rounded-xl bg-[#0A66C2]/10 flex items-center justify-center text-[#0A66C2] text-xl group-hover:bg-[#0A66C2] group-hover:text-white transition-all">
                                <i class="fa-brands fa-linkedin-in"></i>
                            </div>
                            <div>
                                <span class="text-xs text-slate-500 uppercase tracking-wider block">LinkedIn Profile</span>
                                <span class="text-sm font-semibold text-white group-hover:text-neon-cyan transition-colors">linkedin.com/in/wahab-qadeer</span>
                            </div>
                        </a>

                        <!-- GitHub Link -->
                        <a href="https://github.com/wahab-qadeer" target="_blank" class="flex items-center gap-4 p-4 rounded-2xl glass-card hover:border-neon-purple/40 group transition-all">
                            <div class="w-12 h-12 rounded-xl bg-white/10 flex items-center justify-center text-white text-xl group-hover:bg-white group-hover:text-obsidian-900 transition-all">
                                <i class="fa-brands fa-github"></i>
                            </div>
                            <div>
                                <span class="text-xs text-slate-500 uppercase tracking-wider block">GitHub Repository</span>
                                <span class="text-sm font-semibold text-white group-hover:text-neon-purple transition-colors">github.com/wahab-qadeer</span>
                            </div>
                        </a>

                        <!-- Email Link -->
                        <a href="mailto:realwahabqadeer@gmail.com" class="flex items-center gap-4 p-4 rounded-2xl glass-card hover:border-neon-pink/40 group transition-all">
                            <div class="w-12 h-12 rounded-xl bg-neon-pink/10 flex items-center justify-center text-neon-pink text-xl group-hover:bg-neon-pink group-hover:text-white transition-all">
                                <i class="fa-solid fa-envelope"></i>
                            </div>
                            <div>
                                <span class="text-xs text-slate-500 uppercase tracking-wider block">Direct Email</span>
                                <span class="text-sm font-semibold text-white group-hover:text-neon-pink transition-colors">realwahabqadeer@gmail.com</span>
                            </div>
                        </a>
                    </div>
                </div>

                <!-- Contact Form -->
                <div class="lg:col-span-7 reveal">
                    <form id="contact-form" class="glass-card p-8 rounded-3xl space-y-5 relative">
                        <h3 class="text-xl font-bold text-white mb-2">Send a Message</h3>
                        
                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Your Name</label>
                            <input type="text" required id="form-name" placeholder="Enter your name" class="w-full px-4 py-3 rounded-xl bg-obsidian-800 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-cyan transition-colors">
                        </div>

                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Your Email</label>
                            <input type="email" required id="form-email" placeholder="Enter your email" class="w-full px-4 py-3 rounded-xl bg-obsidian-800 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-cyan transition-colors">
                        </div>

                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Subject</label>
                            <input type="text" required id="form-subject" placeholder="Project Inquiry / Opportunity" class="w-full px-4 py-3 rounded-xl bg-obsidian-800 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-cyan transition-colors">
                        </div>

                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Message</label>
                            <textarea rows="4" required id="form-message" placeholder="Write your message here..." class="w-full px-4 py-3 rounded-xl bg-obsidian-800 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-cyan transition-colors resize-none"></textarea>
                        </div>

                        <button type="submit" class="w-full py-3.5 rounded-xl bg-gradient-to-r from-neon-cyan to-neon-purple text-obsidian-900 font-bold text-sm tracking-wider uppercase hover:opacity-95 transition-all shadow-lg shadow-neon-cyan/20 flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane"></i> Send Message
                        </button>
                    </form>
                </div>

            </div>
        </section>

    </main>

    <footer class="border-t border-white/10 py-10 px-4 sm:px-6 lg:px-8 text-center text-xs text-slate-500 relative z-10">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-4">
            <p>© <span id="current-year"></span> Wahab Qadeer. BS Artificial Intelligence @ BIIT.</p>
            <div class="flex items-center gap-4">
                <a href="https://github.com/wahab-qadeer" target="_blank" class="hover:text-neon-cyan transition-colors"><i class="fa-brands fa-github text-base"></i></a>
                <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="hover:text-neon-cyan transition-colors"><i class="fa-brands fa-linkedin text-base"></i></a>
                <a href="mailto:realwahabqadeer@gmail.com" class="hover:text-neon-cyan transition-colors"><i class="fa-solid fa-envelope text-base"></i></a>
            </div>
        </div>
    </footer>

    <!-- Toast Notification Container -->
    <div id="toast" class="fixed bottom-6 right-6 z-50 transform translate-y-24 opacity-0 transition-all duration-300 pointer-events-none glass-card px-6 py-4 rounded-2xl border-neon-emerald flex items-center gap-3 text-white text-sm shadow-2xl">
        <div class="w-8 h-8 rounded-full bg-neon-emerald/20 flex items-center justify-center text-neon-emerald">
            <i class="fa-solid fa-check"></i>
        </div>
        <span id="toast-message">Message sent successfully!</span>
    </div>

    <script>
        document.getElementById('current-year').textContent = new Date().getFullYear();

        // Scroll Reveal Observer
        const revealElements = document.querySelectorAll('.reveal');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                }
            });
        }, { threshold: 0.1 });

        revealElements.forEach(el => observer.observe(el));

        const typingPhrases = [
            "BS(AI) Student @ BIIT",
            "AI & Machine Learning Developer",
            "Software & OOP Specialist",
            "Problem Solver & Systems Builder"
        ];
        let phraseIdx = 0;
        let charIdx = 0;
        let isDeleting = false;
        const typingElement = document.getElementById('typing-text');

        function typeLoop() {
            const currentPhrase = typingPhrases[phraseIdx];
            if (isDeleting) {
                typingElement.textContent = currentPhrase.substring(0, charIdx - 1);
                charIdx--;
            } else {
                typingElement.textContent = currentPhrase.substring(0, charIdx + 1);
                charIdx++;
            }

            let typeSpeed = isDeleting ? 40 : 80;

            if (!isDeleting && charIdx === currentPhrase.length) {
                typeSpeed = 2000;
                isDeleting = true;
            } else if (isDeleting && charIdx === 0) {
                isDeleting = false;
                phraseIdx = (phraseIdx + 1) % typingPhrases.length;
                typeSpeed = 500;
            }

            setTimeout(typeLoop, typeSpeed);
        }
        typeLoop();

        const filterBtns = document.querySelectorAll('.filter-btn');
        const projectCards = document.querySelectorAll('.project-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => {
                    b.classList.remove('active', 'border-neon-cyan', 'text-neon-cyan');
                    b.classList.add('text-slate-300');
                });
                btn.classList.add('active', 'border-neon-cyan', 'text-neon-cyan');

                const filter = btn.getAttribute('data-filter');

                projectCards.forEach(card => {
                    if (filter === 'all' || card.getAttribute('data-category') === filter) {
                        card.style.display = 'flex';
                        setTimeout(() => card.style.opacity = '1', 50);
                    } else {
                        card.style.opacity = '0';
                        setTimeout(() => card.style.display = 'none', 300);
                    }
                });
            });
        });

        const contactForm = document.getElementById('contact-form');
        const toast = document.getElementById('toast');
        const toastMessage = document.getElementById('toast-message');

        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const name = document.getElementById('form-name').value;
            toastMessage.textContent = `Thank you ${name}! Your message has been submitted.`;
            
            // Show toast
            toast.classList.remove('translate-y-24', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');

            contactForm.reset();

            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-24', 'opacity-0');
            }, 4000);
        });

        const canvas = document.getElementById('neural-canvas');
        const ctx = canvas.getContext('2d');

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class NeuralNode {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.vx = (Math.random() - 0.5) * 0.6;
                this.vy = (Math.random() - 0.5) * 0.6;
                this.radius = Math.random() * 2 + 1;
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;

                if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
                if (this.y < 0 || this.y > canvas.height) this.vy *= -1;
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = '#00f2fe';
                ctx.fill();
            }
        }

        const nodes = [];
        const nodeCount = Math.min(Math.floor((window.innerWidth * window.innerHeight) / 12000), 80);

        for (let i = 0; i < nodeCount; i++) {
            nodes.push(new NeuralNode());
        }

        function animateNeuralNet() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Connect nodes
            for (let i = 0; i < nodes.length; i++) {
                nodes[i].update();
                nodes[i].draw();

                for (let j = i + 1; j < nodes.length; j++) {
                    const dx = nodes[i].x - nodes[j].x;
                    const dy = nodes[i].y - nodes[j].y;
                    const dist = Math.sqrt(dx * dx + dy * dy);

                    if (dist < 140) {
                        ctx.beginPath();
                        ctx.moveTo(nodes[i].x, nodes[i].y);
                        ctx.lineTo(nodes[j].x, nodes[j].y);
                        ctx.strokeStyle = `rgba(0, 242, 254, ${1 - dist / 140 * 0.85})`;
                        ctx.lineWidth = 0.6;
                        ctx.stroke();
                    }
                }
            }

            requestAnimationFrame(animateNeuralNet);
        }

        window.onload = function() {
            animateNeuralNet();
        };
    </script>
</body>
</html>
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->[wahab_portfolio.html](https://github.com/user-attachments/files/32415964/wahab_portfolio.html)

