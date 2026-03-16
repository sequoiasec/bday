<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HBD Sayang! <3</title>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@500;700&family=Caveat:wght@700&display=swap" rel="stylesheet">
    <style>
        :root {
            --pastel-pink: #ffdae0;
            --pastel-blue: #d1eaed;
            --pastel-purple: #e2d1f9;
            --soft-text: #6d5d6e;
            --deep-pink: #ff85a1;
        }

        body {
            margin: 0; padding: 0;
            display: flex; justify-content: center; align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--pastel-pink), var(--pastel-blue));
            font-family: 'Quicksand', sans-serif;
            color: var(--soft-text);
            overflow: hidden;
        }

        .container {
            text-align: center; z-index: 10;
            background: rgba(255, 255, 255, 0.6);
            padding: 40px; border-radius: 30px;
            backdrop-filter: blur(5px); border: 2px solid white;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
            animation: fadeIn 1.5s ease-out;
        }

        h1 { font-family: 'Caveat', cursive; font-size: 3rem; color: var(--deep-pink); margin-bottom: 5px; }
        .heart { font-size: 40px; color: #ffb3c1; animation: pulse 1.5s infinite; }

        .btn-open {
            background: var(--deep-pink); color: white; border: none;
            padding: 15px 30px; border-radius: 50px;
            font-weight: bold; cursor: pointer; margin-top: 20px;
            transition: 0.3s; box-shadow: 0 5px 15px rgba(255, 133, 161, 0.3);
        }

        #letter-overlay {
            display: none; position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(255, 255, 255, 0.8);
            z-index: 100; justify-content: center; align-items: center;
            backdrop-filter: blur(8px);
        }

        .letter-content {
            background: #fff; padding: 30px;
            width: 85%; max-width: 400px;
            border-radius: 20px; border: 3px dashed var(--pastel-pink);
            text-align: center; max-height: 85vh; overflow-y: auto;
        }

        .letter-photo {
            width: 150px; height: 150px; border-radius: 50%;
            object-fit: cover; border: 5px solid var(--pastel-pink);
            margin-bottom: 20px;
        }

        .letter-text {
            font-family: 'Caveat', cursive; font-size: 1.6rem;
            line-height: 1.4; color: #444; text-align: left;
            min-height: 200px; 
        }

        .letter-text::after {
            content: "|";
            animation: blink 0.7s infinite;
        }

        @keyframes blink { 50% { opacity: 0; } }
        @keyframes pulse { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.15); } }
        @keyframes fadeIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }

        .close-btn { margin-top: 25px; color: var(--deep-pink); cursor: pointer; display: none; text-decoration: underline; }
    </style>
</head>
<body>

    <audio id="myAudio" loop>
        <source src="kasih putih.mp3" type="audio/mpeg">
    </audio>

    <div class="container">
        <h1>Hi Babe! i have something for u ;p</h1>
        <div class="heart">🌸</div>
        <button class="btn-open" onclick="openLetter()">Buka Pesan Spesial 💌</button>
    </div>

    <div id="letter-overlay">
        <div class="letter-content" id="letterBox">
            <img src="sayangg.jpeg" alt="Foto" class="letter-photo">
            <div id="typewriter" class="letter-text"></div>
            <span id="closeBtn" class="close-btn" onclick="closeLetter()">Tutup Pesan</span>
        </div>
    </div>

    <script>
        const audio = document.getElementById('myAudio');
        const textElement = document.getElementById('typewriter');
        const closeBtn = document.getElementById('closeBtn');
        
        const message = `My Dearest Prasta,\n\nI’ve been thinking a lot lately about how much has changed since we first met, and yet, how my feelings for you only seem to grow deeper and more certain with every passing day.\n\nBeing 22 is such a beautiful, chaotic, and transformative time. I watch you navigate your dreams and ambitions, and I am constantly in awe of the person you are becoming. You carry yourself with a strength you don't always give yourself credit for.\n\nWhat I love most is the way your eyes light up when you talk about something you love. You aren't just my partner, u are my favorite person, my safest harbor, and the best part of my day.\n\nI am here to walk beside you through the uncertainty, to celebrate your wins, and to hold your hand through the setbacks. Thank you for the love that feels like home. I am so incredibly proud to be the one by your side.\n\nWith all my heart,\nSilvana`;

        let i = 0;
        function typeWriter() {
            if (i < message.length) {
    
                if (message.charAt(i) === "\n") {
                    textElement.innerHTML += "<br>";
                } else {
                    textElement.innerHTML += message.charAt(i);
                }
                i++;
                setTimeout(typeWriter, 60); 
            } else {
                closeBtn.style.display = "inline-block"; 
            }
        }

        function openLetter() {
            document.getElementById('letter-overlay').style.display = 'flex';
            audio.play().catch(e => console.log("Audio play blocked"));
            textElement.innerHTML = ""; 
            i = 0;
            setTimeout(typeWriter, 1000); 
        }

        function closeLetter() {
            document.getElementById('letter-overlay').style.display = 'none';
        }
    </script>
</body>
</html>
