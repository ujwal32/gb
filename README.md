# 🗑️ Garbage Classifier (Recyclable vs Non-Recyclable)

A full-stack machine learning web application that classifies garbage images into 12 categories using a trained MobileNetV2 model.

Built with:
- **FastAPI** (backend & frontend)
- **TensorFlow/Keras** (model training)
- **Google OAuth 2.0** (authentication)
- **SQLite + SQLModel** (token tracking database)
- **OpenWeatherMap API** (real-time Air Quality Index)

---

## ✨ Features

✅ Upload an image → predicts the garbage class  
✅ Google OAuth login system  
✅ Each user starts with **1000 tokens** → **3 tokens deducted per prediction**  
✅ Shows remaining tokens + prediction result  
✅ Live **Air Quality Index (AQI)** bar from OpenWeatherMap  
✅ Responsive frontend using Jinja2 templates

---


## 🔐 Authentication Setup

1️⃣ Create Google OAuth 2.0 credentials in [Google Cloud Console](https://console.cloud.google.com/apis/credentials)

- Application Type: **Web Application**
- Authorized redirect URI: http://localhost:8000/auth

---

### 📝 Model Training
The model was trained in Google Colab using:

✅ MobileNetV2 (pretrained on ImageNet)
✅ Data augmentation (zoom, rotation, etc.)
✅ Dataset: mostafaabla/garbage-classification from KaggleHub

Final model exported as garbage_classifier.h5 and placed under /model folder.

12 classes: battery, biological, brown-glass, cardboard, clothes,
green-glass, metal, paper, plastic, shoes, trash, white-glass

---

### 🔍 Class Prediction Flow

User uploads image

FastAPI saves image temporarily

Image is resized → normalized → passed to model

Model predicts class index → maps to class name

3 tokens deducted → result displayed

---

### 📊 Air Quality Integration

Uses OpenWeatherMap Air Pollution API to fetch real-time AQI for a fixed location (customizable).

Displays AQI at top of every page.

---

### 🔑 Token System
Each new user starts with 1000 tokens

Each prediction deducts 3 tokens

Remaining tokens displayed on dashboard and result page

Token balance stored in SQLite (using SQLModel ORM)

---

### Trained_Model_Link:
https://colab.research.google.com/drive/1bWcOI0bAtcl-RNhpHCTmChenqAeX9mR4?usp=sharing
