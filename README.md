# MIMIC-III PPG CAD/CVD Dataset

This repository contains the released patient-level photoplethysmography (PPG) datasets and notebooks used for CAD/CVD cohort construction and exploratory data analysis.

## Released Data

The final task-specific CSV files are stored in `data/`:

- `patient_level_CAD_vs_NonCAD_strict.csv` - strict CAD vs Non-CAD cohort, 3,465 subjects.
- `patient_level_CVD_vs_NonCVD.csv` - implemented CVD vs Non-CVD cohort, 5,456 subjects.

Each row represents one selected waveform record per `SUBJECT_ID` and includes six one-minute PPG windows from minutes 3-8, demographics, comorbidity flags, and binary task labels.

## Notebooks

- `Step_1_PPG_signal_Extraction_MIMIC_III.ipynb` - extracts PPG windows from MIMIC-III matched waveform records.
- `Step-2_Demographic_data_adding.ipynb` - adds demographics and diagnosis-event tables from MIMIC-III clinical data.
- `Step-3_CAD_CVD_labeling.ipynb` - applies ICD-9 prefix-based CAD/CVD labels and comorbidity flags.
- `Step_4_Dataset_Preparation.ipynb` - aggregates to patient-level task CSV files.
- `Step_5_Dataset_EDA_for_BSPC.ipynb` - reproduces manuscript statistics and EDA plots from the released final CSV files.

## Reproducibility Notes

The final CSV files can be used directly with Notebook 5 to reproduce dataset summaries and plots.

Full reproduction from raw MIMIC-III requires independent credentialed access to the MIMIC-III clinical database and MIMIC-III matched waveform database through PhysioNet. The raw MIMIC files are not included in this repository.

For raw reproduction, place the required MIMIC clinical tables under `data/mimic_clinical/` and the matched waveform `RECORDS` file under `work/mimic_waveforms/` before running Steps 1-4.

## Environment

Install dependencies with:

```bash
pip install -r requirements.txt
```

Large CSV files may require Git LFS or an external data-release service if this repository is pushed to GitHub.
