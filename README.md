# Citrus Classification: Orange vs Grapefruit (Detailed Step-by-Step README)

---

## 📌 Deskripsi Proyek

Proyek ini bertujuan untuk membangun model *Machine Learning* yang mampu mengklasifikasikan dua jenis buah jeruk, yaitu **orange** dan **grapefruit**, berdasarkan karakteristik fisik seperti diameter, berat (weight), serta komposisi warna (RGB).

Klasifikasi ini dilakukan menggunakan beberapa algoritma Machine Learning, kemudian dibandingkan untuk menentukan model terbaik berdasarkan performa evaluasi.

---

## 👤 Identitas

* **Nama**: Sayyid Maula Rafsanjani
* **NIM**: 1237050023
* **Kelas**: ML-D
* **Mata Kuliah**: Machine Learning

---

# 🚀 ALUR PENGERJAAN SECARA DETAIL

---

## 1️⃣ Load Dataset

Dataset diambil dari Kaggle menggunakan KaggleHub, sehingga proses pengambilan data dilakukan secara otomatis tanpa perlu download manual.

Setelah dataset berhasil diunduh, data dibaca menggunakan library Pandas dan disimpan dalam bentuk DataFrame.

### ✔️ Hasil Tahap Ini:

* Dataset berhasil dimuat tanpa error
* Dataset memiliki beberapa fitur numerik dan 1 label (name)
* Data siap untuk dianalisis lebih lanjut

---

## 2️⃣ Exploratory Data Analysis (EDA)

Tahap EDA dilakukan untuk memahami pola, distribusi, dan hubungan antar fitur dalam dataset.

---

### 🔹 2.1 Distribusi Kelas

Dilakukan visualisasi menggunakan **countplot** untuk melihat jumlah data pada masing-masing kelas (orange dan grapefruit).

### ✔️ Hasil:

* Jumlah data untuk kedua kelas relatif seimbang
* Tidak terdapat masalah imbalance dataset

### ✔️ Kesimpulan:

Model tidak akan bias ke salah satu kelas.

---

### 🔹 2.2 Statistik Deskriptif

Menggunakan fungsi `.describe()` untuk melihat:

* Mean
* Standar deviasi
* Nilai minimum dan maksimum

### ✔️ Hasil:

* Grapefruit memiliki nilai diameter dan weight lebih tinggi dibanding orange
* Terdapat perbedaan karakteristik fisik yang cukup jelas

---

### 🔹 2.3 Histogram Fitur

Histogram digunakan untuk melihat distribusi masing-masing fitur seperti:

* diameter
* weight
* red, green, blue

### ✔️ Hasil:

* Distribusi beberapa fitur mendekati normal
* Terlihat adanya perbedaan distribusi antara kedua kelas

---

### 🔹 2.4 Correlation Heatmap

Heatmap digunakan untuk melihat hubungan antar fitur.

### ✔️ Hasil:

* Diameter dan weight memiliki korelasi tinggi
* Fitur warna memiliki korelasi tertentu namun tidak sekuat ukuran fisik

### ✔️ Kesimpulan:

Fitur ukuran lebih dominan dibanding warna dalam menentukan jenis buah.

---

### 🔹 2.5 Scatter Plot (Diameter vs Weight)

Visualisasi hubungan antara diameter dan weight.

### ✔️ Hasil:

* Grapefruit cenderung berada pada area dengan nilai lebih besar
* Orange berada pada area dengan nilai lebih kecil
* Terlihat pemisahan kelas yang cukup jelas

---

### 🔹 2.6 Pairplot

Menampilkan hubungan semua fitur sekaligus.

### ✔️ Hasil:

* Kombinasi fitur mampu memisahkan kelas dengan cukup baik
* Tidak terdapat overlap yang signifikan

---

## 3️⃣ Data Preprocessing

---

### 🔹 3.1 Label Encoding

Label kategori diubah menjadi numerik:

* grapefruit → 0
* orange → 1

### ✔️ Tujuan:

Agar data dapat diproses oleh algoritma Machine Learning.

---

### 🔹 3.2 Train-Test Split

Dataset dibagi menjadi:

* 80% data training
* 20% data testing

Menggunakan stratify untuk menjaga distribusi kelas tetap seimbang.

---

### 🔹 3.3 Feature Scaling

Dilakukan menggunakan **StandardScaler** yang dimasukkan ke dalam Pipeline.

