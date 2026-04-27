## Overview
This repository implements the **Relative Centroid Index (RCI)** methodology
for analyzing runoff and precipitation distributions along river main stems.
It provides workflows at the whole-basin scale and at Pfafstetter-derived
subbasin scales, exposed through both single-basin and batch CLIs.

# Repository Structure
```
├── code/
│   ├── single_basin_workflows.py   # Single-basin CLI entry
│   ├── batch_basin_workflows.py    # Batch CLI entry
│   └── core/                       # Core RCI library
├── data/                           # Packaged basin folders (download: https://doi.org/10.5281/zenodo.19364593)
├── examples/                       # Smoke-test cases (see examples/README.md)
├── scripts/                        # Figure-specific analysis (see scripts/README.md)
├── environment.yml
└── requirements.txt
```

## Requirements
- Python (see `environment.yml` for pinned versions)
- Recommended setup:
  ```bash
  mamba env create -f environment.yml
  mamba activate rci
  ```

## Workflow Descriptions
### 1. Pfaf (`python code/single_basin_workflows.py`)
Generates reach-level Pfafstetter codes for a packaged basin.

### 2. Runoff RCI (`python code/single_basin_workflows.py`)
Computes basin-scale runoff RCI from `grades_discharge.csv`.

### 3. Precipitation RCI (`python code/single_basin_workflows.py`)
Computes basin-scale precipitation RCI from upstream MSWEP totals (or a
gridded field if totals are missing).

### 4. Multilevel Runoff RCI (`python code/single_basin_workflows.py --source continuous`)
Computes runoff RCI at each Pfaf level.

### 5. Multilevel Precipitation RCI (`python code/single_basin_workflows.py --source gridded`)
Computes precipitation RCI at each Pfaf level.

# Quick Start
### Single Basin (default: Poyang)
```bash
python code/single_basin_workflows.py pfaf
python code/single_basin_workflows.py runoff
python code/single_basin_workflows.py precipitation
python code/single_basin_workflows.py multilevel --source continuous
python code/single_basin_workflows.py multilevel --source gridded
```


## Citation
Yin, Z., Lin, P., Yamazaki, D., Lin, H., & Zhang, F. (2026). Relative Centroid
Index (RCI): A Novel Scale-Independent Metric for Assessing Hydrological
Distributions across Hierarchical River Networks. Manuscript revised for
publication in Water Resources Research.

Contact: Ziyun Yin (yinziyun0208@stu.pku.edu.cn)
