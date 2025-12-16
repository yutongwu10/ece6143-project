# ece6143-project
# Jet Tagging with CNN, ResNet50 Fine-Tuning, Physics MLP, SVM, and Logistic Regression

This project performs **jet tagging** using deep learning and physics-inspired machine learning, focusing on distinguishing **signal** vs **background** jets from particle physics data.  
The work includes preprocessing, jet image construction, and training/evaluating multiple models.  
All results are based on running code inside Google Colab.

---

## Project Overview

High-energy physics experiments produce jets—collimated sprays of particles.  
Identifying whether a jet originates from a **top quark (signal)** or **QCD background** is a key task in jet tagging.

This project builds **five models**:

1. **CNN (from scratch)** — input: **33×33×1** jet images  
2. **ResNet50 (ImageNet fine-tuning)** — input: jet images **resized to 75×75 and replicated to 3 channels (75×75×3)**  
3. **Physics MLP** — input: **4 physics features** extracted from reconstructed jets *(non-image input)*  
4. **SVM (RBF Kernel)** — input: **flattened 33×33** jet images  
5. **Logistic Regression** — input: **4 physics features** extracted from reconstructed jets *(non-image input)*

All models are trained and evaluated on the same dataset and compared using **accuracy** and **ROC–AUC**.

---

## Dataset

The dataset `val.h5` is downloaded from Zenodo:  
https://zenodo.org/records/2603256/files/val.h5

We use:

- **Signal**: Top-quark jets (10,000 events)  
- **Background**: QCD jets (10,000 events)

Each event contains 200 particles with `(E, px, py, pz)`, and the leading fat jet is reconstructed using the **anti-kT** algorithm.

---

## Results (Latest)

| Model               | AUC    | Accuracy |
|--------------------|--------:|---------:|
| CNN                | 0.8544  | 74.75%   |
| ResNet50           | 0.9314  | 86.85%   |
| Physics MLP        | 0.9260  | 88.33%   |
| SVM (RBF Kernel)   | 0.9388  | 88.10%   |
| Logistic Regression| 0.9260  | 88.85%   |