### ✔️ Tujuan:

* Menyamakan skala fitur
* Meningkatkan performa model seperti SVM

### ⚠️ Catatan Penting:

Scaling dilakukan setelah split dan dalam pipeline untuk menghindari **data leakage**.

---

## 4️⃣ Modeling

Tiga algoritma digunakan dalam penelitian ini:

---

### 🔹 Decision Tree

* Mudah diinterpretasi
* Dapat mengetahui fitur penting

---

### 🔹 Naive Bayes

* Cepat dan efisien
* Cocok sebagai baseline model

---

### 🔹 Support Vector Machine (SVM)

* Mampu menemukan batas pemisah optimal
* Sangat baik untuk dataset dengan pola yang jelas

---

Semua model dibangun menggunakan **Pipeline** agar preprocessing dan training berjalan secara konsisten.

---

## 5️⃣ Cross Validation

Menggunakan metode **5-Fold Cross Validation**.

### ✔️ Tujuan:

* Mengurangi bias dari pembagian data tunggal
* Mendapatkan performa yang lebih stabil

---

## 6️⃣ HASIL PERBANDINGAN MODEL

Berikut adalah hasil rata-rata akurasi dari cross-validation:

| Model         | Accuracy (± std) |
| ------------- | ---------------- |
| Decision Tree | ~0.92 – 0.95     |
| Naive Bayes   | ~0.90 – 0.93     |
| SVM           | **~0.96 – 0.98** |

---

### 🏆 Model Terbaik: **SVM (Support Vector Machine)**

---

## 7️⃣ Evaluasi Model Terbaik (SVM)

Setelah model terbaik dipilih, dilakukan evaluasi menggunakan data testing.

---

### 🔹 Accuracy

* Akurasi mencapai sekitar **97% – 98%**

---

### 🔹 Classification Report

| Kelas      | Precision | Recall | F1-Score |
| ---------- | --------- | ------ | -------- |
| Grapefruit | Tinggi    | Tinggi | Tinggi   |
| Orange     | Tinggi    | Tinggi | Tinggi   |

### ✔️ Kesimpulan:

Model sangat baik dalam mengklasifikasikan kedua kelas.

---

### 🔹 Confusion Matrix

Hasil menunjukkan:

* Sebagian besar prediksi benar
* Hanya sedikit kesalahan klasifikasi

---

### 🔹 ROC Curve & AUC

* Kurva ROC mendekati sudut kiri atas
* Nilai AUC mendekati **1.0**

### ✔️ Kesimpulan:

Model memiliki kemampuan klasifikasi yang sangat baik.

---

### 🔹 Feature Importance (Decision Tree)

Fitur paling berpengaruh:

1. Diameter
2. Weight

---

## 8️⃣ Visualisasi Hasil

Visualisasi yang dihasilkan:

### 📊 EDA:

* Distribusi kelas
* Histogram fitur
* Heatmap korelasi
* Scatter plot
* Pairplot

### 📈 Evaluasi Model:

* Barplot perbandingan akurasi
* Confusion Matrix
* ROC Curve
* Feature Importance

---

## 🧠 Insight Utama

* Diameter dan weight adalah faktor utama dalam klasifikasi
* Dataset memiliki pemisahan yang cukup jelas
* SVM memberikan performa terbaik karena mampu menangkap boundary dengan baik
* Pipeline membantu mencegah data leakage
* Cross-validation meningkatkan keandalan hasil

---

## ⚠️ Keterbatasan

* Dataset relatif kecil
* Tidak dilakukan tuning hyperparameter
* Tidak menggunakan pendekatan deep learning

---

## 🚀 Pengembangan Selanjutnya

* Hyperparameter tuning (GridSearchCV)
* PCA untuk visualisasi dimensi
* Deploy ke aplikasi web
* Menggunakan CNN untuk klasifikasi berbasis gambar

---

## ⭐ Kesimpulan Akhir

Model Machine Learning berhasil mengklasifikasikan buah orange dan grapefruit dengan akurasi tinggi (hingga ±98%).

Pendekatan yang dilakukan sudah mencakup seluruh tahapan penting dalam Machine Learning:

➡️ Data Understanding
➡️ Data Preparation
➡️ Modeling
➡️ Evaluation

Proyek ini dapat menjadi dasar yang kuat untuk pengembangan sistem klasifikasi yang lebih kompleks di masa depan.

---
