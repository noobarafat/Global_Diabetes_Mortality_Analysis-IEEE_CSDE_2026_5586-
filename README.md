# Global Diabetes Mortality Analysis (2000-2014)

Reproducible analysis pipeline for the paper **"Global Diabetes Mortality 
Analysis: A Reproducible WHO Data-Driven Study of Trends, Regional 
Disparities, and Prevalence-Mortality Relationships (2000-2014)"**, 
accepted at IEEE CSDE 2026.

## Overview

This repository contains the complete, executed analysis notebook, source 
datasets, and output figures/tables used in the paper. It covers global 
diabetes mortality trends across 190 countries from 2000 to 2014, using 
harmonized WHO mortality and prevalence data merged through a documented, 
aggregate-row-exclusion pipeline.

## Contents

- `Global_Diabetes_Mortality_Analysis.ipynb` — full analysis notebook with 
  all outputs and figures embedded
- `deaths-from-diabetes-ghe.zip` — WHO Global Health Estimates 2021, 
  diabetes death counts
- `diabetes-prevalence-who-gho.zip` — WHO Global Health Observatory, 
  diabetes prevalence estimates
- `population-unwpp.csv` — UN World Population Prospects 2024, population 
  by country and year
- `paper_outputs/` — all figures (300 DPI) and tables as used in the paper

## Data sources

- WHO Global Health Estimates (GHE) 2021, accessed via Our World in Data, 
  https://ourworldindata.org/grapher/deaths-from-diabetes-ghe
- WHO Global Health Observatory (GHO), accessed via Our World in Data, 
  https://ourworldindata.org/grapher/diabetes-prevalence-who-gho
- UN World Population Prospects 2024, accessed via Our World in Data, 
  https://ourworldindata.org/grapher/population-unwpp

## Methodology summary

- Datasets merged via inner join on Entity, Code, and Year
- The "World" aggregate row (Code: OWID_WRL) explicitly excluded before any 
  statistical computation, since it duplicates the sum of all countries and 
  otherwise inflates descriptive statistics and biases correlation results
- Pearson and Spearman correlation, both on raw death counts and on 
  population-normalized mortality rates (deaths per 100,000)
- Two-way fixed-effects panel regression (country and year fixed effects, 
  country-clustered standard errors)
- Sensitivity checks: annual cross-sectional correlation, country-level 
  average correlation, exclusion of India and China, exclusion of countries 
  under 1 million population
- Bootstrap 95% confidence intervals for CAGR estimates (global, 
  high-income, LMIC)

## Reproducing the analysis

1. Open `Global_Diabetes_Mortality_Analysis.ipynb` in Google Colab
2. Run the first cell, which prompts a file upload
3. Upload the three data files listed above when prompted
4. Runtime → Run all

## Citation

If you use this code or data pipeline, please cite the paper (full citation 
to be added upon publication).
