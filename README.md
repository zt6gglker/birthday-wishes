# birthday-wishes<!DOCTYPE html>
<html>
<head>
    <title>兰舍吉生日快乐</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(45deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee);
            background-size: 400% 400%;
            animation: gradient 15s ease infinite;
            font-family: 'Arial', sans-serif;
            cursor: pointer;
            text-align: center;
            overflow: hidden;
        }
        
        .container {
            padding: 20px;
        }
        
        h1 {
            font-size: 3em;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
        
        .hidden {
            display: none;
            font-size: 2em;
            color: #ff0;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            animation: pulse 1s infinite;
        }
        
        @keyframes gradient {
            0% {background-position: 0% 50%;}
            50% {background-position: 100% 50%;}
            100% {background-position: 0% 50%;}
        }
        
        @keyframes pulse {
            0% {transform: scale(1);}
            50% {transform: scale(1.1);}
            100% {transform: scale(1);}
        }
        
        .balloon {
            position: absolute;
            width: 40px;
            height: 50px;
            background-color: rgba(255,255,255,0.7);
            border-radius: 50%;
            bottom: -50px;
            animation: float 10s linear infinite;
        }
        
        @keyframes float {
            to {
                transform: translateY(-100vh) rotate(360deg);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎉 兰舍吉生日快乐! 🎉</h1>
        <div id="birthdayMessage" class="hidden">生日快乐!</div>
    </div>
    
    <script>
        document.body.addEventListener('click', function() {
            const message = document.getElementById('birthdayMessage');
            message.style.display = 'block';
            
            // 创建气球
            for(let i = 0; i < 20; i++) {
                createBalloon();
            }
            
            // 播放生日音乐
            const audio = new Audio('https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3');
            audio.play().catch(e => console.log('自动播放被阻止，请点击页面以播放音乐'));
        });
        
        function createBalloon() {
            const balloon = document.createElement('div');
            balloon.className = 'balloon';
            balloon.style.left = Math.random() * 100 + 'vw';
            balloon.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 75%)`;
            balloon.style.animationDuration = (5 + Math.random() * 10) + 's';
            document.body.appendChild(balloon);
            
            // 移除气球以避免内存泄漏
            setTimeout(() => {
                balloon.remove();
            }, 10000);
        }
    </script>
</body>
</html>
