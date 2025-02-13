
# Clinical-data-processing
This repository contains scripts and datasets for processing and analyzing clinical study data. The scripts automate data cleaning, transformation, and summary generation.

### Dataset Description


This repository includes a structured dataset from a clinical trial covering patient demographics, clinical observations, and treatment outcomes. The processed dataset consists of 141 observations and 2663 variables. 

The data consists of multiple timepoints (visits) for each subject, denoted by prefixes such as V0 (baseline), D1, D2, etc., up to D7. Each timepoint captures various aspects of the patient's condition and treatment.

The dataset contains a comprehensive set of columns representing clinical trial data. Below is a structured description of the key column categories:

### **1. Patient Demographics and Consent**
- **V0.DW.DM.RFICYN.SIG**: Indicates if the patient provided informed consent.
- **V0.IE.IEPROTV**: Protocol version used in the study.
- **V0.DD.DM.SEX**: Patient's sex.
- **V0.DD.DM.AGE**: Patient's age.
- **V0.DD.SU.SUTRT_CIGARETTES.SUENRF**: Indicates smoking status.
- **V0.MH.MHYN**: Indicates if the patient has pre-existing medical conditions.

### **2. Clinical Observations**
- **V0.FA.FATEST_OBJAWY.FAORRES.int**: Date of symptom onset.
- **V0.PE.PEDAT.DATE**: Date of physical examination.
- **V0.PE.PEPERF**: Indicates if the examination was performed.
- **V0.PE.REASND**: Reason for not performing the examination.
- **V0.PE.PECLSIG.01–10**: Clinical significance of findings across various systems (e.g., cardiovascular, respiratory, neurological).

### **3. Vital Signs**
- **V0.VS.VSPERF**: Indicates if vital signs were measured.
- **V0.VS.VSDAT.DATE**: Date of vital sign measurements.
- **V0.VS.DIABP_VSORRES.txt**: Diastolic blood pressure result.
- **V0.VS.HR_VSORRES.int**: Heart rate measurement.
- **V0.VS.RESP_VSORRES.int**: Respiratory rate measurement.
- **V0.VS.TEMP_VSORRES.int**: Body temperature measurement.

### **4. Laboratory Tests**
#### Hematology
- **V0.BMK.LB.HEMAT_HGB.LBORRES**: Hemoglobin levels.
- **V0.BMK.LB.HEMAT_WBC.LBORRES**: White blood cell count.
#### Biochemistry
- **V0.LB.CHEMISTRY.AST.LBORRES**: Aspartate aminotransferase (AST) levels.
- **V0.LB.CHEMISTRY.ALT.LBORRES**: Alanine aminotransferase (ALT) levels.
#### Biomarkers
- **V0.LB.BIOMARKERS.CRP.LBORRES**: C-reactive protein (CRP) levels.

### **5. Imaging and Diagnostics**
- **V0.PR.X-RAY.PROCCUR**: Indicates if a chest X-ray was performed.
- **V0.EG.EGPERF**: Indicates if a 12-lead ECG was performed.

### **6. Respiratory Support**
- **V0.CM.OXYGEN_CMTRT.CMOCCUR**: Indicates if the patient received oxygen therapy.
- **V0.PR.INVAVENT_PRTRT.PROCCUR**: Indicates if invasive ventilation was used.

## Scripts Description

### 1. `creating_datasets.Rmd`
This script is the primary source for dataset generation. It processes raw clinical data and creates structured datasets used in subsequent analyses. The script includes data transformation steps, cleaning procedures, and variable mapping.

**Features:**
- Reads and preprocesses raw clinical data.
- Applies necessary transformations and data wrangling.
- Generates structured datasets for analysis.
- Ensures data consistency and integrity.

## Generates structured dataset 
## SDTM and ADaM Processing Overview

This script processes clinical trial data following the CDISC SDTM and ADaM standards, providing a streamlined way to handle patient demographics, adverse events, and vital signs. Key updates ensure logical mapping, additional statistics, and improved data visualization for better insights into the dataset.


1. **Enhanced Mapping for SDTM Domains**:
   - Mappings were reviewed for `VSORRES` to ensure logical handling of different measurement types (e.g., blood pressure, temperature, heart rate).
   - Explicitly linked `VSORRES` to measurement-specific variables from the dataset, avoiding misinterpretation of mixed data formats.

2. **ADVS Variable Enhancements**:
   - **New Variables**: Extracted systolic and diastolic blood pressure, numeric results, and identified the type of vital sign measurement (e.g., heart rate, temperature).
   - **Logical Categorization**: Utilized the `VSTESTCD` and `VSORRES` data to create separate fields for systolic blood pressure (`SYSTOLIC_BP`), diastolic blood pressure (`DIASTOLIC_BP`), and a unified numeric representation (`NUMERIC_VALUE`).

3. **Statistical Analysis**:
   - Added descriptive statistics to ADVS and ADSL datasets, including quartiles, skewness, kurtosis, and variance.
   - Validated and excluded invalid data formats to ensure robust numeric computations.
   - Included missing value checks and reporting for critical variables like `VSORRES`.

4. **Visualization Enhancements**:
   - Created gender distribution bar plots.
   - Generated box plots for age groups and vital sign measurements.
   - Visualization now reflects precise mappings of the SDTM fields and measurement types.

### File Outputs

- **Processed SDTM Datasets**:
  - `sdtm_dm.csv`: Subject demographics data.
  - `sdtm_ae.csv`: Adverse event data.
  - `sdtm_vs.csv`: Vital sign measurements.

- **Processed ADaM Datasets**:
  - `adam_adsl.csv`: Subject-level analysis dataset.
  - `adam_adae.csv`: Adverse event analysis dataset.
  - `adam_advs.csv`: Vital signs analysis dataset.

## Usage
1. Load the required R packages.
2. Use `creating_datasets.Rmd` to generate cleaned and structured datasets.
3. Utilize `tabela_wynikowa_tylko_ogol` for summary generation.
4. Customize decimal separators and rounding as needed.
5. Analyze and interpret summary statistics for the clinical study.

## Dependencies
- R version 4.0+
- `psych` package

