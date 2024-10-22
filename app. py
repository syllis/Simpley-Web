from flask import Flask, render_template, request

app = Flask(__name__)

# Function to calculate volume
def calculate_isipadu(bentuk, jejari=0, tinggi=0, panjang=0, lebar=0, sendeng=0):
    if bentuk == 'kon':
        return (1/3) * (22/7) * (jejari**2) * tinggi
    elif bentuk == 'sfera':
        return (4/3) * (22/7) * (jejari**3)
    elif bentuk == 'silinder':
        return (22/7) * (jejari**2) * tinggi
    elif bentuk == 'semibulatan':
        return ((4/3) * (22/7) * (jejari**3)) / 2
    elif bentuk == 'kuboid':
        return panjang * lebar * tinggi
    elif bentuk == 'piramid':
        return (1/3) * (panjang**2) * tinggi
    else:
        return "Bentuk tidak dikenali!"

# Function to calculate surface area
def calculate_luas_permukaan(bentuk, jejari=0, tinggi=0, panjang=0, lebar=0, sendeng=0):
    if bentuk == 'sfera':
        return 4 * (22/7) * (jejari**2)
    elif bentuk == 'semibulatan':
        return 2 * (22/7) * (jejari**2)
    elif bentuk == 'silinder':
        return (2 * (22/7) * (jejari**2)) + (2 * (22/7) * jejari * tinggi)
    elif bentuk == 'kuboid':
        return (2 * panjang * lebar) + (2 * lebar * tinggi) + (2 * panjang * tinggi)
    elif bentuk == 'kon':
        return (22/7) * (jejari**2) + (22/7) * jejari * sendeng
    elif bentuk == 'piramid':
        return (panjang**2) + (4 * (1/2) * panjang * sendeng)
    else:
        return "Bentuk tidak dikenali!"

@app.route('/')
def home():
    return '''
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #e9ecef;
            color: #333;
            padding: 20px;
            text-align: center;
        }
        h1 {
            font-size: 2.5em;
            color: #5cb85c;
            margin-bottom: 20px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
        }
        form {
            background: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            margin: 0 auto;
            width: 300px;
            transition: transform 0.3s ease;
        }
        form:hover {
            transform: scale(1.02);
        }
        select, input {
            margin: 10px 0;
            padding: 10px;
            width: 100%;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }
        input[type="submit"] {
            background: #5cb85c;
            color: #fff;
            border: none;
            cursor: pointer;
            font-size: 1.1em;
            transition: background 0.3s ease;
        }
        input[type="submit"]:hover {
            background: #4cae4c;
        }
        label {
            font-weight: bold;
            display: block;
            margin-top: 10px;
        }
    </style>
    <h1>SIMPLEY</h1>
    <form method="post" action="/calculate">
        <label>Pilih Kiraan:</label>
        <select name="pilihan">
            <option value="isipadu">Isipadu</option>
            <option value="luas_permukaan">Luas Permukaan</option>
        </select>
        <label>Pilih Bentuk:</label>
        <select name="bentuk">
            <option value="kon">Kon</option>
            <option value="sfera">Sfera</option>
            <option value="silinder">Silinder</option>
            <option value="semibulatan">Semibulatan</option>
            <option value="kuboid">Kuboid</option>
            <option value="piramid">Piramid</option>
        </select>
        <label>Jejari:</label>
        <input type="number" name="jejari" step="any" placeholder="Masukkan jejari">
        <label>Tinggi:</label>
        <input type="number" name="tinggi" step="any" placeholder="Masukkan tinggi">
        <label>Panjang:</label>
        <input type="number" name="panjang" step="any" placeholder="Masukkan panjang">
        <label>Lebar:</label>
        <input type="number" name="lebar" step="any" placeholder="Masukkan lebar">
        <label>Sendeng:</label>
        <input type="number" name="sendeng" step="any" placeholder="Masukkan sendeng">
        <input type="submit" value="Kira">
    </form>
    '''

@app.route('/calculate', methods=['POST'])
def calculate():
    try:
        bentuk = request.form['bentuk']
        pilihan = request.form['pilihan']
        jejari = float(request.form.get('jejari', 0.0) or 0.0)
        tinggi = float(request.form.get('tinggi', 0.0) or 0.0)
        panjang = float(request.form.get('panjang', 0.0) or 0.0)
        lebar = float(request.form.get('lebar', 0.0) or 0.0)
        sendeng = float(request.form.get('sendeng', 0.0) or 0.0)

        if pilihan == 'isipadu':
            hasil = calculate_isipadu(bentuk, jejari, tinggi, panjang, lebar, sendeng)
        elif pilihan == 'luas_permukaan':
            hasil = calculate_luas_permukaan(bentuk, jejari, tinggi, panjang, lebar, sendeng)
        else:
            hasil = "Pilihan tidak sah!"

        return f"""
            <style>
                body {{
                    font-family: Arial, sans-serif;
                    background-color: #e9ecef;
                    color: #333;
                    padding: 20px;
                    text-align: center;
                }}
                .result-container {{
                    background: #fff;
                    padding: 20px;
                    border-radius: 10px;
                    box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
                    margin: 20px auto;
                    width: 300px;
                }}
                .result-title {{
                    font-size: 1.5em;
                    color: #5cb85c;
                    margin-bottom: 10px;
                }}
                .result-value {{
                    font-size: 1.2em;
                    font-weight: bold;
                    color: #333;
                }}
                .back-button {{
                    margin-top: 20px;
                    padding: 10px 20px;
                    background-color: #5cb85c;
                    color: white;
                    border: none;
                    border-radius: 5px;
                    cursor: pointer;
                    font-size: 1em;
                    transition: background 0.3s ease;
                }}
                .back-button:hover {{
                    background-color: #4cae4c;
                }}
            </style>
            <div class="result-container">
                <h2 class="result-title">Hasil</h2>
                <p class="result-value">{hasil}</p>
                <form action="/" method="get">
                    <button type="submit" class="back-button">Kira Lagi</button>
                </form>
            </div>
        """
    except ValueError:
        return """
            <style>
                body {
                    font-family: Arial, sans-serif;
                    background-color: #e9ecef;
                    color: #333;
                    padding: 20px;
                    text-align: center;
                }
                .error-container {
                    background: #fff;
                    padding: 20px;
                    border-radius: 10px;
                    box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
                    margin: 20px auto;
                    width: 300px;
                }
                .error-title {
                    font-size: 1.5em;
                    color: #d9534f;
                    margin-bottom: 10px;
                }
                .error-message {
                    font-size: 1.1em;
                    color: #333;
                }
                .back-button {
                    margin-top: 20px;
                    padding: 10px 20px;
                    background-color: #5cb85c;
                    color: white;
                    border: none;
                    border-radius: 5px;
                    cursor: pointer;
                    font-size: 1em;
                    transition: background 0.3s ease;
                }
                .back-button:hover {
                    background-color: #4cae4c;
                }
            </style>
            <div class="error-container">
                <h2 class="error-title">Ralat!</h2>
                <p class="error-message">Input tidak sah. Sila masukkan nombor yang betul.</p>
                <form action="/" method="get">
                    <button type="submit" class="back-button">Kira Lagi</button>
                </form>
            </div>
        """

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000, debug=True)
