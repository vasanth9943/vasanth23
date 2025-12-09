<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vasanth V - Professional Portfolio</title>

    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;
            color: #ffffff;
            overflow-x: hidden;
            background: #000000;
            line-height: 1.6;
        }

        /* ---------------- BACKGROUND ---------------- */
        .animated-bg {
            position: fixed;
            inset: 0;
            z-index: -1;
            background: linear-gradient(45deg, #0a0a0a, #1a1a2e, #16213e, #0f3460);
            background-size: 400% 400%;
            animation: gradientWave 15s ease infinite;
        }

        @keyframes gradientWave {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .tech-grid {
            position: absolute;
            inset: 0;
            background-image:
                linear-gradient(rgba(99, 102, 241, 0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(99, 102, 241, 0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: gridScroll 30s linear infinite;
        }

        @keyframes gridScroll {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        .circuit-lines { position: absolute; inset: 0; overflow: hidden; }
        .circuit-line {
            position: absolute;
            height: 2px;
            background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.5), transparent);
            animation: circuitFlow 8s linear infinite;
        }

        .circuit-line:nth-child(1) { width: 200px; top: 20%; left: -200px; animation-delay: 0s; }
        .circuit-line:nth-child(2) { width: 150px; top: 40%; left: -150px; animation-delay: 2s; }
        .circuit-line:nth-child(3) { width: 180px; top: 60%; left: -180px; animation-delay: 4s; }
        .circuit-line:nth-child(4) { width: 160px; top: 80%; left: -160px; animation-delay: 6s; }

        @keyframes circuitFlow {
            0% { left: -200px; opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { left: 100%; opacity: 0; }
        }

        /* Binary Effect */
        .binary-rain {
            position: absolute;
            inset: 0;
            overflow: hidden;
        }

        .binary-col {
            position: absolute;
            top: -100%;
            color: rgba(99, 102, 241, 0.3);
            font-family: 'Courier New', monospace;
            font-size: 14px;
            white-space: nowrap;
            animation: binaryFall 10s linear infinite;
        }

        @keyframes binaryFall {
            0% { top: -100%; opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { top: 100%; opacity: 0; }
        }

        .binary-col:nth-child(n) { animation-delay: calc(n * 0.3s); left: calc(5% + (n - 1) * 9%); }

        /* Floating Lights */
        .orb { position: absolute; border-radius: 50%; filter: blur(60px); opacity: 0.4; animation: float 20s infinite ease-in-out; }
        .orb1 { width: 400px; height: 400px; background: radial-gradient(circle, #6366f1, transparent); top: 10%; left: 10%; }
        .orb2 { width: 350px; height: 350px; background: radial-gradient(circle, #ec4899, transparent); top: 60%; right: 10%; animation-delay: 3s; }
        .orb3 { width: 300px; height: 300px; background: radial-gradient(circle, #14b8a6, transparent); bottom: 10%; left: 50%; animation-delay: 6s; }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            25% { transform: translate(30px, -30px) scale(1.1); }
            50% { transform: translate(-20px, 20px) scale(0.9); }
            75% { transform: translate(40px, 10px) scale(1.05); }
        }

        /* Particles */
        .particles { position: fixed; inset: 0; z-index: -1; }
        .particle {
            position: absolute;
            width: 3px; height: 3px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            animation: rise 15s linear infinite;
        }

        @keyframes rise {
            0% { transform: translateY(0) translateX(0); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100vh) translateX(100px); opacity: 0; }
        }

        .particle:nth-child(n) { left: calc(n * 10%); animation-delay: calc(n * .3s); }

        /* ---------------- HEADER ---------------- */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.5rem 5%;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            z-index: 1000;
            transition: all 0.3s;
        }

        header.scrolled { padding: 1rem 5%; background: rgba(0, 0, 0, 0.9); }

        nav {
            max-width: 1400px;
            margin: auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, #6366f1, #ec4899, #14b8a6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .nav-menu {
            list-style: none;
            display: flex;
            gap: 3rem;
        }

        .nav-menu a {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            font-weight: 500;
            position: relative;
            transition: 0.3s;
        }

        .nav-menu a:hover { color: #fff; }

        /* Resume button */
        .nav-resume {
            background: linear-gradient(135deg, #6366f1, #ec4899);
            padding: .6rem 1.5rem;
            border-radius: 50px;
            color: #fff !important;
        }

        /* ---------------- HERO ---------------- */
        .hero {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 8rem 5% 5rem;
            text-align: center;
        }

        .hero-title {
            font-size: clamp(2.5rem, 6vw, 5rem);
            font-weight: 800;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, #ffffff, #a78bfa, #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-subtitle {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            color: rgba(255, 255, 255, 0.7);
            margin-bottom: 2rem;
        }

        .hero-description {
            max-width: 700px;
            margin: 0 auto 3rem;
            font-size: 1.1rem;
            color: rgba(255, 255, 255, 0.6);
        }

        .cta-buttons { display: flex; gap: 1.5rem; justify-content: center; flex-wrap: wrap; }
        .btn {
            padding: 1rem 2.5rem;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
        }
        .btn-primary {
            background: linear-gradient(135deg, #6366f1, #ec4899);
            color: #fff;
        }
        .btn-secondary {
            border: 2px solid rgba(255, 255, 255, 0.3);
            color: #fff;
        }

        /* ---------------- SECTIONS ---------------- */
        section {
            padding: 6rem 5%;
            max-width: 1400px;
            margin: auto;
        }

        .section-title {
            text-align: center;
            font-size: clamp(2rem, 4vw, 3rem);
            font-weight: 700;
            margin-bottom: 4rem;
            background: linear-gradient(135deg, #6366f1, #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Cards */
        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2.5rem;
        }

        .card {
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 24px;
            padding: 2.5rem;
            backdrop-filter: blur(20px);
            transition: .5s;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 50px rgba(99, 102, 241, 0.3);
        }

        .card-icon {
            width: 60px; height: 60px;
            border-radius: 16px;
            font-size: 1.8rem;
            display: flex; justify-content: center; align-items: center;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, #6366f1, #ec4899);
        }

        .card-title {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .card-subtitle { color: #ec4899; margin-bottom: .5rem; font-weight: 600; }
        .card-date { font-size: .9rem; color: rgba(255,255,255,.4); margin-bottom: 1rem; }
        .card-text { color: rgba(255,255,255,.7); }

        /* Skills */
        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
            justify-content: center;
        }

        .skill-badge {
            padding: 1rem 2rem;
            background: rgba(255,255,255,0.1);
            border-radius: 50px;
            border: 1px solid rgba(255,255,255,0.2);
            font-weight: 600;
        }

        /* Contact */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            max-width: 1000px;
            margin: auto;
        }

        .contact-card {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px;
            text-align: center;
            padding: 2rem;
            transition: .3s;
        }

        .contact-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(99,102,241,0.3);
        }

        .contact-icon { font-size: 2.5rem; margin-bottom: 1rem; }
        .contact-value a { color: #fff; text-decoration: none; }

        footer {
            text-align: center;
            padding: 3rem 5%;
            border-top: 1px solid rgba(255,255,255,0.1);
            background: rgba(0,0,0,.8);
        }
    </style>
</head>

<body>

    <!-- BACKGROUND -->
    <div class="animated-bg">
        <div class="tech-grid"></div>

        <div class="circuit-lines">
            <div class="circuit-line"></div>
            <div class="circuit-line"></div>
            <div class="circuit-line"></div>
            <div class="circuit-line"></div>
        </div>

        <div class="binary-rain">
            <div class="binary-col">01001010<br>10110101<br>11001100<br>01110011</div>
            <div class="binary-col">11010110<br>00101011<br>10011010<br>01100011</div>
            <div class="binary-col">10101100<br>01011010<br>11010101<br>01001110</div>
            <div class="binary-col">01110010<br>10011011<br>00111001<br>10101100</div>
            <div class="binary-col">11001010<br>10110100<br>11010010<br>00101110</div>
        </div>

        <div class="orb orb1"></div>
        <div class="orb orb2"></div>
        <div class="orb orb3"></div>
    </div>

    <div class="particles">
        <div class="particle"></div><div class="particle"></div><div class="particle"></div>
        <div class="particle"></div><div class="particle"></div><div class="particle"></div>
        <div class="particle"></div><div class="particle"></div><div class="particle"></div>
        <div class="particle"></div>
    </div>

    <!-- HEADER -->
    <header>
        <nav>
            <div class="logo">VASANTH V</div>
            <ul class="nav-menu">
                <li><a href="#about">About</a></li>
                <li><a href="#experience">Experience</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <!-- HERO -->
    <section class="hero">
        <div class="hero-content">
            <h1 class="hero-title">Hi, I'm Vasanth V</h1>
            <p class="hero-subtitle">IT Professional | UI/UX Designer | Machine Learning Enthusiast</p>
            <p class="hero-description">
                Motivated and adaptable individual seeking opportunities in the IT industry to apply problem-solving skills,
                learn new technologies, and contribute to organizational growth.
            </p>

            <div class="cta-buttons">
                <a href="#contact" class="btn btn-primary">Get In Touch</a>
                <a href="#" class="btn btn-secondary">Resume</a>
            </div>
        </div>
    </section>

    <!-- ABOUT -->
    <section id="about">
        <h2 class="section-title">About Me</h2>
        <div class="card">
            <div class="card-icon">🎓</div>
            <h3 class="card-title">Education</h3>
            <p class="card-text"><strong>B.Tech Information Technology</strong><br>Anjalai Ammal Mahalingam Engineering College<br>CGPA: 7.5 / 10 | May 2025</p>
            <p class="card-text" style="margin-top:1.2rem"><strong>HSC – Karthi Vidhyalaya Matric Hr Sec School</strong><br>78% | May 2021</p>
            <p class="card-text" style="margin-top:1.2rem"><strong>SSLC – Karthi Vidhyalaya Matric Hr Sec School</strong><br>70% | March 2019</p>
        </div>
    </section>

    <!-- EXPERIENCE -->
    <section id="experience">
        <h2 class="section-title">Professional Experience</h2>
        <div class="card-grid">
            <div class="card">
                <div class="card-icon">🎨</div>
                <h3 class="card-title">UI/UX Intern</h3>
                <p class="card-subtitle">Astonish Infotech [P] LTD</p>
                <p class="card-date">June 14 – August 10, 2025</p>
                <p class="card-text">
                    Designed user-friendly interfaces using Figma, created wireframes and interactive prototypes,
                    and contributed to client-based UI/UX projects.
                </p>
            </div>

            <div class="card">
                <div class="card-icon">🤖</div>
                <h3 class="card-title">Machine Learning Intern</h3>
                <p class="card-subtitle">SmartiApps Technologies</p>
                <p class="card-date">February – May 2025</p>
                <p class="card-text">
                    Worked on ML-based lung cancer prediction system using CT scan images — responsible for preprocessing,
                    evaluating deep learning models, and improving prediction performance.
                </p>
            </div>
        </div>
    </section>

    <!-- PROJECTS -->
    <section id="projects">
        <h2 class="section-title">Academic Projects</h2>
        <div class="card-grid">
            <div class="card">
                <div class="card-icon">🔬</div>
                <h3 class="card-title">Lung Cancer Detection Using ResNeXt</h3>
                <p class="card-text">
                    Built a deep learning model based on ResNeXt architecture for lung cancer classification using CT scan images.
                    Enhanced accuracy using CLAHE preprocessing and CutMix augmentation.
                </p>
                <p class="card-text"><strong>Technologies:</strong> Python, TensorFlow, CNN, ResNeXt, CLAHE</p>
            </div>

            <div class="card">
                <div class="card-icon">💼</div>
                <h3 class="card-title">Conference Management System</h3>
                <p class="card-text">
                    Java-based project for maintaining employee records and generating automated reports.
                    Included performance monitoring and data storage.
                </p>
                <p class="card-text"><strong>Technologies:</strong> Java, SQL, JDBC, Swing</p>
            </div>
        </div>
    </section>

    <!-- SKILLS -->
    <section id="skills">
        <h2 class="section-title">Technical Skills</h2>
        <div class="skills-grid">
            <div class="skill-badge">HTML</div>
            <div class="skill-badge">CSS</div>
            <div class="skill-badge">JavaScript</div>
            <div class="skill-badge">Java</div>
            <div class="skill-badge">SQL</div>
        </div>

        <h2 class="section-title" style="margin-top: 5rem;">Soft Skills</h2>
        <div class="skills-grid">
            <div class="skill-badge">Communication</div>
            <div class="skill-badge">Team Collaboration</div>
            <div class="skill-badge">Time Management</div>
            <div class="skill-badge">Problem Solving</div>
            <div class="skill-badge">Adaptability</div>
            <div class="skill-badge">Critical Thinking</div>
        </div>
    </section>

    <!-- CONTACT -->
    <section id="contact">
        <h2 class="section-title">Get In Touch</h2>
        <div class="contact-grid">
            <div class="contact-card">
                <div class="contact-icon">📧</div>
                <p class="contact-label">Email</p>
                <p class="contact-value"><a href="mailto:vasanthmv230@gmail.com">vasanthmv230@gmail.com</a></p>
            </div>

            <div class="contact-card">
                <div class="contact-icon">📱</div>
                <p class="contact-label">Phone</p>
                <p class="contact-value"><a href="tel:9943160748">9943160748</a></p>
            </div>

            <div class="contact-card">
                <div class="contact-icon">💼</div>
                <p class="contact-label">LinkedIn</p>
                <p class="contact-value"><a href="https://linkedin.com/in/vasanth-v-230vd" target="_blank">vasanth-v-230vd</a></p>
            </div>

            <div class="contact-card">
                <div class="contact-icon">📍</div>
                <p class="contact-label">Location</p>
                <p class="contact-value">Tamil Nadu, India</p>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer>
        <p>&copy; 2024 Vasanth V. All rights reserved. Built with passion and code.</p>
    </footer>

    <!-- SCRIPT -->
    <script>
        // Header scroll effect
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            header.classList.toggle('scrolled', window.scrollY > 100);
        });

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(link => {
            link.addEventListener('click', e => {
                e.preventDefault();
                const target = document.querySelector(link.getAttribute('href'));
                if (target) target.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>

</body>
</html>
