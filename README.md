# NLP_turkish_web
# Fixed-Split and Reproducible Transformer Comparison for Three-Class Sentiment Analysis on Turkish Movie Reviews

This repository contains the code, fixed split assignment file, and SHA-256 fingerprint for the paper submitted to SIU 2026.

> ⚠️ **Anonymous review in progress.** Author information will be added upon acceptance.

---

## Overview

This study compares BERTurk and ConvBERTurk for three-class sentiment analysis (positive / neutral / negative) on Turkish movie reviews under a fixed train-test split, and examines sensitivity to label boundary definitions.

---

## Dataset

- **Total instances:** 23,605 (after deduplication and short-text filtering)
- **Split:** Fixed 80–20 → 18,884 train / 4,721 test
- **SHA-256 fingerprint:** `f0a57be...`
- **Labeling Scheme A:** 1–3 negative, 4–6 neutral, 7–10 positive
- **Labeling Scheme B:** 1–4 negative, 5–6 neutral, 7–10 positive

---

## Models

| Model | HuggingFace ID |
|-------|---------------|
| BERTurk | `dbmdz/bert-base-turkish-cased` |
| ConvBERTurk | `dbmdz/convbert-base-turkish-cased` |

---

## Training Parameters

| Parameter | Value |
|-----------|-------|
| Learning rate | 2×10⁻⁵ |
| Weight decay | 0.01 |
| Warmup ratio | 0.10 |
| Epochs | 3 |
| Train / Eval batch size | 16 / 32 |
| Max sequence length | 256 |
| Seeds | 42, 43, 44 |

---

## Results (Aggregated, mean ± std over 3 seeds)

| Scheme | Model | Accuracy | Macro F1 | Weighted F1 | Balanced Acc. | MCC |
|--------|-------|----------|----------|-------------|---------------|-----|
| A | ConvBERTurk | .860±.005 | .599±.004 | .877±.004 | .664±.011 | .470±.009 |
| A | BERTurk | .849±.003 | .585±.004 | .869±.002 | .661±.005 | .445±.006 |
| B | ConvBERTurk | .851±.005 | .587±.010 | .871±.003 | .657±.011 | .449±.009 |
| B | BERTurk | .834±.011 | .570±.007 | .859±.007 | .656±.011 | .423±.009 |

---

## Repository Structure
```
├── data/
│   └── split_assignment.csv   # Fixed train/test split assignments
├── src/
│   └── train.py               # Training and evaluation script
├── fingerprint.txt            # SHA-256 fingerprint of the dataset
└── requirements.txt
```

---

## Requirements
```bash
pip install -r requirements.txt
```

---

## Citation

Will be added upon acceptance.
