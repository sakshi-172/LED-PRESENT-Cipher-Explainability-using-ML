# 🔐 LED & PRESENT Cipher Explainability using ML

This project investigates **cryptographic pattern analysis** through the lens of machine learning, focusing on the **explainability of lightweight block ciphers**—**LED** and **PRESENT**. 
We evaluate **multi-class classifiers** trained to distinguish between ciphertexts generated using **different S-box configurations**, and provide interpretability using **SHAP** and **LIME**.

---

## 📌 Project Objective

> To classify and interpret 64-bit ciphertexts generated using **LED and PRESENT lightweight block ciphers** under **varied S-box settings**, using ML models like **Artificial Neural Networks (ANN)** and **1D Convolutional Neural Networks (CNN)**.

---

## ⚙️ Cipher Overview

### 🔸 LED Cipher
- **Block size:** 64 bits  
- **Key size:** 128 bits (fixed)  
- **S-box:** 4-bit (16 entries)

### 🔸 PRESENT Cipher
- **Block size:** 64 bits  
- **Key size:** 80 bits (fixed)  
- **S-box:** 4-bit (16 entries)

Both ciphers follow Substitution-Permutation Network (SPN) structures.

---

## 🧪 Dataset Generation

For **both ciphers (LED & PRESENT)**, we perform the following steps:

### ✅ Step 1: Ciphertext Generation (Label 0)
- Randomly generate `2^17` (131072) unique **64-bit plaintexts**.
- Encrypt them using the **fixed key** and the **original S-box**.
- Store the ciphertexts in CSV format with label **`0`**.

### ✅ Step 2: S-box Variant 1 (Label 1)
- Swap S-box values:  
  `S(3) = B` and `S(C) = 4` → `S(3) = 4`, `S(C) = B`
- Encrypt same plaintexts with modified S-box.
- Store resulting ciphertexts with label **`1`**.

### ✅ Step 3: S-box Variant 2 (Label 2)
- Replace value:  
  `S(3) = B` → `S(3) = 4`
- Encrypt again and label all ciphertexts with **`2`**.


---

## 🤖 Machine Learning Models

### 🔹 1. Artificial Neural Network (ANN)
- Input: 64 features (bit-wise)
- Architecture: Fully connected layers with ReLU and Softmax
- Optimizer: Adam  
- Loss: Categorical Crossentropy

### 🔹 2. 1D Convolutional Neural Network (CNN)
- Input reshaped to `(64, 1)`
- Layers: Conv1D → GlobalMaxPooling → Dense → Softmax
- Optimized for learning local bitwise patterns

---

## 🧠 Explainability: SHAP & LIME

### 🔸 SHAP (SHapley Additive exPlanations)
- Used to visualize **bitwise importance** of features for each class prediction.
- `shap.summary_plot()` shows global impact of each bit.

### 🔸 LIME (Local Interpretable Model-Agnostic Explanations)
- Provides instance-level explanations.
- Identifies **important bits** responsible for each prediction.

---

## 📣 Key Highlights
- ✅ End-to-end ML pipeline from ciphertext generation → classification → explainability
- ✅ Cipher-specific encryption logic adhering to the LED & PRESENT cipher structure
- ✅ Analysis of S-box vulnerabilities through ML explainability tools
- ✅ Clear dataset labeling and class separation

---

## 📬 Contact / Citation
If you use or build upon this project in your research or applications, please consider citing it or giving it a ⭐ on GitHub. Your support helps increase the visibility and impact of this work.

### Project Title:
**"LED & PRESENT Cipher Explainability using ML"**
Developed as part of Summer Internship at Scientific Analysis Group (SAG), DRDO, New Delhi

👩‍💻 **Developer:** Sakshi
- 🎓 B.Tech (Information Technology)
- 🏫 Maharaja Surajmal Institute of Technology, GGSIPU
- 📍 Delhi, India
