# smart-quiz-pro
智慧題庫系統
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>智慧題庫 - 作答系統</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f3f4f6;
            color: #333;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #1a73e8;
            color: white;
            padding: 20px;
            text-align: center;
        }

        header h1 {
            font-size: 36px;
            margin: 0;
        }

        nav {
            margin-top: 10px;
            font-size: 18px;
        }

        nav a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
        }

        nav a:hover {
            text-decoration: underline;
        }

        .main-content {
            padding: 30px;
        }

        .question {
            background-color: white;
            padding: 20px;
            margin: 20px 0;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }

        .question h3 {
            margin: 0;
            font-size: 24px;
        }

        .options button {
            margin: 5px;
            padding: 10px 20px;
            font-size: 16px;
            background-color: #4caf50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .options button:hover {
            background-color: #45a049;
        }

        .status {
            font-size: 20px;
            margin-top: 10px;
        }

        .correct {
            color: green;
        }

        .incorrect {
            color: red;
        }

        .progress-bar {
            width: 100%;
            background-color: #ddd;
            margin: 20px 0;
        }

        .progress-bar > div {
            height: 30px;
            background-color: #4caf50;
            text-align: center;
            color: white;
            line-height: 30px;
        }

        .confirm-button {
            display: none;
            margin: 20px auto;
            padding: 12px 25px;
            font-size: 18px;
            background-color: #1a73e8;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .confirm-button:hover {
            background-color: #155ab5;
        }
    </style>
</head>
<body>

    <header>
        <h1>智慧題庫 - 線上測驗系統</h1>
        <nav>
            <a href="#">首頁</a>
            <a href="#">題庫</a>
            <a href="#">統計</a>
            <a href="#">登入</a>
        </nav>
    </header>

    <div class="main-content">
        <div class="question" id="q1">
            <h3>1. 2 + 3 = ?</h3>
            <div class="options">
                <button onclick="answer(1, 'incorrect')">4</button>
                <button onclick="answer(1, 'correct')">5</button>
                <button onclick="answer(1, 'incorrect')">6</button>
            </div>
            <div class="status" id="status1"></div>
        </div>

        <div class="question" id="q2">
            <h3>2. 5 × 2 = ?</h3>
            <div class="options">
                <button onclick="answer(2, 'correct')">10</button>
                <button onclick="answer(2, 'incorrect')">12</button>
            </div>
            <div class="status" id="status2"></div>
        </div>

        <div class="question" id="q3">
            <h3>3. 9 − 4 = ?</h3>
            <div class="options">
                <button onclick="answer(3, 'correct')">5</button>
                <button onclick="answer(3, 'incorrect')">6</button>
            </div>
            <div class="status" id="status3"></div>
        </div>

        <div class="progress-bar">
            <div id="progress">進度: 0%</div>
        </div>

        <button class="confirm-button" id="confirmBtn" onclick="confirmAnswers()">確認交卷</button>
    </div>

    <script>
        let answered = 0, total = 3;

        function answer(qnum, result) {
            const statusEl = document.getElementById('status' + qnum);
            if (result === 'correct') {
                statusEl.innerHTML = '✅ 正確';
                statusEl.className = 'status correct';
            } else {
                statusEl.innerHTML = '❌ 錯誤';
                statusEl.className = 'status incorrect';
            }
            answered++;
            updateProgress();
            if (answered === total) {
                document.getElementById('confirmBtn').style.display = 'inline-block';
            }
        }

        function updateProgress() {
            let progress = (answered / total) * 100;
            document.getElementById('progress').style.width = progress + '%';
            document.getElementById('progress').innerText = '進度: ' + Math.round(progress) + '%';
        }

        function confirmAnswers() {
            alert('您已完成作答，系統將顯示解析與分析。');
        }
    </script>

</body>
</html>
