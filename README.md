<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SPACETIME LABORATORIES</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Share Tech Mono', monospace;
            background: #001a1a;
            color: #00ffcc;
            overflow-x: hidden;
            position: relative;
        }
        
        /* Animated shader background */
        body::before {
            content: "";
            position: fixed;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(0, 255, 204, 0.05) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(255, 170, 0, 0.03) 0%, transparent 50%),
                radial-gradient(circle at 40% 20%, rgba(0, 217, 255, 0.04) 0%, transparent 50%);
            animation: shaderMove 20s ease-in-out infinite;
            z-index: 0;
            pointer-events: none;
        }
        
        @keyframes shaderMove {
            0%, 100% {
                transform: translate(0, 0) rotate(0deg);
            }
            33% {
                transform: translate(5%, -5%) rotate(1deg);
            }
            66% {
                transform: translate(-3%, 3%) rotate(-1deg);
            }
        }
        
        /* Grid overlay */
        body::after {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 255, 204, 0.02) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 255, 204, 0.02) 1px, transparent 1px);
            background-size: 50px 50px;
            z-index: 0;
            pointer-events: none;
            animation: gridPulse 4s ease-in-out infinite;
        }
        
        @keyframes gridPulse {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 0.8; }
        }
        
        /* Scanlines */
        .scanlines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 0, 0, 0.1) 0px,
                transparent 1px,
                transparent 2px,
                rgba(0, 0, 0, 0.1) 3px
            );
            pointer-events: none;
            z-index: 999;
            animation: scanlineMove 8s linear infinite;
        }
        
        @keyframes scanlineMove {
            0% { transform: translateY(0); }
            100% { transform: translateY(10px); }
        }
        
        /* Vignette effect */
        .vignette {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            box-shadow: inset 0 0 200px rgba(0, 0, 0, 0.8);
            pointer-events: none;
            z-index: 998;
        }
        
        /* Chromatic aberration on text */
        .chromatic {
            position: relative;
        }
        
        .chromatic::before,
        .chromatic::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
        
        .chromatic::before {
            color: rgba(255, 0, 0, 0.3);
            z-index: -1;
            animation: glitchAnim1 2s infinite;
        }
        
        .chromatic::after {
            color: rgba(0, 255, 255, 0.3);
            z-index: -2;
            animation: glitchAnim2 2s infinite;
        }
        
        @keyframes glitchAnim1 {
            0%, 100% { transform: translate(0); }
            20% { transform: translate(-2px, 1px); }
            40% { transform: translate(2px, -1px); }
            60% { transform: translate(-1px, 2px); }
            80% { transform: translate(1px, -2px); }
        }
        
        @keyframes glitchAnim2 {
            0%, 100% { transform: translate(0); }
            20% { transform: translate(2px, -1px); }
            40% { transform: translate(-2px, 1px); }
            60% { transform: translate(1px, -2px); }
            80% { transform: translate(-1px, 2px); }
        }
        
        .container {
            position: relative;
            z-index: 1;
        }
        
        /* Header */
        header {
            padding: 40px 20px;
            text-align: center;
            position: relative;
        }
        
        .logo-container {
            position: relative;
            display: inline-block;
            margin-bottom: 30px;
        }
        
        .logo-frame {
            position: relative;
            width: 350px;
            height: 350px;
            margin: 0 auto;
            border: 2px solid #00ffcc;
            background: radial-gradient(circle at center, rgba(0, 255, 204, 0.05) 0%, transparent 70%);
            box-shadow: 
                0 0 40px rgba(0, 255, 204, 0.4),
                inset 0 0 40px rgba(0, 255, 204, 0.1);
            animation: logoGlow 3s ease-in-out infinite;
        }
        
        @keyframes logoGlow {
            0%, 100% { 
                box-shadow: 
                    0 0 40px rgba(0, 255, 204, 0.4),
                    inset 0 0 40px rgba(0, 255, 204, 0.1);
                border-color: #00ffcc;
            }
            50% { 
                box-shadow: 
                    0 0 60px rgba(0, 255, 204, 0.6),
                    inset 0 0 60px rgba(0, 255, 204, 0.2);
                border-color: #00d9ff;
            }
        }
        
        /* Corner brackets */
        .logo-frame::before,
        .logo-frame::after {
            content: "";
            position: absolute;
            width: 30px;
            height: 30px;
            border: 2px solid #00ffcc;
        }
        
        .logo-frame::before {
            top: -10px;
            left: -10px;
            border-right: none;
            border-bottom: none;
            box-shadow: 0 0 20px rgba(0, 255, 204, 0.5);
        }
        
        .logo-frame::after {
            bottom: -10px;
            right: -10px;
            border-left: none;
            border-top: none;
            box-shadow: 0 0 20px rgba(0, 255, 204, 0.5);
        }
        
        .logo {
            width: 100%;
            height: 100%;
            object-fit: contain;
            filter: brightness(1.3) contrast(1.2) drop-shadow(0 0 20px rgba(0, 255, 204, 0.6));
        }
        
        /* HUD numbers */
        .hud-readout {
            position: absolute;
            font-size: 0.65rem;
            letter-spacing: 2px;
            text-shadow: 0 0 10px currentColor;
        }
        
        .hud-tl {
            top: -35px;
            left: -50px;
            color: #00ffcc;
        }
        
        .hud-tr {
            top: -35px;
            right: -50px;
            color: #ffaa00;
        }
        
        .hud-bl {
            bottom: -35px;
            left: -50px;
            color: #00ffcc;
        }
        
        .hud-br {
            bottom: -35px;
            right: -50px;
            color: #00d9ff;
        }
        
        h1 {
            font-size: 3.5rem;
            letter-spacing: 20px;
            color: #00ffcc;
            text-shadow: 
                0 0 20px #00ffcc,
                0 0 40px #00ffcc,
                0 0 60px #00ffcc;
            margin: 20px 0 10px;
            animation: titlePulse 2s ease-in-out infinite;
        }
        
        @keyframes titlePulse {
            0%, 100% {
                text-shadow: 
                    0 0 20px #00ffcc,
                    0 0 40px #00ffcc,
                    0 0 60px #00ffcc;
            }
            50% {
                text-shadow: 
                    0 0 30px #00ffcc,
                    0 0 60px #00ffcc,
                    0 0 90px #00ffcc;
            }
        }
        
        .subtitle {
            font-size: 1.3rem;
            letter-spacing: 12px;
            color: #00d9ff;
            text-shadow: 0 0 30px #00d9ff;
        }
        
        .tagline {
            margin-top: 15px;
            font-size: 0.8rem;
            color: #ffaa00;
            letter-spacing: 3px;
            text-shadow: 0 0 15px #ffaa00;
        }
        
        /* Main panels */
        .panel-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin: 40px 20px;
        }
        
        .panel {
            background: rgba(0, 26, 26, 0.8);
            border: 1px solid #00ffcc;
            border-left: 3px solid #00ffcc;
            padding: 25px;
            position: relative;
            box-shadow: 
                0 0 20px rgba(0, 255, 204, 0.2),
                inset 0 0 30px rgba(0, 255, 204, 0.05);
        }
        
        .panel::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, #00ffcc, transparent);
            box-shadow: 0 0 10px #00ffcc;
        }
        
        .panel-label {
            font-size: 0.7rem;
            color: #00d9ff;
            text-shadow: 0 0 10px #00d9ff;
            margin-bottom: 15px;
            letter-spacing: 3px;
        }
        
        .panel-value {
            font-size: 2rem;
            color: #00ffcc;
            text-shadow: 0 0 15px #00ffcc;
            margin-bottom: 10px;
        }
        
        .panel-bar {
            width: 100%;
            height: 6px;
            background: rgba(0, 255, 204, 0.1);
            position: relative;
            overflow: hidden;
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.5);
        }
        
        .panel-bar::after {
            content: "";
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            background: linear-gradient(90deg, #00ffcc, #00d9ff);
            box-shadow: 0 0 15px #00ffcc;
            animation: barPulse 2s ease-in-out infinite;
        }
        
        .panel-bar.b1::after { width: 94%; }
        .panel-bar.b2::after { width: 87%; }
        .panel-bar.b3::after { width: 91%; }
        .panel-bar.b4::after { width: 78%; background: linear-gradient(90deg, #ffaa00, #ff6b35); box-shadow: 0 0 15px #ffaa00; }
        
        @keyframes barPulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        
        /* Terminal */
        .terminal {
            margin: 40px 20px 120px 20px;
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid #00d9ff;
            box-shadow: 
                0 0 30px rgba(0, 217, 255, 0.3),
                inset 0 0 50px rgba(0, 217, 255, 0.05);
        }
        
        .terminal-header {
            background: linear-gradient(180deg, rgba(0, 217, 255, 0.15) 0%, rgba(0, 217, 255, 0.05) 100%);
            padding: 15px 25px;
            border-bottom: 2px solid #00d9ff;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .terminal-title {
            color: #00d9ff;
            text-shadow: 0 0 15px #00d9ff;
            letter-spacing: 4px;
            font-size: 0.85rem;
        }
        
        .indicators {
            display: flex;
            gap: 12px;
        }
        
        .indicator {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            animation: indicatorBlink 2s ease-in-out infinite;
        }
        
        .ind-cyan {
            background: #00d9ff;
            box-shadow: 0 0 15px #00d9ff;
        }
        
        .ind-green {
            background: #00ffcc;
            box-shadow: 0 0 15px #00ffcc;
            animation-delay: 0.5s;
        }
        
        .ind-orange {
            background: #ffaa00;
            box-shadow: 0 0 15px #ffaa00;
            animation-delay: 1s;
        }
        
        @keyframes indicatorBlink {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.4; transform: scale(0.8); }
        }
        
        .terminal-body {
            padding: 30px;
            line-height: 2;
            font-size: 0.9rem;
        }
        
        .cmd-line {
            margin-bottom: 10px;
        }
        
        .prompt {
            color: #00d9ff;
            text-shadow: 0 0 10px #00d9ff;
        }
        
        .cmd-output {
            color: #00ffcc;
            margin-left: 20px;
        }
        
        .cmd-output.warn {
            color: #ffaa00;
            text-shadow: 0 0 10px #ffaa00;
        }
        
        .cursor-blink {
            display: inline-block;
            width: 10px;
            height: 1.2em;
            background: #00ffcc;
            box-shadow: 0 0 10px #00ffcc;
            animation: cursorAnim 1s step-end infinite;
            margin-left: 5px;
        }
        
        @keyframes cursorAnim {
            50% { opacity: 0; }
        }
        
        /* Status bar */
        .status-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 26, 26, 0.95);
            border-top: 2px solid #00ffcc;
            padding: 12px 20px;
            display: flex;
            justify-content: space-between;
            font-size: 0.7rem;
            z-index: 100;
            box-shadow: 0 -5px 30px rgba(0, 255, 204, 0.3);
        }
        
        .status-item {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #00ffcc;
            text-shadow: 0 0 8px #00ffcc;
        }
        
        .status-dot {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: #00ffcc;
            box-shadow: 0 0 12px #00ffcc;
            animation: statusDotPulse 1.5s ease-in-out infinite;
        }
        
        @keyframes statusDotPulse {
            0%, 100% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.4); opacity: 0.7; }
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            h1 { 
                font-size: 2rem; 
                letter-spacing: 10px; 
            }
            .subtitle {
                font-size: 1rem;
                letter-spacing: 6px;
            }
            .logo-frame {
                width: 250px;
                height: 250px;
            }
            .hud-readout {
                font-size: 0.6rem;
            }
            .status-bar {
                flex-wrap: wrap;
                gap: 8px;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <div class="scanlines"></div>
    <div class="vignette"></div>
    
    <div class="container">
        <header>
            <div class="logo-container">
                <div class="logo-frame">
                    <img src="https://spacetimelaboratories.com/logo.png" alt="Spacetime Laboratories" class="logo">
                    <div class="hud-readout hud-tl">▸ 500588</div>
                    <div class="hud-readout hud-tr">⚠ 550014</div>
                    <div class="hud-readout hud-bl">◂ 019.0+8</div>
                    <div class="hud-readout hud-br">✓ SYNC</div>
                </div>
            </div>
            <h1 data-text="SPACETIME" class="chromatic">SPACETIME</h1>
            <p class="subtitle">LABORATORIES</p>
            <p class="tagline">[ QUANTUM RESEARCH DIVISION • TEMPORAL MECHANICS UNIT ]</p>
        </header>
        
        <div class="panel-grid">
            <div class="panel">
                <div class="panel-label">◆ QUANTUM ENTANGLEMENT</div>
                <div class="panel-value">94.2%</div>
                <div class="panel-bar b1"></div>
            </div>
            
            <div class="panel">
                <div class="panel-label">◆ NEURAL SYNCHRONIZATION</div>
                <div class="panel-value">87.6%</div>
                <div class="panel-bar b2"></div>
            </div>
            
            <div class="panel">
                <div class="panel-label">◆ TEMPORAL STABILITY</div>
                <div class="panel-value">91.8%</div>
                <div class="panel-bar b3"></div>
            </div>
            
            <div class="panel">
                <div class="panel-label">◆ CAUSALITY MATRIX</div>
                <div class="panel-value">78.3%</div>
                <div class="panel-bar b4"></div>
            </div>
        </div>
        
        <div class="terminal">
            <div class="terminal-header">
                <div class="terminal-title">⟨ SYSTEM INTERFACE v2.077 ⟩</div>
                <div class="indicators">
                    <div class="indicator ind-cyan"></div>
                    <div class="indicator ind-green"></div>
                    <div class="indicator ind-orange"></div>
                </div>
            </div>
            <div class="terminal-body">
                <div class="cmd-line">
                    <span class="prompt">root@spacetime-lab:~$</span>
                    <span class="cmd-output">./initialize_systems.sh</span>
                </div>
                <div class="cmd-line">
                    <span class="cmd-output">▸ Loading quantum processors... [OK]</span>
                </div>
                <div class="cmd-line">
                    <span class="cmd-output">▸ Initializing neural networks... [OK]</span>
                </div>
                <div class="cmd-line">
                    <span class="cmd-output">▸ Synchronizing temporal coordinates... [OK]</span>
                </div>
                <div class="cmd-line">
                    <span class="cmd-output warn">▸ Calibrating causality matrix... [STANDBY]</span>
                </div>
                <div class="cmd-line"><br></div>
                <div class="cmd-line">
                    <span class="prompt">root@spacetime-lab:~$</span>
                    <span class="cmd-output">cat mission_statement.txt</span>
                </div>
                <div class="cmd-line">
                    <span class="cmd-output">
                        ╔════════════════════════════════════════════╗<br>
                        ║  EXPLORING THE BOUNDARIES OF SPACETIME   ║<br>
                        ║  ADVANCING QUANTUM & TEMPORAL RESEARCH   ║<br>
                        ║  PUSHING THE LIMITS OF HUMAN KNOWLEDGE   ║<br>
                        ╚════════════════════════════════════════════╝
                    </span>
                </div>
                <div class="cmd-line"><br></div>
                <div class="cmd-line">
                    <span class="prompt">root@spacetime-lab:~$</span>
                    <span class="cursor-blink"></span>
                </div>
            </div>
        </div>
    </div>
    
    <div class="status-bar">
        <div class="status-item">
            <span class="status-dot"></span>
            <span>ACTIVE</span>
        </div>
        <div class="status-item">
            <span>UPTIME: 99.97%</span>
        </div>
        <div class="status-item">
            <span>LAT: [CLASSIFIED]</span>
        </div>
        <div class="status-item">
            <span>STARDATE: 2025.341</span>
        </div>
        <div class="status-item">
            <span>CLEARANCE: Ω</span>
        </div>
    </div>
</body>
</html>
