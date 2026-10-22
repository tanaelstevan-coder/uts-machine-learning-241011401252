# UTS Machine Learning – Linear & Logistic Regression

| | |
|---|---|
| **Nama** | TANAEL STEVAN SITOHANG |
| **NIM** | 241011401252 |
| **Kelas** | 05TPLM003 (Reg B) |
| **random_state** | 52 |

## Isi Repositori
- `tugas_UTS.ipynb` — notebook jawaban (sudah di-*Run All*, lengkap dengan output & grafik)
- `Ads_Data.csv`, `Email_Data.csv` — dataset

## Ringkasan Hasil

### Bagian A – Linear Regression (Ads_Data.csv, split 80/20)
- Persamaan (normal equation): **ŷ = 29.4375 + 9.0091 · BiayaIklan**
- Setiap kenaikan biaya iklan 1 juta Rp → penjualan naik ± 9,01 juta Rp.

| | MAE | MSE | RMSE | R² |
|---|---|---|---|---|
| Training | 4.3895 | 28.9508 | 5.3806 | 0.9489 |
| Testing | 4.9646 | 67.2248 | 8.1991 | 0.9224 |

- Gradient Descent (5000 iterasi): lr 0.001 → terlalu lambat (b=25.59, m=9.61); lr 0.02 → konvergen, identik dengan normal equation; lr 0.1 → divergen (overflow → inf/nan).
- Prediksi: 4.5 juta → 69.98 | 7 juta → 92.50 | 12 juta → 137.55 (ekstrapolasi, kurang bisa dipercaya).

### Bagian B – Logistic Regression (Email_Data.csv, split 75/25)
- P(Spam) = σ(−11.0478 + 0.9466·JumlahLink + 0.9278·KataPromo), log loss akhir 0.2137.
- Evaluasi data testing (threshold 0.5): Accuracy **0.8667**, Precision 0.875, Recall 0.875, F1 0.875 (TN=6, FP=1, FN=1, TP=7).
- Eksperimen threshold: 0.3 → P=0.70/R=0.875; 0.5 → P=0.875/R=0.875; 0.7 → P=1.00/R=0.625. **Dipilih threshold 0.7** (FP lebih merugikan).
- Prediksi email baru (threshold 0.7): E1 Bukan Spam, E2 Bukan Spam, E3 Spam, E4 Spam.

### Bagian C & Bonus
- Jawaban konsep ada di notebook.
- Bonus: sklearn `LinearRegression` identik dengan implementasi sendiri; `LogisticRegression` berbeda karena regularisasi L2 default (C=1.0), akurasi testing tetap sama (0.8667).
