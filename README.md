# Driver Analytics — Eye-Gaze & Visual Attention Analysis

## Project Overview

This research project explores computer-vision and eye-gaze analytics for driver monitoring, with a focus on transforming raw eye-tracking outputs into a structured format suitable for visual-attention and gaze-pattern analysis.

The project uses the VETA (Visual Eye-Tracking Analytics) framework as a reference for processing and analysing gaze data.

## Objective

The objective of this stage of the project is to develop a preprocessing pipeline that converts raw pupil-detection data into a clean, time-ordered representation for downstream eye-gaze analytics.

The workflow focuses on:

- Identifying valid pupil detections
- Ordering observations temporally
- Extracting pupil coordinates
- Computing inter-frame time differences
- Transforming the data into a VETA-compatible format

## Data

The raw eye-tracking data contains frame-level observations including:

- Image timestamps
- Camera information
- Image dimensions
- Face bounding-box coordinates
- Pupil detection information
- Pupil centre coordinates
- Additional eye-tracking and landmark attributes

The dataset is processed locally and is **not included in this repository**.

## Methodology

The preprocessing workflow implemented in `Veta_translation.ipynb` follows these steps:

1. Load the raw eye-tracking CSV data using Pandas.
2. Filter observations where the right pupil is successfully detected.
3. Sort observations using `image_timestamp`.
4. Generate a sequential observation index `t`.
5. Extract the right pupil centre coordinates as `x` and `y`.
6. Calculate the time difference between consecutive observations.
7. Convert timestamp differences from nanoseconds to seconds.
8. Retain the variables required for downstream VETA analysis.
9. Export the transformed data into a VETA-ready CSV structure.

### Output Structure

| Variable | Description |
|---|---|
| `t` | Sequential observation index |
| `x` | Right pupil centre X-coordinate |
| `y` | Right pupil centre Y-coordinate |
| `dt` | Time difference from the previous observation in seconds |

The current preprocessing run produced **567 valid observations** after filtering for right-pupil detection.

## Project Workflow

```text
Raw Eye-Tracking Data
        │
        ▼
Filter Valid Pupil Detections
        │
        ▼
Temporal Sorting
        │
        ▼
Extract Pupil Coordinates
        │
        ▼
Calculate Time Differences
        │
        ▼
VETA-Compatible Data
        │
        ▼
Downstream Gaze & Visual-Attention Analysis
````

## Technologies

- Python
- Pandas
- Google Colab
- CSV-based eye-tracking data
- VETA visual attention analytics framework

## Repository Contents

```text
research-driver-analytics/
│
├── README.md
│
└── Veta_translation.ipynb
````

The notebook contains the implemented preprocessing and data-transformation workflow.

## Research References

### VETA

The project draws on the VETA framework for visual eye-tracking analytics. VETA supports the exploration of gaze patterns and behaviours across time and space.

**Reference:**
Goodwin et al., *VETA: Visual eye-tracking analytics for the exploration of gaze patterns and behaviours*, Visual Informatics, 2022.

### HigherHRNet

HigherHRNet was investigated as a computer-vision reference for human pose estimation and scale-aware representation learning. It is an external research implementation and is **not included as original project code in this repository**.

## Current Scope

The current repository focuses on the **eye-tracking data preprocessing and VETA translation stage** of the research project.

The processed data provides a structured foundation for subsequent analysis of gaze behaviour and visual attention in driver-monitoring applications.

## Outcome

The project establishes a reproducible preprocessing workflow for converting raw pupil-detection outputs into a temporally ordered gaze representation suitable for downstream visual-attention analysis.
