# tro87722.github.io
Settlement Calculator by State
<!DOCTYPE index.html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Injury Settlement Calculator</title>
    <style>
        :root { --primary: #2c3e50; --accent: #e74c3c; --light: #ecf0f1; }
        body { font-family: 'Segoe UI', sans-serif; background: #f4f7f6; display: flex; justify-content: center; padding: 20px; }
        .calc-container { background: white; padding: 30px; border-radius: 12px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); width: 100%; max-width: 500px; }
        h2 { color: var(---primary); margin-top: 0; text-align: center; }
        .input-group { margin-bottom: 15px; }
        label { display: block; margin-bottom: 5px; font-weight: bold; color: #555; }
        input, select { width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 6px; box-sizing: border-box; }
        button { width: 100%; padding: 15px; background: var(--primary); color: white; border: none; border-radius: 6px; font-size: 16px; cursor: pointer; transition: 0.3s; margin-top: 10px; }
        button:hover { background: #1a252f; }
        #results { margin-top: 25px; padding: 20px; background: var(--light); border-radius: 8px; display: none; text-align: center; }
        .lead-form { border-top: 2px solid #ddd; margin-top: 20px; padding-top: 20px; display: none; }
        .estimate-val { font-size: 24px; color: var(--accent); font-weight: bold; }
    </style>
</head>
<body>

<div class="calc-container">
    <h2>Settlement Estimator</h2>
    
    <div id="calculator-ui">
        <div class="input-group">
            <label>Medical Expenses ($)</label>
            <input type="number" id="med_bills" placeholder="e.g. 5000">
        </div>
        <div class="input-group">
            <label>Lost Wages ($)</label>
            <input type="number" id="lost_wages" placeholder="e.g. 2000">
        </div>
        <div class="input-group">
            <label>Injury Severity</label>
            <select id="severity">
                <option value="1.5">Minor (Bruises, soft tissue)</option>
                <option value="3">Moderate (Broken bones, minor surgery)</option>
                <option value="5">Severe (Spinal, Brain injury, Permanent)</option>
            </select>
        </div>
        <button onclick="calculateEstimate()">Calculate My Estimate</button>
    </div>

    <div id="results">
        <p>Estimated Case Value:</p>
        <div class="estimate-val" id="total-display">$0</div>
        <p style="font-size: 12px; color: #777;">*This is an estimate only and not legal advice.</p>
        
        <div class="lead-form" id="lead-form">
            <h3>Get a Free Attorney Review</h3>
            <p>Speak to a local lawyer to maximize this amount.</p>
            <form id="contact-form">
                <div class="input-group"><input type="text" placeholder="Full Name" required></div>
                <div class="input-group"><input type="email" placeholder="Email Address" required></div>
                <div class="input-group"><input type="tel" placeholder="Phone Number" required></div>
                <button type="submit" style="background: var(--accent);">Send to Attorney</button>
            </form>
        </div>
    </div>
</div>

<script>
function calculateEstimate() {
    const med = parseFloat(document.getElementById('med_bills').value) || 0;
    const wages = parseFloat(document.getElementById('lost_wages').value) || 0;
    const multiplier = parseFloat(document.getElementById('severity').value);
    
    // Formula: (Medical + Wages) + ((Medical + Wages) * Multiplier)
    const economic = med + wages;
    const nonEconomic = economic * multiplier;
    const total = economic + nonEconomic;

    document.getElementById('total-display').innerText = '$' + total.toLocaleString();
    document.getElementById('results').style.display = 'block';
    document.getElementById('lead-form').style.display = 'block';
}
</script>

</body>
</html>
