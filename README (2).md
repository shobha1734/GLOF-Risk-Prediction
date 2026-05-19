# ❄️ GLOF Risk Predictor

> AI-powered Glacial Lake Outburst Flood detection using satellite imagery and deep learning.

**Shobha Panthi** · DATA 690 · UMBC · 2026

🔗 **[Try the Live App](https://huggingface.co/spaces/shobha1734/Glof-Risk-predictor)**

---

## The Problem

15 million people worldwide live at risk from glacial lake outburst floods. When natural ice or debris dams fail, entire villages are destroyed in minutes. Climate change is making this worse every year — and we cannot monitor thousands of lakes manually.

**This project uses AI to do it automatically.**

---

## What It Does

Upload any satellite image of a glacial lake → get an instant flood risk assessment in under 1 second — for free.

| Risk Level | Probability | Action |
|---|---|---|
| 🟢 Safe | Below 35% | Monitor normally |
| 🟡 Uncertain | 35% to 60% | Send to expert |
| 🔴 Dangerous | Above 60% | Alert immediately |

---

## Results

| Metric | Score |
|---|---|
| Accuracy | 84.8% |
| AUC-ROC | 0.917 |
| Dangerous Recall | 85.7% |
| Avg Precision | 0.890 |

> Dangerous Recall is the most important metric — missing a dangerous lake means a real flood goes unwarned.

---

## How It Was Built

**Data:** 309 glacial lakes across 7 world regions collected from the Global GLOF Database using Google Earth Engine and Sentinel-2 satellite imagery at 25m resolution.

**Model:** EfficientNet-B0 with two-phase transfer learning.
- Phase 1 — frozen backbone, train head only (10 epochs)
- Phase 2 — unfreeze last 10 layers, fine-tune (15 epochs)

**Training:** Trained locally on NVIDIA Jetson Nano

**Deployment:** Live on Hugging Face · Edge inference on NVIDIA Jetson Nano

---

## Project Structure

```
GLOF_Project/
├── 1_Data_Collection/          Google Earth Engine script
├── 2_Training/                 Model training code (Jetson Nano)
├── 3_Deployment_HuggingFace/   Live web app
├── 4_Deployment_Jetson/        Edge device deployment
├── 5_Results/                  Charts and evaluation metrics
└── 6_Poster/                   Awareness poster
```

---

## Run It

**Web App**
```
1. Open the live app link above
2. Upload a satellite lake image
3. Click Analyze Risk Level
```

**Jetson Nano — Webcam Detection**
```bash
python3 GLOF_Webcam_Final.py
```

**Jetson Nano — File Prediction**
```bash
python3 GLOF_Capture_Predict.py
```

---

## References

- Lützow et al. (2023). A global database of historic glacier lake outburst floods. *Earth System Science Data*. https://doi.org/10.5194/essd-15-2983-2023
- Taylor et al. (2023). Glacial lake outburst floods threaten millions globally. *Nature Communications*. https://doi.org/10.1038/s41467-023-36033-x

---

*Trained on NVIDIA Jetson Nano · Model weights available on request · Built with PyTorch, Google Earth Engine, Gradio*
