# Deploying a Flask App on Vercel
![Screenshot 2025-03-10 160418](https://github.com/user-attachments/assets/2f7cdecd-40e0-43a9-b746-05a61c343482)

This guide will help you set up and deploy a Flask application using Vercel.

## Prerequisites
- Python installed
- Node.js installed (for Vercel CLI)
- PyCharm or any preferred code editor
- A Vercel account

## Steps to Set Up and Deploy

### 1. Install Flask
Open the terminal and run:
```sh
pip install Flask
```

### 2. Create `app.py`
Inside your project folder, create a file named `app.py` and add the following code:
```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/data')
def get_data():
    return jsonify({"message": "Hello from Flask on Vercel!"})

if __name__ == '__main__':
    app.run(debug=True)
```

### 3. Run and Test Locally
Run the following command in the terminal:
```sh
python app.py
```
Then, open your browser and go to:
```
http://127.0.0.1:5000/api/data
```

### 4. Create `vercel.json`
Create a `vercel.json` file in your project folder and add:
```json
{
  "builds": [{ "src": "app.py", "use": "@vercel/python" }],
  "routes": [{ "src": "/(.*)", "dest": "app.py" }]
}
```

### 5. Prepare for Deployment
Run the following command to generate `requirements.txt`:
```sh
pip freeze > requirements.txt
```

### 6. Install Vercel CLI
To install Vercel CLI globally, run:
```sh
npm install -g vercel
```

### 7. Deploy to Vercel
Run the deployment command:
```sh
vercel
```
Follow the instructions and select the correct settings.

### 8. Test the Deployed App
Once deployed, visit your app’s URL and test the endpoint:
```
https://your-vercel-app-url/api/data
```

### 9. Update and Redeploy
If you make changes to your code, you can deploy updates by running:
```sh
vercel --prod
```
Alternatively, if your project is linked to GitHub, just commit and push the changes—Vercel will automatically redeploy.

---
### 🎉 Congratulations! Your Flask app is live on Vercel! 🎉

