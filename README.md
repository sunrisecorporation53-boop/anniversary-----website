# anniversary-----website

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>365 Days of Us | 30.01.2026</title>
    
    <!-- Modern Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,600;1,400&family=Plus+Jakarta+Sans:wght@200;400;600&display=swap" rel="stylesheet">
    
    <!-- Animation Libraries -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        :root {
            --bg-deep: #030303;
            --rose-gold: #e0b0ff; /* Ethereal lavender-pink */
            --accent-gold: #d4af37;
            --glass: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.08);
            --text-main: #f0f0f0;
            --text-dim: #888;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            cursor: none; /* Custom cursor used for 2026 trend */
        }

        body {
            background-color: var(--bg-deep);
            color: var(--text-main);
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* --- Custom Cursor --- */
        #cursor-follower {
            position: fixed;
            width: 20px;
            height: 20px;
            background: var(--rose-gold);
            border-radius: 50%;
            pointer-events: none;
            z-index: 9999;
            mix-blend-mode: difference;
            transition: transform 0.1s ease;
        }

        /* --- Preloader --- */
        #loader {
            position: fixed;
            inset: 0;
            background: #000;
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: clip-path 1.2s cubic-bezier(0.8, 0, 0.2, 1);
        }

        .loader-content {
            text-align: center;
        }

        .loader-line {
            width: 100px;
            height: 2px;
            background: var(--rose-gold);
            margin: 20px auto;
            transform: scaleX(0);
        }

        /* --- Layout Sections --- */
        section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 5vw;
            position: relative;
        }

        /* --- Hero --- */
        .hero-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(3rem, 10vw, 8rem);
            font-weight: 300;
            text-align: center;
            line-height: 1.1;
            background: linear-gradient(135deg, #fff 0%, var(--rose-gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .scroll-pill {
            position: absolute;
            bottom: 40px;
            padding: 10px 20px;
            border: 1px solid var(--glass-border);
            border-radius: 100px;
            font-size: 0.7rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            opacity: 0.5;
            animation: bounce 2s infinite;
        }

        /* --- Bento Grid --- */
        .bento-container {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            grid-auto-rows: 250px;
            gap: 20px;
            max-width: 1200px;
            width: 100%;
        }

        .bento-card {
            background: var(--glass);
            backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            border-radius: 30px;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .bento-card:hover {
            border-color: var(--rose-gold);
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.05);
        }

        .card-big { grid-column: span 2; grid-row: span 2; }
        .card-tall { grid-row: span 2; }

        .stat-number {
            font-size: 3.5rem;
            font-family: 'Cormorant Garamond', serif;
            color: var(--rose-gold);
            display: block;
        }

        /* --- The Love Letter --- */
        .letter-text {
            max-width: 800px;
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.2rem;
            text-align: center;
            line-height: 1.4;
            font-style: italic;
        }

        /* --- Interaction --- */
        #celebrate-btn {
            background: transparent;
            border: 1px solid var(--rose-gold);
            color: var(--rose-gold);
            padding: 20px 50px;
            border-radius: 100px;
            font-size: 1rem;
            letter-spacing: 5px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 40px;
        }

        #celebrate-btn:hover {
            background: var(--rose-gold);
            color: var(--bg-deep);
            box-shadow: 0 0 30px rgba(224, 176, 255, 0.3);
        }

        /* --- Floating Orbs --- */
        .orb {
            position: absolute;
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, rgba(224, 176, 255, 0.08) 0%, transparent 70%);
            z-index: -1;
            pointer-events: none;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-10px);}
            60% {transform: translateY(-5px);}
        }

        @media (max-width: 768px) {
            .bento-container { grid-template-columns: 1fr; }
            .card-big, .card-tall { grid-column: span 1; grid-row: span 1; }
            .hero-title { font-size: 4rem; }
            .letter-text { font-size: 1.5rem; }
        }
    </style>
