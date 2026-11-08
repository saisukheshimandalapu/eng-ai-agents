# Assignment 3: Anti-UAV Visual Tracking System

**Student:** Sai Sukheshi Mandalapu (sm14567)
**Date of submission:** November 8, 2026

## Contents
- `dut-anti-uav.ipynb`: detector fine-tuning, Kalman tracker, evaluation and answers to questions 1-6 (all cell outputs saved)
- `video12_kalman.mp4`: output video for video12 (green = ground truth, red = Kalman estimate and trajectory)

## Results
| | Detector alone | Detector + Kalman filter |
|---|---|---|
| Test mAP@0.5 (input 640 / 1280) | 0.885 / 0.901 (3-epoch baseline: 0.689 / 0.749) | n/a |
| Success AUC, 20 sequences | 0.629 | 0.645 |
| Precision@20px, 20 sequences | 0.838 | 0.859 |
| Absent-box rate, 20 sequences | 0.99 | 0.84 |
| video13 AUC | 0.066 | 0.071 |

## How to run the notebook
1. Open `dut-anti-uav.ipynb` in Google Colab.
2. Select Runtime → Change runtime type → T4 GPU.
3. Run all cells top to bottom (Runtime → Run all). The first cell installs `ultralytics`, `filterpy` and `datasets`; the data downloads from the Hugging Face dataset `aegean-ai/dut-anti-uav`.
4. Expected run time on a T4: about 1-1.5 hours (training about 23 min, detection on 24,804 tracking frames about 15-25 min). The tracker and evaluation run in seconds on the cached detections.

## Tests
No separate tests. The notebook's provided scoring code evaluates the detector (mAP@0.5) and the tracker (success AUC, precision@20px, absent-box rate, and the video13 / absent-box check, which reports "both conditions met").
