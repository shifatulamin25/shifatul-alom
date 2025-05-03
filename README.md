<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Special Birthday Wishes</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: 'Arial', sans-serif;
            background-color: #f0f8ff;
            overflow-x: hidden;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Password Page */
        .password-container {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            text-align: center;
            max-width: 400px;
            width: 90%;
            animation: fadeIn 1s ease-in-out;
        }

        .password-container h2 {
            color: #ff6b6b;
            margin-bottom: 20px;
        }

        .password-input {
            padding: 12px;
            width: 80%;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            margin-bottom: 15px;
            transition: border 0.3s;
        }

        .password-input:focus {
            border-color: #ff6b6b;
            outline: none;
        }

        .submit-btn {
            background-color: #ff6b6b;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s;
        }

        .submit-btn:hover {
            background-color: #ff5252;
            transform: translateY(-2px);
        }

        .error-message {
            color: red;
            margin-top: 10px;
            display: none;
        }

        /* Main Content (hidden initially) */
        .main-content {
            display: none;
            width: 100%;
            height: 100%;
            position: relative;
        }

        /* Page Styles */
        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            box-sizing: border-box;
            opacity: 0;
            transition: opacity 1s ease-in-out;
            text-align: center;
        }

        .page.active {
            opacity: 1;
        }

        /* Page 1 - Names */
        .page-1 {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
        }

        .name-container {
            text-align: center;
        }

        .my-name {
            font-size: 3rem;
            color: #ff6b6b;
            margin-bottom: 30px;
            opacity: 0;
            transform: translateY(50px);
            animation: slideUp 1s forwards 0.5s;
        }

        .bff-name {
            font-size: 4rem;
            color: #4ecdc4;
            font-weight: bold;
            opacity: 0;
            transform: scale(0.5);
            animation: zoomIn 1s forwards 1.5s;
        }

        .heart {
            color: #ff6b6b;
            font-size: 2rem;
            margin: 20px 0;
            opacity: 0;
            animation: fadeIn 1s forwards 2.5s;
        }

        /* Page 2 - Birthday Wishes */
        .page-2 {
            background: linear-gradient(135deg, #fff1eb 0%, #ace0f9 100%);
        }

        .birthday-date {
            font-size: 1.5rem;
            color: #555;
            margin-bottom: 20px;
            opacity: 0;
            animation: fadeIn 1s forwards 0.5s;
        }

        .birthday-title {
            font-size: 3.5rem;
            color: #ff6b6b;
            margin-bottom: 20px;
            opacity: 0;
            animation: bounceIn 1s forwards 1s;
        }

        .birthday-message {
            font-size: 1.8rem;
            color: #333;
            max-width: 800px;
            line-height: 1.6;
            opacity: 0;
            animation: fadeIn 1s forwards 1.5s;
        }

        .highlight {
            color: #ff6b6b;
            font-weight: bold;
        }

        /* Page 3 - Special Message */
        .page-3 {
            background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
        }

        .special-message {
            font-size: 2rem;
            color: #333;
            max-width: 800px;
            line-height: 1.6;
            opacity: 0;
            animation: fadeIn 1s forwards 0.5s;
        }

        .signature {
            margin-top: 40px;
            font-style: italic;
            font-size: 1.8rem;
            color: #ff6b6b;
            opacity: 0;
            animation: slideUp 1s forwards 1.5s;
        }

        /* Navigation */
        .nav-dots {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            z-index: 100;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: #ccc;
            margin: 0 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .dot.active {
            background-color: #ff6b6b;
            transform: scale(1.3);
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
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

        @keyframes zoomIn {
            from { 
                opacity: 0;
                transform: scale(0.5);
            }
            to { 
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes bounceIn {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            50% {
                opacity: 1;
                transform: scale(1.05);
            }
            70% {
                transform: scale(0.9);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        /* Confetti */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: #f00;
            opacity: 0;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .my-name {
                font-size: 2rem;
            }
            .bff-name {
                font-size: 2.5rem;
            }
            .birthday-title {
                font-size: 2.5rem;
            }
            .birthday-message, .special-message {
                font-size: 1.4rem;
            }
        }
    </style>
</head>
<body>
    <!-- Password Protection -->
    <div class="password-container" id="passwordContainer">
        <h2>Enter the Secret Password</h2>
        <input type="password" class="password-input" id="passwordInput" placeholder="Enter password">
        <button class="submit-btn" id="submitBtn">Enter</button>
        <p class="error-message" id="errorMessage">Incorrect password! Try again.</p>
    </div>

    <!-- Main Content -->
    <div class="main-content" id="mainContent">
        <!-- Page 1 - Names -->
        <div class="page page-1 active">
            <div class="name-container">
                <div class="my-name">From: [Your Name]</div>
                <div class="heart">❤</div>
                <div class="bff-name">To: [BFF's Name]</div>
            </div>
        </div>

        <!-- Page 2 - Birthday Wishes -->
        <div class="page page-2">
            <div class="birthday-date">Birthday Date: [Month Day, Year]</div>
            <h1 class="birthday-title">Happy Birthday!</h1>
            <div class="birthday-message">
                Wishing you an <span class="highlight">amazing</span> birthday filled with joy, laughter, and all the things you love! 
                <br><br>
                May this year bring you <span class="highlight">endless happiness</span>, success in all your endeavors, and dreams that come true. 
                <br><br>
                You're not just my best friend, you're family. Here's to many more years of friendship and memories!
            </div>
        </div>

        <!-- Page 3 - Special Message -->
        <div class="page page-3">
            <div class="special-message">
                Even though your birthday is still coming, I wanted to give you these early wishes to show how special you are to me. 
                <br><br>
                No matter where life takes us, I'll always be here for you - cheering you on, laughing with you, and supporting you through everything.
            </div>
            <div class="signature">
                With all my love,<br>
                [Your Name]
            </div>
        </div>

        <!-- Navigation Dots -->
        <div class="nav-dots">
            <div class="dot active" data-page="0"></div>
            <div class="dot" data-page="1"></div>
            <div class="dot" data-page="2"></div>
        </div>
    </div>

    <script>
        // Password Protection
        const passwordContainer = document.getElementById('passwordContainer');
        const mainContent = document.getElementById('mainContent');
        const passwordInput = document.getElementById('passwordInput');
        const submitBtn = document.getElementById('submitBtn');
        const errorMessage = document.getElementById('errorMessage');

        // Set your password here
        const correctPassword = "bff123"; // Change this to your desired password

        submitBtn.addEventListener('click', () => {
            if (passwordInput.value === correctPassword) {
                passwordContainer.style.display = 'none';
                mainContent.style.display = 'block';
                createConfetti();
            } else {
                errorMessage.style.display = 'block';
                passwordInput.value = '';
                passwordInput.focus();
            }
        });

        // Allow pressing Enter to submit password
        passwordInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                submitBtn.click();
            }
        });

        // Page Navigation
        const pages = document.querySelectorAll('.page');
        const dots = document.querySelectorAll('.dot');
        let currentPage = 0;

        // Set up dot navigation
        dots.forEach((dot, index) => {
            dot.addEventListener('click', () => {
                navigateToPage(index);
            });
        });

        // Auto-advance pages every 5 seconds
        setInterval(() => {
            const nextPage = (currentPage + 1) % pages.length;
            navigateToPage(nextPage);
        }, 8000);

        function navigateToPage(pageIndex) {
            // Hide current page
            pages[currentPage].classList.remove('active');
            dots[currentPage].classList.remove('active');
            
            // Show new page
            currentPage = pageIndex;
            pages[currentPage].classList.add('active');
            dots[currentPage].classList.add('active');

            // Create confetti when reaching birthday page
            if (currentPage === 1) {
                createConfetti();
            }
        }

        // Confetti animation
        function createConfetti() {
            const colors = ['#ff6b6b', '#4ecdc4', '#ffe66d', '#ff9ff3', '#feca57', '#1dd1a1'];
            
            for (let i = 0; i < 100; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = -10 + 'px';
                confetti.style.transform = `rotate(${Math.random() * 360}deg)`;
                
                document.body.appendChild(confetti);
                
                const animationDuration = Math.random() * 3 + 2;
                
                // Animate each confetti piece
                setTimeout(() => {
                    confetti.style.opacity = '1';
                    confetti.style.transition = `all ${animationDuration}s linear`;
                    confetti.style.top = '100vh';
                    confetti.style.left = (parseFloat(confetti.style.left) + (Math.random() * 200 - 100)) + 'px';
                }, 0);
                
                // Remove confetti after animation
                setTimeout(() => {
                    confetti.remove();
                }, animationDuration * 1000);
            }
        }

        // Replace placeholders with actual names and date
        document.addEventListener('DOMContentLoaded', () => {
            // Replace these with your actual information
            const yourName = "Alex";
            const bffName = "Taylor";
            const birthdayDate = "December 25, 2023";
            
            // Update the content
            document.querySelector('.my-name').textContent = `From: ${yourName}`;
            document.querySelector('.bff-name').textContent = `To: ${bffName}`;
            document.querySelector('.birthday-date').textContent = `Birthday Date: ${birthdayDate}`;
            document.querySelector('.signature').innerHTML = `With all my love,<br>${yourName}`;
        });
    </script>
</body>
</html>