</head>
<body>

    <div id="cursor-follower"></div>

    <!-- Preloader -->
    <div id="loader">
        <div class="loader-content">
            <h2 style="font-weight: 200; letter-spacing: 10px;">JANUARY 30</h2>
            <div class="loader-line" id="loaderLine"></div>
            <p style="font-size: 0.6rem; letter-spacing: 4px; opacity: 0.5;">PREPARING YOUR MAGIC</p>
        </div>
    </div>

    <div class="orb" style="top: 10%; left: -10%;"></div>
    <div class="orb" style="bottom: 10%; right: -10%;"></div>

    <main>
        <!-- Section 1: Hero -->
        <section id="hero">
            <p style="letter-spacing: 5px; opacity: 0.6; margin-bottom: 20px;">EST. JANUARY 30, 2025</p>
            <h1 class="hero-title">A Year of <br>Endless You.</h1>
            <div class="scroll-pill">Scroll Into Our Story</div>
        </section>

        <!-- Section 2: The Journey Counter -->
        <section id="stats">
            <div class="bento-container">
                <div class="bento-card card-big">
                    <p style="color: var(--text-dim); text-transform: uppercase; letter-spacing: 2px;">The Best Year</p>
                    <h2 class="stat-number">365 Days</h2>
                    <p>Of laughter, growth, and realizing that every version of my future involves you.</p>
                </div>
                <div class="bento-card">
                    <span class="stat-number">8,760</span>
                    <p>Hours of pure happiness.</p>
                </div>
                <div class="bento-card card-tall">
                    <p style="color: var(--text-dim); text-transform: uppercase; letter-spacing: 2px;">Our Favorite Place</p>
                    <h2 style="font-family: 'Cormorant Garamond'; font-size: 2rem; margin-top: 20px;">"Anywhere <br>You Are."</h2>
                </div>
                <div class="bento-card">
                    <span class="stat-number">∞</span>
                    <p>Reasons why I love you.</p>
                </div>
            </div>
        </section>

        <!-- Section 3: The Message -->
        <section id="message">
            <div class="letter-text" id="revealText">
                "In 2025, you were a dream I was just waking up to. In 2026, you are the reality I never want to leave. Thank you for making this first year the most beautiful chapter of my life."
            </div>
        </section>

        <!-- Section 4: Finale -->
        <section id="finale">
            <h2 style="font-family: 'Cormorant Garamond'; font-size: 3rem;">Ready for year two?</h2>
            <button id="celebrate-btn" onclick="celebrate()">Click to Celebrate</button>
            <p style="margin-top: 40px; opacity: 0.4; font-size: 0.8rem;">I LOVE YOU FOREVER</p>
        </section>
    </main>

    <script>
        // --- GSAP Registration ---
        gsap.registerPlugin(ScrollTrigger);

        // --- Custom Cursor ---
        const cursor = document.getElementById('cursor-follower');
        document.addEventListener('mousemove', e => {
            gsap.to(cursor, {
                x: e.clientX,
                y: e.clientY,
                duration: 0.1
            });
        });

        // --- Preloader Logic ---
        window.addEventListener('load', () => {
            const tl = gsap.timeline();
            tl.to("#loaderLine", { scaleX: 1, duration: 1.5, ease: "power2.inOut" })
              .to("#loader", { 
                  clipPath: "polygon(0 0, 100% 0, 100% 0, 0 0)", 
                  duration: 1.5, 
                  ease: "power4.inOut" 
              })
              .from(".hero-title", { y: 100, opacity: 0, duration: 1.2, ease: "power4.out" }, "-=0.5");
        });

        // --- Scroll Animations ---
        gsap.utils.toArray(".bento-card").forEach((card, i) => {
            gsap.from(card, {
                scrollTrigger: {
                    trigger: card,
                    start: "top 85%",
                },
                opacity: 0,
                y: 50,
                duration: 1,
                delay: i * 0.1
            });
        });

        gsap.from("#revealText", {
            scrollTrigger: {
                trigger: "#revealText",
                start: "top 70%",
            },
            opacity: 0,
            filter: "blur(10px)",
            y: 30,
            duration: 2
        });

        // --- Interaction: Celebration ---
        function celebrate() {
            const duration = 5 * 1000;
            const end = Date.now() + duration;

            (function frame() {
                confetti({
                    particleCount: 3,
                    angle: 60,
                    spread: 55,
                    origin: { x: 0 },
                    colors: ['#e0b0ff', '#ffffff', '#d4af37']
                });
                confetti({
                    particleCount: 3,
                    angle: 120,
                    spread: 55,
                    origin: { x: 1 },
                    colors: ['#e0b0ff', '#ffffff', '#d4af37']
                });

                if (Date.now() < end) {
                    requestAnimationFrame(frame);
                }
            }());

            // Transform button
            const btn = document.getElementById('celebrate-btn');
            btn.innerHTML = "I LOVE YOU!";
            btn.style.borderColor = "white";
        }

        // --- Aesthetic Micro-interactions ---
        document.querySelectorAll('.bento-card, #celebrate-btn').forEach(el => {
            el.addEventListener('mouseenter', () => gsap.to(cursor, { scale: 4, background: 'rgba(255,255,255,0.1)' }));
            el.addEventListener('mouseleave', () => gsap.to(cursor, { scale: 1, background: 'var(--rose-gold)' }));
        });
    </script>
</body>
</html>
