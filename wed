<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบรับบริจาคออนไลน์</title>
    <style>
        body {
            font-family: 'Prompt', sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f5f5f5;
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #0066cc;
            text-align: center;
            margin-bottom: 30px;
        }
        .donation-options {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        .bank-option {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            transition: all 0.3s ease;
        }
        .bank-option:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        .bank-logo {
            width: 80px;
            height: 80px;
            object-fit: contain;
            margin-bottom: 10px;
        }
        .donate-button {
            display: block;
            background-color: #0066cc;
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            text-decoration: none;
            margin-top: 10px;
            font-weight: bold;
        }
        .donate-button:hover {
            background-color: #004999;
        }
        .prompt-text {
            margin-top: 20px;
            padding: 15px;
            background-color: #f9f9f9;
            border-left: 4px solid #0066cc;
        }
        .qr-code {
            width: 150px;
            height: 150px;
            margin: 0 auto;
            display: block;
            background-color: #eee;
            margin-bottom: 15px;
        }
        .account-details {
            margin-top: 15px;
            font-weight: bold;
        }
        .amount-buttons {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin: 20px 0;
        }
        .amount-button {
            padding: 8px 15px;
            background-color: #e6f2ff;
            border: 1px solid #99ccff;
            border-radius: 5px;
            cursor: pointer;
        }
        .amount-button:hover {
            background-color: #cce6ff;
        }
        #custom-amount {
            padding: 8px;
            width: 100px;
            margin: 0 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>ร่วมสนับสนุนโครงการของเรา</h1>
        
        <div class="prompt-text">
            <p>ทุกการสนับสนุนของท่านมีค่าต่อการดำเนินงานของเรา เลือกช่องทางการบริจาคที่สะดวกสำหรับท่าน</p>
        </div>
        
        <div class="amount-buttons">
            <button class="amount-button" onclick="setAmount(100)">฿100</button>
            <button class="amount-button" onclick="setAmount(300)">฿300</button>
            <button class="amount-button" onclick="setAmount(500)">฿500</button>
            <button class="amount-button" onclick="setAmount(1000)">฿1,000</button>
            <input type="number" id="custom-amount" placeholder="จำนวนเงิน" onchange="setCustomAmount()">
        </div>
        
        <div class="donation-options">
            <!-- SCB -->
            <div class="bank-option">
                <img src="/api/placeholder/100/100" alt="SCB" class="bank-logo">
                <h3>ธนาคารไทยพาณิชย์</h3>
                <p class="account-details">เลขที่บัญชี: 123-4-56789-0</p>
                <a href="#" class="donate-button" id="scb-button" onclick="openBankApp('scb')">บริจาคผ่าน SCB EASY</a>
            </div>
            
            <!-- Krungthai -->
            <div class="bank-option">
                <img src="/api/placeholder/100/100" alt="Krungthai" class="bank-logo">
                <h3>ธนาคารกรุงไทย</h3>
                <p class="account-details">เลขที่บัญชี: 987-6-54321-0</p>
                <a href="#" class="donate-button" id="ktb-button" onclick="openBankApp('krungthai')">บริจาคผ่าน Krungthai NEXT</a>
            </div>
            
            <!-- Kasikorn -->
            <div class="bank-option">
                <img src="/api/placeholder/100/100" alt="Kasikorn" class="bank-logo">
                <h3>ธนาคารกสิกรไทย</h3>
                <p class="account-details">เลขที่บัญชี: 111-2-33333-4</p>
                <a href="#" class="donate-button" id="kbank-button" onclick="openBankApp('kbank')">บริจาคผ่าน K PLUS</a>
            </div>
            
            <!-- Bangkok Bank -->
            <div class="bank-option">
                <img src="/api/placeholder/100/100" alt="Bangkok Bank" class="bank-logo">
                <h3>ธนาคารกรุงเทพ</h3>
                <p class="account-details">เลขที่บัญชี: 555-6-77777-8</p>
                <a href="#" class="donate-button" id="bbl-button" onclick="openBankApp('bbl')">บริจาคผ่าน Bangkok Bank Mobile</a>
            </div>
            
            <!-- PromptPay -->
            <div class="bank-option">
                <img src="/api/placeholder/150/150" alt="PromptPay QR" class="qr-code">
                <h3>พร้อมเพย์</h3>
                <p class="account-details">หมายเลข: 089-123-4567</p>
                <a href="#" class="donate-button" onclick="openPromptPay()">บริจาคผ่าน PromptPay</a>
            </div>
        </div>
    </div>

    <script>
        let donationAmount = 100; // Default amount
        
        function setAmount(amount) {
            donationAmount = amount;
            updateDonationLinks();
        }
        
        function setCustomAmount() {
            const customAmount = document.getElementById('custom-amount').value;
            if (customAmount && !isNaN(customAmount) && customAmount > 0) {
                donationAmount = parseFloat(customAmount);
                updateDonationLinks();
            }
        }
        
        function updateDonationLinks() {
            console.log(`Donation amount set to: ${donationAmount} baht`);
            // Here you would update the links with the new amount
        }
        
        function openBankApp(bank) {
            let url;
            const recipient = encodeURIComponent("บริจาคโครงการ");
            
            switch(bank) {
                case 'scb':
                    // SCB Deep Link Format (example)
                    url = `scbeasy://payment/billpay/confirmation/0000000?amt=${donationAmount}&ref1=DONATION`;
                    break;
                case 'krungthai':
                    // Krungthai NEXT Deep Link Format (example)
                    url = `krungthai://x/transfer/4987654321?amount=${donationAmount}&note=donation`;
                    break;
                case 'kbank':
                    // K PLUS Deep Link Format (example)
                    url = `kplus://transfer/1112333334/DONATION/${donationAmount}`;
                    break;
                case 'bbl':
                    // Bangkok Bank Mobile Deep Link Format (example)
                    url = `bangkokbank://payment?account=5556777778&amount=${donationAmount}&reference=DONATION`;
                    break;
                default:
                    url = '#';
            }
            
            // Try to open the app
            const opened = window.open(url, '_blank');
            
            // If unable to open the app (likely desktop or unsupported device)
            if (!opened || opened.closed || typeof opened.closed == 'undefined') {
                alert(`คุณกำลังพยายามเปิดแอป ${bank.toUpperCase()}\nหากคุณใช้งานบนคอมพิวเตอร์หรืออุปกรณ์ที่ไม่รองรับ กรุณาใช้งานผ่านสมาร์ทโฟนที่มีแอปธนาคารติดตั้งไว้`);
            }
        }
        
        function openPromptPay() {
            // ในกรณีจริง คุณอาจจะต้องการสร้าง QR Code แบบไดนามิกที่มีจำนวนเงิน
            alert(`กรุณาสแกน QR Code PromptPay ด้านบนเพื่อโอนเงินจำนวน ${donationAmount} บาท`);
        }
    </script>
</body>
</html>
