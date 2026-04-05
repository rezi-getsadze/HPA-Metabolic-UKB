# HPA-Metabolic-UKB

This repository contains the code and synthetic pilot data for: **"Mechanistic Modeling of Stress-Induced Glucose Dysregulation: Calibrating a Coupled HPA-Metabolic Framework to the UK Biobank"** (ICCS 2026). The project implements a coupled 18-variable ODE system linking psychosocial stress (HPA axis) to glucose-insulin metabolic dynamics. We use individualized scaling for glucose uptake and hepatic production to replicate clinical bimodal distributions without group-specific refitting.

### Main files

* **`main_simulation.ipynb`**: the primary calibrated model. includes the simulation loop for the pilot cohorts, generates the statistical validation plots (ecdf, q-q, and population density), and runs an independent HbA1c validation against Field 30750 (not used in initialization).
* **`uncalibrated_simulation.ipynb`**: the baseline comparison (uncalibrated).
* **`synthetic_data.ipynb`**: script to generate the synthetic pilot datasets (`t2d_pilot_healthy_full.csv` and `t2d_diabetics_full.csv`) used to verify the scaling logic.
* **`t2d_preprocess.ipynb`**: the data pipeline for raw uk biobank files. handles the mapping of mental health items, metabolic markers, and unit conversions. Generates data (N=100) for simulation, `t2d_pilot_50_healthy.csv` and `t2d_pilot_50_diabetics.csv` from the full csv files. Updated filtering uses IS NOT Yes criterion for healthy cohort (avoids excluding participants with missing follow-up instances) and checks both Instance 0 and Instance 1 medication fields.

### Data note

The included CSV files are randomized synthetic pilot cohorts ($N=100$) designed to mirror the raw UK Biobank structure. They represent metabolic extremes (50 healthy, 50 T2D) to test the model's attractor stability. Due to licensing restrictions, raw UKB data is not provided.

### Installation

1. clone the repo:
   ```bash
   git clone https://github.com/rezi-getsadze/HPA-Metabolic-UKB.git
   ```
2. to install the required Python packages, run:
   ```bash
   pip install -r requirements.txt
   ```
