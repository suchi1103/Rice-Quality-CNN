# Rice-Quality-CNN-
An AI and Deep Learning system using CNNs to automate rice quality assessment and predict shelf life based on environmental factors (moisture, temperature, and humidity) for precision agriculture.


# Leveraging Artificial Intelligence and Deep Learning for Rice Quality Analysis and Shelf-Life Prediction in Precision Agriculture

## 📌 Project Overview
This repository contains the complete implementation of an intelligent, data-driven agricultural automation system designed to optimize post-harvest rice management. Traditional manual crop inspection is subjective, slow, and unscalable. This project implements an automated, non-destructive system utilizing **2D Convolutional Neural Networks (CNNs)** to classify rice varieties and detect physical defects via computer vision. Additionally, it integrates environmental data (moisture, temperature, humidity) using **Machine Learning Regression and Time-Series Models** to dynamically forecast the storage shelf life of different rice grains.

---

## 🚀 Key Features
* **Image-Based Variety Classification:** Automated grading and classification of 5 distinct rice varieties (Arborio, Basmati, Ipsala, Jasmine, and Karacadag).
* **Automated Defect Detection:** Computer-vision-driven localization of broken grains, discoloration, chalkiness, and organic contaminants.
* **Real-Time Shelf-Life Prediction:** Employs predictive ML regression models to estimate continuous storage durability based on live environmental variables.
* **Precision Post-Harvest Storage Optimization:** Provides early triggers and alerts to mitigate fungal growth and minimize supply chain food waste.

---

## 📊 Dataset & Pipeline Architecture
The system processes data through two parallel analytical pipelines:

### 1. Computer Vision Pipeline (Rice Quality)
* **Dataset Size:** 75,000 high-resolution images distributed evenly across 5 grain classes.
* **Data Split:** Strict 80% Training (60,000 images), 10% Validation (7,500 images), and 10% Testing (7,500 images).
* **Feature Extraction:** Spatial tracking of structural aspect ratios, grain contours, lengths, surface textures, and opacity.

### 2. Tabular/Time-Series Pipeline (Shelf Life)
* Evaluates continuous environmental features: Temperature (°C), Relative Humidity (%), Grain Moisture Content (%), Airflow Rate (m³/h), and Light Exposure (hrs).
* Compares structural storage efficiency between Airtight Bins vs. Plastic Bags, and Bulk vs. Individual packaging configurations.

---

## 🛠️ Model Architecture & Technical Stack

### Computer Vision (Deep Learning)
A custom sequential **2D Convolutional Neural Network (2D CNN)** built on TensorFlow/Keras with **267,397 total trainable parameters**:
* **Input Layer:** Normalized image inputs (48x48x3 RGB spatial dimensions).
* **Conv Block 1:** 2D Convolution (32 filters, 3x3 kernel) + MaxPooling2D (2x2 stride).
* **Conv Block 2:** 2D Convolution (64 filters, 3x3 kernel) + MaxPooling2D (2x2 stride).
* **Dense Flattening Layer:** Converts multi-dimensional feature maps into a 7,744-element vector.
* **Fully Connected Layer:** Dense layer with 32 units and ReLU activation.
* **Softmax Output Layer:** 5 output units mapping to the distinct rice variety categories.

### Predictive Analytics (Machine Learning)
* **Random Forest Regression & Support Vector Regression (SVR):** Utilized for estimating continuous shelf-life bounds by monitoring linear/non-linear environmental thresholds.
* **Long Short-Term Memory (LSTM) Networks:** Captures sequential, time-varying storage dependencies across historical seasonal fluctuations.

---

## 📈 System Metrics & Performance Evaluations

### Deep Learning Model Validation Metrics
The core 2D CNN model achieves exceptionally high generalization on unseen validation benchmarks:
* **Training Classification Accuracy:** 98.88% (Optimized via Callback scheduling).
* **Validation/Test Accuracy:** 99.16%.
* **Receiver Operating Characteristic (ROC):** Reached a perfect Area Under the Curve (**AUC = 1.00**) across all evaluated target classes.

### Per-Class Classification Report Benchmarks

| Rice Variety Class | Precision | Recall | F1-Score | Support Size |
| :--- | :---: | :---: | :---: | :---: |
| **Arborio** | 0.98 | 0.99 | 0.99 | 1,500 |
| **Basmati** | 1.00 | 0.99 | 0.99 | 1,500 |
| **Ipsala** | 1.00 | 1.00 | 1.00 | 1,500 |
| **Jasmine** | 0.99 | 0.99 | 0.99 | 1,500 |
| **Karacadag** | 0.99 | 0.99 | 0.99 | 1,500 |
| **Macro Average** | **0.99** | **0.99** | **0.99** | **7,500** |
| **Weighted Average** | **0.99** | **0.99** | **0.99** | **7,500** |
