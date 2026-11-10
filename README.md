# AquaTrace-SIH26-ML

This repository contains the machine learning engine for AquaTrace, developed for the Smart India Hackathon (SIH) 2026. It provides the end-to-end pipeline that powers the platform's predictive capabilities by correlating historical fish landing data with marine biogeochemistry and weather telemetry. The model forecasts coastal environmental risks and utilizes Explainable AI (SHAP) to translate complex data into transparent, actionable insights.

The complete full-stack application is in this repository : [https://github.com/samridha24/AquaTrace](https://github.com/samridha24/AquaTrace)

## Features
* **End-to-End ML Pipeline:** Fully contained in a single Jupyter Notebook (`SIH_26_ML.ipynb`).
* **Multi-Source Data Integration:** Combines local offline datasets (Copernicus Marine, CMFRI) with dynamically fetched API data (Open-Meteo, Google Earth Engine).
* **Explainable AI (XAI):** Utilizes SHAP (SHapley Additive exPlanations) to explain feature importance and model predictions, ensuring transparency.
* **Plug-and-Play Architecture:** Directory structures are pre-configured or dynamically generated, requiring zero manual file management to run.

## Repository Structure

```text
AquaTrace-SIH26-ML/
├── README.md                                         
├── requirements.txt                                  # Python dependencies
├── SIH_26_ML.ipynb                                   # Main Machine Learning Notebook
└── content/
    └── data/
        ├── marine/
        │   └── bbp_cdm.nc                            # Copernicus BBP & CDM telemetry data
        └── processed/
            └── Districtwise_and_specieswise_Maharashtra.csv  # CMFRI Fish Landings baseline
```

## Datasets

This project utilizes both offline and online (fetched at runtime) datasets:

**Included in this repository:**
1. **Marine Optics Data (`bbp_cdm.nc`):** Particulate Backscattering (BBP) and Colored Dissolved Organic Matter (CDM) telemetry downloaded from the Copernicus Marine Service.
2. **Fish Landings Data (`Districtwise_and_specieswise_Maharashtra.csv`):** Historical district-wise fish landing records from CMFRI for the state of Maharashtra.

**Fetched dynamically during runtime:**
* **Weather Data:** Automatically downloaded via the Open-Meteo API.
* **Satellite Imagery (Sentinel):** Automatically processed and fetched via Google Earth Engine (GEE).
*(Note: The notebook will automatically create the `weather/` and `sentinel/` folders inside `content/data/` to store this data when you run it).*

## Installation & Setup

To run this project locally, you will need Python installed on your system.

**1. Clone the repository:**
```bash
git https://github.com/rp-009/AquaTrace-SIH26-ML/
cd AquaTrace-SIH26-ML
```

**2. Create a virtual environment:**
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

**3. Install dependencies:**
```bash
pip install -r requirements.txt
```

**4. Run the Jupyter Notebook:**
```bash
jupyter notebook
```
Open `SIH_26_ML.ipynb` in your browser and click **"Run All"** to execute the pipeline from start to finish.

## Explainable AI (SHAP)
Because this model is intended for real-world stakeholder use, transparency is critical. The final cells of the notebook implement SHAP values to break down exactly which environmental factors (e.g., CDM levels, specific weather conditions) are driving the model's predictions for fish landings. 
