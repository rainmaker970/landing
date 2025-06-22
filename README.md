<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>בניית פאנלים שיווקיים עם AI | הדרכה חינמית</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .hero-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
            text-align: center;
        }

        .main-headline {
            font-size: clamp(2rem, 5vw, 3.5rem);
            font-weight: 800;
            color: #2d3748;
            margin-bottom: 20px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .sub-headline {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            color: #4a5568;
            margin-bottom: 30px;
            line-height: 1.4;
        }

        .highlight-box {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            padding: 25px;
            border-radius: 15px;
            margin: 30px 0;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }

        .highlight-text {
            font-size: 1.3rem;
            font-weight: 600;
            color: #2d3748;
            text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.8);
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.9);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 2px solid transparent;
        }

        .feature-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
            border-color: #667eea;
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 15px;
            display: block;
        }

        .feature-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: #2d3748;
            margin-bottom: 10px;
        }

        .feature-text {
            color: #4a5568;
            font-size: 1rem;
        }

        .image-placeholder {
            width: 200px;
            height: 200px;
            border-radius: 20px;
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            margin: 30px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1rem;
            color: #4a5568;
            border: 3px dashed #667eea;
            transition: all 0.3s ease;
        }

        .image-placeholder:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }

        .cta-button {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 18px 40px;
            font-size: 1.4rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
            margin: 20px 0;
            text-decoration: none;
            display: inline-block;
            text-align: center;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(102, 126, 234, 0.6);
        }

        .cta-subtitle {
            display: block;
            font-size: 0.9rem;
            opacity: 0.9;
            margin-top: 5px;
        }

        .form-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
            margin-bottom: 30px;
        }

        .form-placeholder {
            background: linear-gradient(135deg, #ffeaa7 0%, #fab1a0 100%);
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            border: 3px dashed #e17055;
            color: #2d3748;
            font-size: 1.2rem;
            font-weight: 600;
        }

        .guarantee-box {
            background: linear-gradient(135deg, #a8e6cf 0%, #dcedc1 100%);
            padding: 25px;
            border-radius: 15px;
            margin: 30px 0;
            text-align: center;
            border-right: 5px solid #00b894;
        }

        .guarantee-text {
            font-size: 1.1rem;
            color: #2d3748;
            font-weight: 600;
        }

        .urgency-banner {
            background: linear-gradient(135deg, #fd79a8 0%, #fdcb6e 100%);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            margin-bottom: 20px;
            animation: pulse 2s infinite;
        }

        .timer-box {
            background: linear-gradient(135deg, #e84393 0%, #fd79a8 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            margin: 20px 0;
            color: white;
            font-weight: bold;
            box-shadow: 0 10px 25px rgba(232, 67, 147, 0.3);
        }

        .timer {
            font-size: 1.5rem;
            margin: 10px 0;
        }

        .scarcity-box {
            background: linear-gradient(135deg, #ff7675 0%, #fd79a8 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            margin: 20px 0;
            color: white;
            font-weight: bold;
            animation: shake 3s infinite;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-2px); }
            75% { transform: translateX(2px); }
        }

        .social-proof {
            background: linear-gradient(135deg, #74b9ff 0%, #0984e3 100%);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            margin: 20px 0;
            color: white;
            font-weight: 600;
        }

        .what-you-get, .ideal-for, .testimonials-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
        }

        .section-title {
            font-size: 2rem;
            color: #2d3748;
            text-align: center;
            margin-bottom: 30px;
            font-weight: 700;
        }

        .benefits-list {
            font-size: 1.2rem;
            color: #2d3748;
            line-height: 2;
        }

        .benefits-list div {
            margin: 15px 0;
            padding: 15px;
            background: linear-gradient(135deg, #a8e6cf 0%, #dcedc1 100%);
            border-radius: 10px;
            border-right: 5px solid #00b894;
        }

        .ideal-list {
            font-size: 1.1rem;
            color: #2d3748;
            line-height: 2;
        }

        .ideal-list div {
            margin: 12px 0;
            padding: 12px;
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            border-radius: 8px;
            border-right: 4px solid #667eea;
        }

        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .testimonial {
            background: linear-gradient(135deg, #ffeaa7 0%, #fab1a0 100%);
            padding: 25px;
            border-radius: 15px;
            font-style: italic;
            font-size: 1.1rem;
            color: #2d3748;
            border-right: 5px solid #e17055;
            position: relative;
        }

        .testimonial::before {
            content: '"';
            font-size: 4rem;
            position: absolute;
            top: -10px;
            right: 15px;
            opacity: 0.3;
            color: #e17055;
        }

        .money-back {
            background: linear-gradient(135deg, #00b894 0%, #55efc4 100%);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            margin: 30px 0;
            color: white;
            font-weight: bold;
            font-size: 1.2rem;
            box-shadow: 0 10px 25px rgba(0, 184, 148, 0.3);
        }

        .value-proposition {
            background: linear-gradient(135deg, #fd79a8 0%, #fdcb6e 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            margin: 20px 0;
            color: #2d3748;
            font-weight: bold;
            font-size: 1.1rem;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }

        .urgency-text {
            color: #2d3748;
            font-weight: 700;
            font-size: 1.1rem;
        }

        @media (max-width: 768px) {
            .hero-section, .form-section, .what-you-get, .ideal-for, .testimonials-section {
                padding: 25px;
            }
            
            .cta-button {
                width: 100%;
                padding: 15px;
            }

            .testimonials-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="urgency-banner">
            <div class="urgency-text">🔥 הדרכה חינמית מוגבלת בזמן - ההזדמנות שלך לשנות את המשחק!</div>
        </div>

        <div class="timer-box">
            <div>⏰ ההדרכה תסתיים בעוד:</div>
            <div class="timer" id="countdown">23:59:45</div>
            <div>אל תפספס את ההזדמנות הזאת!</div>
        </div>

        <div class="social-proof">
            👥 בהישג ידכם של 2,847 איש עסקים חכמים | 👀 נצפתה 12,456 פעמים השבוע
        </div>

        <div class="hero-section">
            <h1 class="main-headline">הפכתי משפכי שיווק מורכבים למשחק ילדים!</h1>
            
            <p class="sub-headline">בניית פאנלים שיווקיים 100% בעזרת AI<br>בלי להזיע בבנייה ובלי לשלם ארגזים של קאש למשווקים</p>

            <div class="highlight-box">
                <div class="highlight-text">איך אני בונה פאנל שלם עם AI בלי מגע ידי אדם!<br>עיצוב + כתיבה ב-LIVE מול האישונים שלך בפחות מ-8 דקות</div>
            </div>

            <div class="scarcity-box">
                ⚠️ מקומות מוגבלים: נותרו רק 47 מקומות<br>
                (ההדרכה מוגבלת ל-100 משתתפים בלבד)
            </div>

            <div class="features-grid">
                <div class="feature-card">
                    <span class="feature-icon">🤖</span>
                    <div class="feature-title">בינה מלאכותית מתקדמת</div>
                    <div class="feature-text">AI שבונה עבורך פאנלים מושלמים תוך דקות</div>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">⚡</span>
                    <div class="feature-title">מהיר כברק</div>
                    <div class="feature-text">פאנל מושלם תוך 8 דקות בלבד</div>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">💰</span>
                    <div class="feature-title">חוסך אלפי שקלים</div>
                    <div class="feature-text">בלי לשלם למעצבים ומשווקים יקרים</div>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">🎯</span>
                    <div class="feature-title">פשוט לכולם</div>
                    <div class="feature-text">גם אם אתה לא טכנולוגי בכלל</div>
                </div>
            </div>

            <div class="image-placeholder">
                מקום לתמונה מרובעת<br>עם קצוות מעוגלים
            </div>

            <a href="#form" class="cta-button">
                🎯 כן! אני רוצה את ההדרכה בחינם
                <span class="cta-subtitle">(ערך של 497₪ - חינם היום בלבד!)</span>
            </a>

            <div class="guarantee-box">
                <div class="guarantee-text">✅ בסוף ההדרכה תדע איך לבנות פאנלים בדקות בודדות<br>גם אם אתה ארכי פארכי ולא טכנולוגי בעליל</div>
            </div>
        </div>

        <div class="what-you-get">
            <h3 class="section-title">מה בדיוק תקבל בהדרכה?</h3>
            <div class="benefits-list">
                <div>✓ הטכניקה המדויקת לבניית פאנלים עם AI בצורה מקצועית</div>
                <div>✓ הכלים הטובים ביותר (חינמיים ובתשלום) שאני משתמש בהם</div>
                <div>✓ תבניות מוכנות לשימוש מיידי - פשוט העתק והדבק</div>
                <div>✓ דוגמאות אמיתיות מהשטח עם תוצאות מדידות</div>
                <div>✓ בונוס מיוחד: רשימת הפרומפטים הטובים ביותר לפאנלים</div>
            </div>
        </div>

        <div class="testimonials-section">
            <h3 class="section-title">מה אמרו אנשים שכבר השתמשו בשיטה</h3>
            <div class="testimonials-grid">
                <div class="testimonial">
                    חסכתי 15,000 ש״ח על עיצוב פאנלים וזה עבד מושלם! בניתי 5 פאנלים בשבוע אחד
                    <br><strong>- דני כהן, יזם דיגיטלי</strong>
                </div>
                <div class="testimonial">
                    אני לא מבין כלום בטכנולוגיה אבל הצלחתי לבנות פאנל מדהים תוך 10 דקות
                    <br><strong>- רחל לוי, קוסמטיקאית</strong>
                </div>
                <div class="testimonial">
                    השיטה הזאת פשוט גאונית! חסך לי חודשים של עבודה ואלפי שקלים
                    <br><strong>- יוסי מזרחי, יועץ עסקי</strong>
                </div>
            </div>
        </div>

        <div class="ideal-for">
            <h3 class="section-title">ההדרכה מושלמת עבור:</h3>
            <div class="ideal-list">
                <div>• בעלי עסקים שרוצים לחסוך אלפי שקלים על שיווק</div>
                <div>• מתחילים בשיווק דיגיטלי שרוצים תוצאות מהירות</div>
                <div>• מי שמתקשה עם הטכנולוגיה אבל רוצה להצליח</div>
                <div>• פרילנסרים שרוצים להוסיף שירות נוסף ללקוחות</div>
                <div>• כל מי שמעוניין לייעל את התהליכים השיווקיים שלו</div>
            </div>
        </div>

        <div class="value-proposition">
            🎁 ערך כולל של מעל 2,000₪ - שלך בחינם היום!
        </div>

        <div class="money-back">
            💰 הבטחת החזר מלא תוך 30 יום<br>
            אם לא תחסוך לפחות 5,000₪ בעלויות שיווק!
        </div>

        <div class="form-section" id="form">
            <h2 style="text-align: center; color: #2d3748; margin-bottom: 30px; font-size: 2rem;">השאר פרטים וקבל גישה מיידית</h2>
            
            <div class="form-placeholder">
                כאן יבוא טופס רב מסר<br>
                עם עיצוב יפה וקולח<br><br>
                📝 שם מלא<br>
                📧 אימייל<br>
                📱 טלפון<br>
                <br>
                <strong>כפתור: "כן! אני רוצה את ההדרכה עכשיו!"</strong>
            </div>

            <div style="text-align: center; margin-top: 30px;">
                <p style="color: #4a5568; font-size: 0.9rem;">🔒 הפרטים שלך מוגנים ומאובטחים 100%</p>
                <p style="color: #4a5568; font-size: 0.9rem;">📧 ללא ספאם - רק תוכן איכותי ורלוונטי</p>
                <p style="color: #4a5568; font-size: 0.9rem;">⚡ קבלת גישה מיידית לאחר הרשמה</p>
            </div>
        </div>

        <div style="text-align: center; color: rgba(255,255,255,0.8); padding: 20px;">
            <p>© 2024 - כל הזכויות שמורות | בניית פאנלים עם AI</p>
        </div>
    </div>

    <script>
        // טיימר ספירה לאחור
        function startCountdown() {
            let timeLeft = 23 * 60 * 60 + 59 * 60 + 45; // 23:59:45
            
            const timer = setInterval(() => {
                const hours = Math.floor(timeLeft / 3600);
                const minutes = Math.floor((timeLeft % 3600) / 60);
                const seconds = timeLeft % 60;
                
                document.getElementById('countdown').textContent = 
                    `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                
                timeLeft--;
                
                if (timeLeft < 0) {
                    clearInterval(timer);
                    document.getElementById('countdown').textContent = "00:00:00";
                }
            }, 1000);
        }
        
        // התחלת הטיימר כשהדף נטען
        window.onload = startCountdown;

        // גלילה חלקה לטופס
        document.querySelector('a[href="#form"]').addEventListener('click', function(e) {
            e.preventDefault();
            document.getElementById('form').scrollIntoView({
                behavior: 'smooth'
            });
        });
    </script>
</body>
</html># landing
