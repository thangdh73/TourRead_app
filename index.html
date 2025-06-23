from flask import Flask, request, jsonify, render_template_string

app = Flask(__name__)

def calculate_green_read(paces, actual_slope, green_speed, uphill=False):
    one_percent_break = (paces * 2) - 1
    actual_break = one_percent_break * actual_slope
    speed_adjustment = (green_speed - 10) * 0.1 * actual_break
    adjusted_break = actual_break + speed_adjustment
    
    if uphill:
        adjusted_break *= 0.95 ** actual_slope  # Subtract 5% for each percent uphill
    else:
        adjusted_break *= 1.05 ** actual_slope  # Add 5% for each percent downhill
    
    return {
        '1% Break (inches)': round(one_percent_break, 2),
        'Actual Break (inches)': round(actual_break, 2),
        'Adjusted Break (inches)': round(adjusted_break, 2)
    }

@app.route('/')
def home():
    html = '''
    <!DOCTYPE html>
    <html>
    <head>
        <title>Golf Green Read Calculator</title>
        <style>
            body { font-family: Arial, sans-serif; max-width: 600px; margin: 50px auto; padding: 20px; }
            .form-group { margin-bottom: 15px; }
            label { display: block; margin-bottom: 5px; font-weight: bold; }
            input, select { width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 4px; }
            button { background: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer; }
            button:hover { background: #45a049; }
            .result { margin-top: 20px; padding: 15px; background: #f9f9f9; border-radius: 4px; }
        </style>
    </head>
    <body>
        <h1>Golf Green Read Calculator</h1>
        <form id="calcForm">
            <div class="form-group">
                <label for="paces">Paces:</label>
                <input type="number" id="paces" name="paces" step="0.1" required>
            </div>
            <div class="form-group">
                <label for="actual_slope">Actual Slope (%):</label>
                <input type="number" id="actual_slope" name="actual_slope" step="0.1" required>
            </div>
            <div class="form-group">
                <label for="green_speed">Green Speed:</label>
                <input type="number" id="green_speed" name="green_speed" step="0.1" required>
            </div>
            <div class="form-group">
                <label for="uphill">Direction:</label>
                <select id="uphill" name="uphill">
                    <option value="false">Downhill</option>
                    <option value="true">Uphill</option>
                </select>
            </div>
            <button type="submit">Calculate</button>
        </form>
        <div id="result" class="result" style="display: none;"></div>
        
        <script>
            document.getElementById('calcForm').addEventListener('submit', async (e) => {
                e.preventDefault();
                const formData = new FormData(e.target);
                const data = {
                    paces: parseFloat(formData.get('paces')),
                    actual_slope: parseFloat(formData.get('actual_slope')),
                    green_speed: parseFloat(formData.get('green_speed')),
                    uphill: formData.get('uphill') === 'true'
                };
                
                try {
                    const response = await fetch('/calculate', {
                        method: 'POST',
                        headers: {'Content-Type': 'application/json'},
                        body: JSON.stringify(data)
                    });
                    const result = await response.json();
                    
                    document.getElementById('result').innerHTML = `
                        <h3>Results:</h3>
                        <p><strong>1% Break:</strong> ${result['1% Break (inches)']} inches</p>
                        <p><strong>Actual Break:</strong> ${result['Actual Break (inches)']} inches</p>
                        <p><strong>Adjusted Break:</strong> ${result['Adjusted Break (inches)']} inches</p>
                    `;
                    document.getElementById('result').style.display = 'block';
                } catch (error) {
                    document.getElementById('result').innerHTML = '<p style="color: red;">Error: ' + error.message + '</p>';
                    document.getElementById('result').style.display = 'block';
                }
            });
        </script>
    </body>
    </html>
    '''
    return html

@app.route('/calculate', methods=['POST'])
def calculate():
    try:
        data = request.json
        if not data:
            return jsonify({'error': 'No JSON data provided'}), 400
        
        required_fields = ['paces', 'actual_slope', 'green_speed', 'uphill']
        for field in required_fields:
            if field not in data:
                return jsonify({'error': f'Missing required field: {field}'}), 400
        
        paces = data['paces']
        actual_slope = data['actual_slope']
        green_speed = data['green_speed']
        uphill = data['uphill']

        result = calculate_green_read(paces, actual_slope, green_speed, uphill)
        return jsonify(result)
    except Exception as e:
        return jsonify({'error': str(e)}), 500

if __name__ == '__main__':
    app.run(debug=True)