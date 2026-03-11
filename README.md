# Thin Report Splitter for Power BI

## Overview

This project contains a Python script designed to **separate a Power BI report from its original semantic model (dataset)** and rebind it to a different dataset.

The goal is to convert a regular report into a **thin report**, which improves governance, reuse of semantic models, and simplifies dataset management.

The script uses the **semantic-link-labs** library to automate the process inside Microsoft Fabric / Power BI environments.

---

# What the Script Does

The workflow consists of three main steps:

### 1. Copy the Semantic Model

The script first **deploys a copy of the original dataset** to a different workspace.

This allows organizations to centralize datasets while allowing reports to remain in their original workspace.

---

### 2. Rebind the Report

Once the dataset is deployed, the report is **rebound to the new dataset**.

This converts the report into a **thin report** because it no longer contains its own data model.

---

### 3. Optional Dataset Cleanup

The script can optionally **remove the original dataset** after the report has been successfully rebound.

This prevents duplicate models and helps enforce centralized data governance.

---

# Script Configuration

The following variables must be configured before running the script:

| Variable                        | Description                                                 |
| ------------------------------- | ----------------------------------------------------------- |
| `start_workspace`               | Workspace where the original report and dataset are located |
| `report`                        | Name of the report                                          |
| `dataset_name`                  | Name of the original dataset                                |
| `destination_dataset_workspace` | Workspace where the new dataset will be deployed            |
| `destination_dataset_name`      | Name of the new dataset                                     |
| `remove_original_dataset`       | If `True`, deletes the original dataset                     |
| `overwrite`                     | If `True`, allows overwriting existing datasets             |

Example configuration:

```
start_workspace = "Workspace A"
report = "Sales Report"
dataset_name = "Sales Dataset"

destination_dataset_workspace = "Central Models"
destination_dataset_name = "Sales Dataset"

remove_original_dataset = True
overwrite = True
```

---

# Requirements

Before running the script, install the required library:

```
pip install semantic-link-labs
```

---

# How to Run

1. Open the notebook or Python script
2. Configure workspace and dataset variables
3. Run the script

The script will automatically:

* copy the semantic model
* rebind the report
* optionally delete the original dataset

---

# Use Cases

This tool is useful for:

* migrating reports to **centralized semantic models**
* converting reports to **thin reports**
* enforcing **Power BI governance best practices**
* automating dataset management across workspaces

---

# Example Architecture

Before running the script:

```
Workspace A
 ├── Report
 └── Dataset
```

After running the script:

```
Workspace A
 └── Thin Report

Central Models Workspace
 └── Dataset
```

---

# Why Thin Reports?

Thin reports are considered a **best practice in Power BI architecture** because they:

* reduce duplicate datasets
* improve performance
* simplify maintenance
* allow centralized data models

---

# Radule

Created as a utility script to simplify Power BI report and dataset management.
