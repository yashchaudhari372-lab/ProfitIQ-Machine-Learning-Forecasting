# 📈 ProfitIQ Forecasting | Machine Learning & Retail Analytics

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python) ![Flask](https://img.shields.io/badge/Flask-Web%20App-black?logo=flask) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Gradient%20Boosting-orange?logo=scikitlearn) ![Vercel](https://img.shields.io/badge/Deployment-Vercel-black?logo=vercel)

**An end-to-end machine learning web application for estimating retail store profit using a Gradient Boosting Regressor, with an interactive analytics dashboard.**

🔗 **[Live Demo](https://store-profit-prediction.vercel.app/)** · **[GitHub Repository](https://github.com/yashchaudhari372-lab/Store_Profit_Prediction)**

## 📌 Project Overview

Retail profitability depends on transaction characteristics such as sales value, discount, quantity, product category, shipping method, and location. This project provides an interactive interface where users enter retail transaction details and receive a predicted profit value from a saved machine learning model.

The application uses a **Gradient Boosting Regressor** loaded from `Gradient_model.pkl` and a **Flask** backend. Its interface includes interactive visualizations powered by Chart.js and styling with Tailwind CSS.

> **Important:** This application is a demonstration of predictive analytics. Predicted profit is an estimate, not a guaranteed financial outcome..

## ✨ Key Features

- Predicts a numerical profit estimate for a retail transaction.
- Accepts **13 transaction and customer-related input features**.
- Provides a responsive, interactive analytics dashboard.
- Displays charts to explore input factors and prediction-related visuals.
- Offers multiple dashboard themes.
- Exposes a JSON-based `/predict` endpoint for integration.
- Includes a deployed web demo on Vercel.

## 🧠 Machine Learning Approach

**Algorithm:** Gradient Boosting Regressor (supervised regression)

Gradient boosting builds an ensemble of decision trees sequentially. Each new tree attempts to reduce errors made by the preceding ensemble, enabling the model to capture nonlinear relationships between retail transaction attributes and profit.

### Prediction Workflow

```text
User enters retail transaction details
                 ↓
Input fields converted to numeric feature values
                 ↓
13 features arranged in the model's expected order
                 ↓
Saved Gradient Boosting model predicts profit
                 ↓
Predicted value returned by Flask API
                 ↓
Dashboard displays the result and visualizations
```

### Input Features

| # | Feature | Description |
|---|---|---|
| 1 | Ship Mode | Shipping method (encoded) |
| 2 | Customer Name | Customer identifier (encoded) |
| 3 | Segment | Customer segment (encoded) |
| 4 | Country | Country (encoded) |
| 5 | City | City (encoded) |
| 6 | State | State (encoded) |
| 7 | Region | Sales region (encoded) |
| 8 | Category | Product category (encoded) |
| 9 | Sub-Category | Product subcategory (encoded) |
| 10 | Product Name | Product identifier (encoded) |
| 11 | Sales | Transaction sales amount |
| 12 | Quantity | Number of units |
| 13 | Discount | Applied discount fraction |

**Note:** Encoded categorical inputs must match the encoding used during model training. The repository does not include the original training notebook or encoding mappings, so reproducibility of training is not yet documented.

## 🛠️ Tech Stack

| Layer | Technologies |
|---|---|
| Language | Python |
| ML | Scikit-learn, Gradient Boosting Regressor |
| Numerical computing | NumPy |
| Backend | Flask |
| Model serialization | Pickle (`.pkl`) |
| Frontend | HTML, JavaScript, Tailwind CSS, Alpine.js |
| Visualizations | Chart.js |
| Deployment | Vercel |

## 📁 Repository Structure

```text
Store_Profit_Prediction/
├── app.py                 # Flask app, dashboard HTML, and prediction API
├── Gradient_model.pkl     # Saved regression model
├── requirements.txt       # Python dependencies
└── README.md              # Project documentation
```

## ⚙️ Installation & Local Setup

**1. Clone the repository**

```bash
git clone https://github.com/yashchaudhari372-lab/Store_Profit_Prediction.git
cd Store_Profit_Prediction
```

**2. Create and activate a virtual environment (recommended)**

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

macOS / Linux:

```bash
source .venv/bin/activate
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

**4. Start the Flask application**

```bash
python app.py
```

**5. Open your browser**

```text
http://127.0.0.1:5000/
```

> Only load `.pkl` files from sources you trust. Pickle deserialization can execute code.

## 🔌 Prediction API

**Endpoint:** `POST /predict`  
**Content-Type:** `application/json`

Example request (numeric categorical values are illustrative only):

```bash
curl -X POST http://127.0.0.1:5000/predict \
  -H "Content-Type: application/json" \
  -d '{"features":{"Ship Mode":0,"Customer Name":10,"Segment":0,"Country":0,"City":20,"State":10,"Region":1,"Category":0,"Sub-Category":3,"Product Name":100,"Sales":250.0,"Quantity":3,"Discount":0.1}}'
```

Example response format (prediction value varies with the model and inputs):

```json
{
  "status": "success",
  "prediction": 0.0
}
```

> **Model availability:** The current application code has a mathematical fallback if the saved model cannot be loaded. A response in fallback mode is **not** a Gradient Boosting model prediction. Check server logs to confirm the model loaded successfully before interpreting outputs as ML predictions.

## 📊 Model Evaluation

The repository includes the serialized model but does not publish a verified held-out test evaluation. Do not present fabricated scores.

| Regression Metric | Verified Result |
|---|---|
| R² Score | 89% |

For reproducible evaluation, add the training dataset, preprocessing/encoding pipeline, train-test split details, and an evaluation notebook or script. Compare predicted and actual profit on a held-out test set.

## 💼 Business Use Cases

- Estimate transaction-level profitability for scenario analysis.
- Explore how discounts, quantities, and sales amounts relate to predicted profit.
- Support retail reporting and exploratory business analytics.
- Demonstrate an end-to-end regression deployment workflow.

## 🚀 Future Improvements

- Publish training and evaluation notebooks with reproducible preprocessing.
- Save categorical encoders together with the trained model.
- Add verified MAE, RMSE, and R² results.
- Validate API inputs and remove the fallback from production predictions.
- Add model explainability using feature importance or SHAP.
- Add real-versus-predicted plots and business-friendly profit units.
- Include application screenshots and automated tests.

## 👨‍💻 Developer

**Yash Chaudhari**  
Aspiring Data Scientist & Data Analyst

- **GitHub:** https://github.com/yashchaudhari372-lab
- **LinkedIn:** https://www.linkedin.com/in/yashchaudhari08/

---

⭐ If you find this project useful, consider starring the repository.
