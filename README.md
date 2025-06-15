<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Загадки от Яндекс Алисы</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #ff2975;
            --secondary: #f8b400;
            --accent: #2575fc;
            --dark: #2c3e50;
            --light: #f8f9fa;
            --success: #2ecc71;
            --error: #e74c3c;
            --warning: #f39c12;
        }
        
        body {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            color: var(--dark);
        }
        
        .container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 25px;
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.3);
            width: 100%;
            max-width: 800px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 90vh;
        }
        
        /* Шапка сайта */
        .header {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            padding: 30px;
            text-align: center;
            color: white;
            position: relative;
        }
        
        .alisa-container {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .alisa-icon {
            width: 100px;
            height: 100px;
            background: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 50px;
            color: var(--primary);
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
        }
        
        .header h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }
        
        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .share-section {
            margin-top: 20px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 15px;
        }
        
        .share-title {
            font-size: 1.1rem;
            margin-bottom: 10px;
        }
        
        .share-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        
        .share-btn {
            padding: 10px 20px;
            background: white;
            color: var(--primary);
            border: none;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s;
        }
        
        .share-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* Основное содержимое */
        .content {
            display: flex;
            flex: 1;
            padding: 30px;
        }
        
        .left-panel {
            flex: 1;
            padding: 20px;
            display: flex;
            flex-direction: column;
        }
        
        .right-panel {
            width: 300px;
            background: linear-gradient(to bottom, #f8f9fa, #e9ecef);
            border-radius: 20px;
            padding: 25px;
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.05);
        }
        
        /* Загадка */
        .riddle-container {
            background: linear-gradient(to right, #f0f5ff, #e6eeff);
            border-radius: 20px;
            padding: 35px;
            margin-bottom: 25px;
            text-align: center;
            min-height: 220px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 3px dashed var(--accent);
            position: relative;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .riddle-container::before {
            content: '"';
            position: absolute;
            top: 20px;
            left: 30px;
            font-size: 80px;
            color: var(--accent);
            opacity: 0.2;
            font-family: serif;
        }
        
        #riddle-text {
            font-size: 1.8rem;
            line-height: 1.6;
            color: var(--dark);
            font-weight: 500;
            z-index: 2;
        }
        
        .difficulty {
            display: inline-block;
            padding: 5px 15px;
            border-radius: 20px;
            margin-top: 20px;
            font-weight: 600;
            font-size: 0.9rem;
        }
        
        .easy { background: var(--success); color: white; }
        .medium { background: var(--warning); color: white; }
        .hard { background: var(--error); color: white; }
        
        /* Форма ввода */
        .input-group {
            margin: 20px 0;
        }
        
        #answer-input {
            width: 100%;
            padding: 18px 25px;
            font-size: 1.2rem;
            border: 2px solid #ddd;
            border-radius: 15px;
            outline: none;
            transition: all 0.3s;
        }
        
        #answer-input:focus {
            border-color: var(--secondary);
            box-shadow: 0 0 0 4px rgba(248, 180, 0, 0.2);
        }
        
        .buttons {
            display: flex;
            gap: 15px;
            margin-top: 15px;
        }
        
        button {
            flex: 1;
            padding: 16px;
            border: none;
            border-radius: 15px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        #check-btn {
            background: linear-gradient(to right, #3498db, #2980b9);
            color: white;
        }
        
        #check-btn:hover {
            background: linear-gradient(to right, #2980b9, var(--accent));
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        #new-riddle-btn {
            background: linear-gradient(to right, var(--secondary), #ff9500);
            color: white;
        }
        
        #new-riddle-btn:hover {
            background: linear-gradient(to right, #ff9500, var(--secondary));
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* Результат */
        #result {
            min-height: 140px;
            margin: 20px 0;
            padding: 25px;
            border-radius: 20px;
            font-size: 1.3rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            transition: all 0.4s;
        }
        
        .default-result {
            background: var(--light);
            color: #6c757d;
        }
        
        .success {
            background: linear-gradient(to right, var(--success), #27ae60);
            color: white;
            animation: popIn 0.5s;
        }
        
        .error {
            background: linear-gradient(to right, var(--error), #c0392b);
            color: white;
            animation: shake 0.5s;
        }
        
        .smiley {
            font-size: 3.5rem;
            margin: 15px 0;
            animation: bounce 1s infinite;
        }
        
        @keyframes popIn {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-8px); }
            40%, 80% { transform: translateX(8px); }
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        
        /* Статистика */
        .stats {
            margin-top: 20px;
        }
        
        .stat-item {
            display: flex;
            justify-content: space-between;
            padding: 15px 0;
            border-bottom: 1px solid #ddd;
        }
        
        .stat-value {
            font-weight: 700;
            color: var(--accent);
            font-size: 1.3rem;
        }
        
        .progress-container {
            margin: 25px 0;
        }
        
        .progress-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }
        
        .progress-bar {
            height: 12px;
            background: #e0e0e0;
            border-radius: 6px;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background: linear-gradient(to right, var(--secondary), var(--primary));
            border-radius: 6px;
            transition: width 0.5s;
        }
        
        /* Сложность */
        .difficulty-selector {
            margin-top: 25px;
        }
        
        .difficulty-title {
            font-size: 1.2rem;
            margin-bottom: 15px;
            color: var(--dark);
            font-weight: 600;
        }
        
        .difficulty-options {
            display: flex;
            gap: 10px;
        }
        
        .difficulty-btn {
            flex: 1;
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 12px;
            background: white;
            cursor: pointer;
            text-align: center;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .difficulty-btn.active {
            border-color: var(--accent);
            background: var(--accent);
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
        }
        
        .difficulty-btn:hover:not(.active) {
            border-color: #3498db;
        }
        
        /* Подвал */
        .footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 20px;
            font-size: 1rem;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 10px;
        }
        
        .footer-link {
            color: var(--secondary);
            text-decoration: none;
            transition: all 0.3s;
        }
        
        .footer-link:hover {
            color: white;
            text-decoration: underline;
        }
        
        /* Адаптивность */
        @media (max-width: 768px) {
            .content {
                flex-direction: column;
            }
            
            .right-panel {
                width: 100%;
                margin-top: 20px;
            }
            
            #riddle-text {
                font-size: 1.5rem;
            }
            
            .header h1 {
                font-size: 2.2rem;
            }
            
            .share-buttons {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="alisa-container">
                <div class="alisa-icon">
                    <i class="fas fa-robot"></i>
                </div>
                <div>
                    <h1>Загадки от Яндекс Алисы</h1>
                    <p>Проверьте свою смекалку с загадками разных уровней сложности!</p>
                </div>
            </div>
            
            <div class="share-section">
                <div class="share-title">Поделиться игрой:</div>
                <div class="share-buttons">
                    <button class="share-btn" id="copy-link">
                        <i class="fas fa-link"></i> Скопировать ссылку
                    </button>
                    <button class="share-btn" id="share-telegram">
                        <i class="fab fa-telegram"></i> Telegram
                    </button>
                    <button class="share-btn" id="share-vk">
                        <i class="fab fa-vk"></i> ВКонтакте
                    </button>
                </div>
            </div>
        </div>
        
        <div class="content">
            <div class="left-panel">
                <div class="riddle-container">
                    <div id="riddle-text">Нажмите "Новая загадка", чтобы начать игру!</div>
                    <div id="difficulty" class="difficulty">???</div>
                </div>
                
                <div class="input-group">
                    <input type="text" id="answer-input" placeholder="Введите ваш ответ..." autocomplete="off">
                </div>
                
                <div class="buttons">
                    <button id="check-btn">
                        <i class="fas fa-check-circle"></i> Проверить ответ
                    </button>
                    <button id="new-riddle-btn">
                        <i class="fas fa-sync-alt"></i> Новая загадка
                    </button>
                </div>
                
                <div id="result" class="default-result">
                    <p>Здесь будет отображен результат вашей попытки</p>
                    <div class="smiley">😊</div>
                </div>
            </div>
            
            <div class="right-panel">
                <div class="stats">
                    <h3><i class="fas fa-chart-line"></i> Ваша статистика</h3>
                    
                    <div class="stat-item">
                        <span>Отгадано загадок:</span>
                        <span class="stat-value" id="correct-count">0</span>
                    </div>
                    
                    <div class="stat-item">
                        <span>Не отгадано:</span>
                        <span class="stat-value" id="incorrect-count">0</span>
                    </div>
                    
                    <div class="stat-item">
                        <span>Текущая серия:</span>
                        <span class="stat-value" id="streak-count">0</span>
                    </div>
                    
                    <div class="progress-container">
                        <div class="progress-label">
                            <span>Прогресс:</span>
                            <span id="progress-value">0%</span>
                        </div>
                        <div class="progress-bar">
                            <div class="progress" id="progress" style="width: 0%"></div>
                        </div>
                    </div>
                </div>
                
                <div class="difficulty-selector">
                    <div class="difficulty-title">
                        <i class="fas fa-sliders-h"></i> Выберите сложность:
                    </div>
                    <div class="difficulty-options">
                        <div class="difficulty-btn active" data-difficulty="all">Все</div>
                        <div class="difficulty-btn" data-difficulty="easy">Легкие</div>
                        <div class="difficulty-btn" data-difficulty="medium">Средние</div>
                        <div class="difficulty-btn" data-difficulty="hard">Сложные</div>
                    </div>
                </div>
                
                <div class="difficulty-selector">
                    <div class="difficulty-title">
                        <i class="fas fa-trophy"></i> Достижения:
                    </div>
                    <div class="achievements">
                        <div class="achievement">
                            <i class="fas fa-star" style="color: gold;"></i> 
                            <span>Новичок: отгадайте 5 загадок</span>
                        </div>
                        <div class="achievement">
                            <i class="fas fa-star" style="color: silver;"></i> 
                            <span>Знаток: отгадайте 10 загадок</span>
                        </div>
                        <div class="achievement">
                            <i class="fas fa-star" style="color: #cd7f32;"></i> 
                            <span>Эксперт: отгадайте 20 загадок</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>© 2023 Загадки от Яндекс Алисы | Ответы вводите в нижнем регистре без лишних пробелов</p>
            <div class="footer-links">
                <a href="#" class="footer-link">Помощь</a>
                <a href="#" class="footer-link">О проекте</a>
                <a href="#" class="footer-link">Добавить загадку</a>
                <a href="#" class="footer-link">Обратная связь</a>
            </div>
        </div>
    </div>

    <script>
        // База данных загадок с разными уровнями сложности
        const riddles = [
            // Легкие загадки
            {
                question: "Висит груша, нельзя скушать. Что это?",
                answer: "лампочка",
                difficulty: "easy"
            },
            {
                question: "Зимой и летом одним цветом. Что это?",
                answer: "ель",
                difficulty: "easy"
            },
            {
                question: "Сидит дед, во сто шуб одет. Кто его раздевает, тот слезы проливает. Что это?",
                answer: "лук",
                difficulty: "easy"
            },
            {
                question: "Не огонь, а жжется. Что это?",
                answer: "крапива",
                difficulty: "easy"
            },
            {
                question: "Два кольца, два конца, посередине гвоздик. Что это?",
                answer: "ножницы",
                difficulty: "easy"
            },
            
            // Средние загадки
            {
                question: "Что принадлежит вам, но другие используют это чаще, чем вы?",
                answer: "имя",
                difficulty: "medium"
            },
            {
                question: "Что можно сломать, даже если его не трогать?",
                answer: "обещание",
                difficulty: "medium"
            },
            {
                question: "Чем больше из нее берешь, тем больше она становится. Что это?",
                answer: "яма",
                difficulty: "medium"
            },
            {
                question: "Что идет по городу и не двигается?",
                answer: "дорога",
                difficulty: "medium"
            },
            {
                question: "Что имеет много ключей, но не может открыть ни одной двери?",
                answer: "фортепиано",
                difficulty: "medium"
            },
            
            // Сложные загадки
            {
                question: "Что может путешествовать по миру, оставаясь в углу?",
                answer: "почтовая марка",
                difficulty: "hard"
            },
            {
                question: "У меня есть города, но нет домов. У меня есть горы, но нет деревьев. У меня есть вода, но нет рыб. Что я такое?",
                answer: "карта",
                difficulty: "hard"
            },
            {
                question: "Чем больше вы берете, тем больше вы оставляете позади. Что это?",
                answer: "следы",
                difficulty: "hard"
            },
            {
                question: "Что можно поймать, но нельзя бросить?",
                answer: "простуда",
                difficulty: "hard"
            },
            {
                question: "Что полно дыр, но всё ещё держит воду?",
                answer: "губка",
                difficulty: "hard"
            },
            {
                question: "Я начинаюсь с Т, заканчиваюсь на Т и наполнен Т. Что я?",
                answer: "чайник",
                difficulty: "hard"
            },
            {
                question: "Что становится влажнее, чем больше его сушат?",
                answer: "полотенце",
                difficulty: "hard"
            },
            {
                question: "Что у вас есть, что вы не можете видеть, и чем больше у вас этого, тем меньше вы видите?",
                answer: "тьма",
                difficulty: "hard"
            }
        ];

        // Элементы DOM
        const riddleText = document.getElementById('riddle-text');
        const answerInput = document.getElementById('answer-input');
        const checkBtn = document.getElementById('check-btn');
        const newRiddleBtn = document.getElementById('new-riddle-btn');
        const resultDiv = document.getElementById('result');
        const difficultySpan = document.getElementById('difficulty');
        const correctCount = document.getElementById('correct-count');
        const incorrectCount = document.getElementById('incorrect-count');
        const streakCount = document.getElementById('streak-count');
        const progress = document.getElementById('progress');
        const progressValue = document.getElementById('progress-value');
        const difficultyBtns = document.querySelectorAll('.difficulty-btn');
        const copyLinkBtn = document.getElementById('copy-link');
        const shareTelegramBtn = document.getElementById('share-telegram');
        const shareVkBtn = document.getElementById('share-vk');

        // Переменные состояния
        let currentRiddle = null;
        let correctAnswers = 0;
        let incorrectAnswers = 0;
        let currentStreak = 0;
        let usedRiddles = [];
        let currentDifficulty = "all";

        // Выбор случайной загадки с учетом сложности
        function getRandomRiddle() {
            // Фильтруем загадки по выбранной сложности
            let availableRiddles = riddles.filter(r => {
                if (currentDifficulty === "all") return true;
                return r.difficulty === currentDifficulty;
            });
            
            // Исключаем уже использованные загадки
            availableRiddles = availableRiddles.filter(r => !usedRiddles.includes(r.question));
            
            // Если загадки закончились, сбрасываем использованные
            if (availableRiddles.length === 0) {
                usedRiddles = [];
                availableRiddles = riddles.filter(r => {
                    if (currentDifficulty === "all") return true;
                    return r.difficulty === currentDifficulty;
                });
            }
            
            // Выбираем случайную загадку
            const randomIndex = Math.floor(Math.random() * availableRiddles.length);
            const riddle = availableRiddles[randomIndex];
            
            // Добавляем в использованные
            usedRiddles.push(riddle.question);
            
            return riddle;
        }

        // Начало новой загадки
        function startNewRiddle() {
            currentRiddle = getRandomRiddle();
            riddleText.textContent = currentRiddle.question;
            answerInput.value = '';
            resultDiv.className = 'default-result';
            resultDiv.innerHTML = '<p>Здесь будет отображен результат вашей попытки</p><div class="smiley">😊</div>';
            
            // Устанавливаем класс сложности
            difficultySpan.className = currentRiddle.difficulty;
            difficultySpan.textContent = 
                currentRiddle.difficulty === "easy" ? "Лёгкий уровень" :
                currentRiddle.difficulty === "medium" ? "Средний уровень" : "Сложный уровень";
            
            answerInput.focus();
        }

        // Проверка ответа
        function checkAnswer() {
            if (!currentRiddle) {
                showResult('Сначала получите загадку!', 'error', '😕');
                return;
            }

            const userAnswer = answerInput.value.trim().toLowerCase();
            
            if (!userAnswer) {
                showResult('Введите ответ!', 'error', '😕');
                return;
            }

            if (userAnswer === currentRiddle.answer) {
                correctAnswers++;
                currentStreak++;
                correctCount.textContent = correctAnswers;
                streakCount.textContent = currentStreak;
                showResult('✅ Верно! Отличная работа!', 'success', '😊');
            } else {
                incorrectAnswers++;
                currentStreak = 0;
                incorrectCount.textContent = incorrectAnswers;
                streakCount.textContent = currentStreak;
                const message = `❌ Неверно! Правильный ответ: <strong>${currentRiddle.answer}</strong>`;
                showResult(message, 'error', '😢');
            }
            
            // Обновляем прогресс
            updateProgress();
        }

        // Обновление прогресса
        function updateProgress() {
            const total = correctAnswers + incorrectAnswers;
            const percentage = total > 0 ? Math.round((correctAnswers / total) * 100) : 0;
            progress.style.width = `${percentage}%`;
            progressValue.textContent = `${percentage}%`;
        }

        // Показать результат
        function showResult(message, className, smiley) {
            resultDiv.className = className;
            resultDiv.innerHTML = `
                <div>${message}</div>
                <div class="smiley">${smiley}</div>
            `;
        }

        // Изменение сложности
        function setDifficulty(difficulty) {
            currentDifficulty = difficulty;
            
            // Обновляем активную кнопку
            difficultyBtns.forEach(btn => {
                if (btn.dataset.difficulty === difficulty) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
            
            // Начинаем новую загадку
            startNewRiddle();
        }

        // Функции для публикации
        function copyLink() {
            const dummy = document.createElement('textarea');
            document.body.appendChild(dummy);
            dummy.value = window.location.href;
            dummy.select();
            document.execCommand('copy');
            document.body.removeChild(dummy);
            
            alert('Ссылка скопирована в буфер обмена! Теперь вы можете поделиться игрой.');
        }
        
        function shareTelegram() {
            const url = encodeURIComponent(window.location.href);
            const text = encodeURIComponent('Попробуй отгадать загадки от Яндекс Алисы!');
            window.open(`https://t.me/share/url?url=${url}&text=${text}`, '_blank');
        }
        
        function shareVK() {
            const url = encodeURIComponent(window.location.href);
            const title = encodeURIComponent('Загадки от Яндекс Алисы');
            const description = encodeURIComponent('Интересная игра с загадками разных уровней сложности');
            window.open(`https://vk.com/share.php?url=${url}&title=${title}&description=${description}`, '_blank');
        }

        // Обработчики событий
        newRiddleBtn.addEventListener('click', startNewRiddle);
        checkBtn.addEventListener('click', checkAnswer);
        
        answerInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                checkAnswer();
            }
        });
        
        difficultyBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                setDifficulty(btn.dataset.difficulty);
            });
        });
        
        copyLinkBtn.addEventListener('click', copyLink);
        shareTelegramBtn.addEventListener('click', shareTelegram);
        shareVkBtn.addEventListener('click', shareVK);

        // Начальная инициализация
        startNewRiddle();
    </script>
</body>
</html>
