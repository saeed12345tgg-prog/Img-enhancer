<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Free AI-powered image enhancer tool to improve image quality, clarity, and resolution">
    <meta name="keywords" content="image enhancer, AI image tool, photo clarity, image optimizer, photo enhancer">
    <title>AI Image Enhancer | Improve Photo Quality Instantly</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4361ee;
            --primary-dark: #3a56d4;
            --secondary: #7209b7;
            --accent: #f72585;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --success: #4cc9f0;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            --glass: rgba(255, 255, 255, 0.1);
            --glass-border: rgba(255, 255, 255, 0.2);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 80%, rgba(67, 97, 238, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(114, 9, 183, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(247, 37, 133, 0.1) 0%, transparent 50%);
            z-index: -1;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 0;
            animation: fadeInDown 1s ease;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .logo-icon {
            background: var(--primary);
            width: 40px;
            height: 40px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 15px rgba(67, 97, 238, 0.4);
            animation: pulse 2s infinite;
        }

        .logo h1 {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(to right, #fff, #a5b4fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        nav a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
            position: relative;
            padding: 0.5rem 0;
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: var(--transition);
        }

        nav a:hover::after {
            width: 100%;
        }

        .hero {
            text-align: center;
            padding: 4rem 0;
            animation: fadeInUp 1s ease;
        }

        .hero h2 {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(to right, #fff, #a5b4fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto 2rem;
            color: #cbd5e1;
            line-height: 1.6;
        }

        .tool-container {
            background: var(--glass);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: var(--shadow);
            margin: 2rem 0;
            animation: slideUp 1s ease;
        }

        .tool-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .tool-title {
            font-size: 1.8rem;
            font-weight: 700;
        }

        .steps {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .step {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.75rem 1.5rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 50px;
            font-weight: 500;
            transition: var(--transition);
        }

        .step.active {
            background: var(--primary);
            box-shadow: 0 4px 15px rgba(67, 97, 238, 0.4);
        }

        .step-number {
            background: rgba(255, 255, 255, 0.2);
            width: 24px;
            height: 24px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
        }

        .step.active .step-number {
            background: rgba(255, 255, 255, 0.3);
        }

        .upload-area {
            border: 2px dashed var(--glass-border);
            border-radius: 15px;
            padding: 3rem 2rem;
            text-align: center;
            margin-bottom: 2rem;
            transition: var(--transition);
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .upload-area:hover {
            border-color: var(--primary);
            transform: translateY(-5px);
        }

        .upload-area i {
            font-size: 4rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .upload-area h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .upload-area p {
            color: #94a3b8;
            margin-bottom: 1.5rem;
        }

        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
        }

        .btn:hover {
            background: var(--primary-dark);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(67, 97, 238, 0.4);
        }

        .btn-accent {
            background: var(--accent);
            box-shadow: 0 4px 15px rgba(247, 37, 133, 0.3);
        }

        .btn-accent:hover {
            background: #e11574;
            box-shadow: 0 6px 20px rgba(247, 37, 133, 0.4);
        }

        .image-preview {
            display: none;
            margin-bottom: 2rem;
            animation: fadeIn 0.5s ease;
        }

        .preview-container {
            display: flex;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .preview-box {
            flex: 1;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 15px;
            padding: 1.5rem;
            text-align: center;
        }

        .preview-title {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .preview-image {
            width: 100%;
            height: 250px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .preview-image img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            border-radius: 8px;
        }

        .enhancement-controls {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 15px;
            padding: 2rem;
            margin-bottom: 2rem;
            animation: fadeIn 0.5s ease;
        }

        .control-title {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            font-weight: 600;
        }

        .slider-container {
            margin-bottom: 1.5rem;
        }

        .slider-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
        }

        .slider-label {
            font-weight: 500;
        }

        .slider-value {
            color: var(--success);
            font-weight: 600;
        }

        .slider {
            -webkit-appearance: none;
            width: 100%;
            height: 8px;
            border-radius: 4px;
            background: rgba(255, 255, 255, 0.1);
            outline: none;
        }

        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            background: var(--primary);
            cursor: pointer;
            box-shadow: 0 2px 10px rgba(67, 97, 238, 0.5);
            transition: var(--transition);
        }

        .slider::-webkit-slider-thumb:hover {
            transform: scale(1.2);
        }

        .enhancement-presets {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .preset {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--glass-border);
            border-radius: 10px;
            padding: 1rem;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
        }

        .preset:hover {
            background: rgba(67, 97, 238, 0.2);
            transform: translateY(-3px);
        }

        .preset.active {
            background: rgba(67, 97, 238, 0.3);
            border-color: var(--primary);
        }

        .preset-icon {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
            color: var(--primary);
        }

        .preset-name {
            font-weight: 500;
            margin-bottom: 0.25rem;
        }

        .preset-desc {
            font-size: 0.8rem;
            color: #94a3b8;
        }

        .action-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
        }

        .ad-container {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            margin: 2rem 0;
            animation: fadeIn 1s ease;
        }

        .ad-label {
            font-size: 0.9rem;
            color: #94a3b8;
            margin-bottom: 1rem;
        }

        .ad-placeholder {
            background: rgba(255, 255, 255, 0.05);
            height: 250px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 1rem;
        }

        .ad-placeholder i {
            font-size: 2.5rem;
            color: var(--gray);
        }

        .ad-placeholder p {
            color: var(--gray);
        }

        footer {
            text-align: center;
            padding: 2rem 0;
            margin-top: 2rem;
            border-top: 1px solid var(--glass-border);
            color: #94a3b8;
            font-size: 0.9rem;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 1rem;
        }

        .footer-links a {
            color: #94a3b8;
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: var(--light);
        }

        /* Animations */
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        @keyframes pulse {
            0% {
                box-shadow: 0 4px 15px rgba(67, 97, 238, 0.4);
            }
            50% {
                box-shadow: 0 4px 25px rgba(67, 97, 238, 0.7);
            }
            100% {
                box-shadow: 0 4px 15px rgba(67, 97, 238, 0.4);
            }
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-10px);
            }
            60% {
                transform: translateY(-5px);
            }
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .preview-container {
                flex-direction: column;
            }
            
            .hero h2 {
                font-size: 2.8rem;
            }
        }

        @media (max-width: 768px) {
            nav ul {
                display: none;
            }
            
            .hero h2 {
                font-size: 2.2rem;
            }
            
            .steps {
                flex-direction: column;
            }
            
            .action-buttons {
                flex-direction: column;
            }
        }

        @media (max-width: 576px) {
            .container {
                padding: 1rem;
            }
            
            .tool-container {
                padding: 1.5rem;
            }
            
            .hero h2 {
                font-size: 1.8rem;
            }
        }

        /* Loading Animation */
        .loading {
            display: none;
            text-align: center;
            padding: 2rem;
        }

        .spinner {
            width: 50px;
            height: 50px;
            border: 5px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            border-top-color: var(--primary);
            animation: spin 1s linear infinite;
            margin: 0 auto 1rem;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        /* Results Animation */
        .results {
            display: none;
            animation: fadeIn 0.5s ease;
        }

        .result-stats {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 1.5rem;
            text-align: center;
            transition: var(--transition);
        }

        .stat-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.08);
        }

        .stat-value {
            font-size: 2rem;
            font-weight: 700;
            color: var(--success);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: #94a3b8;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-magic"></i>
                </div>
                <h1>AI Image Enhancer</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">How It Works</a></li>
                    <li><a href="#">Pricing</a></li>
                    <li><a href="#">FAQ</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
        </header>

        <section class="hero">
            <h2>Transform Your Images with AI Power</h2>
            <p>Enhance image quality, increase resolution, and bring out hidden details with our advanced AI technology. Completely free and easy to use.</p>
            <button class="btn btn-accent">
                <i class="fas fa-rocket"></i> Start Enhancing Now
            </button>
        </section>

        <div class="tool-container">
            <div class="tool-header">
                <h2 class="tool-title">AI Image Enhancer</h2>
                <div class="steps">
                    <div class="step active">
                        <div class="step-number">1</div>
                        <span>Upload</span>
                    </div>
                    <div class="step">
                        <div class="step-number">2</div>
                        <span>Enhance</span>
                    </div>
                    <div class="step">
                        <div class="step-number">3</div>
                        <span>Download</span>
                    </div>
                </div>
            </div>

            <div class="upload-area" id="uploadArea">
                <i class="fas fa-cloud-upload-alt"></i>
                <h3>Upload Your Image</h3>
                <p>Drag & drop your image here or click to browse</p>
                <p class="small">Supports JPG, PNG, WEBP (Max 10MB)</p>
                <button class="btn" id="uploadBtn">
                    <i class="fas fa-folder-open"></i> Choose File
                </button>
                <input type="file" id="fileInput" accept="image/*" style="display: none;">
            </div>

            <div class="image-preview" id="imagePreview">
                <div class="preview-container">
                    <div class="preview-box">
                        <h3 class="preview-title">Original Image</h3>
                        <div class="preview-image">
                            <img id="originalImage" src="" alt="Original">
                        </div>
                    </div>
                    <div class="preview-box">
                        <h3 class="preview-title">Enhanced Image</h3>
                        <div class="preview-image">
                            <img id="enhancedImage" src="" alt="Enhanced">
                        </div>
                    </div>
                </div>

                <div class="enhancement-controls">
                    <h3 class="control-title">Enhancement Settings</h3>
                    
                    <div class="slider-container">
                     
