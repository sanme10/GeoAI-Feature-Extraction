# GeoAI: Automated Feature Extraction for GIS
### Multi-Sensor Semantic Segmentation & Object Detection

##  Project Overview
As a Geomatics Engineer, I developed this repository to demonstrate two distinct Deep Learning approaches for extracting spatial features from satellite and aerial imagery. This project bridges the gap between raw spectral data and GIS-ready vector geometry.

---

##  Section 1: Semantic Segmentation (U-Net)
**Goal:** Pixel-level classification for precise area calculation and land-use mapping.

### 1. Building Footprint Extraction (NAIP Imagery)
* **Sensor:** NAIP Aerial Imagery (0.6m Multi-spectral).
* **Metric:** **0.88 Validation IoU.**
* **Technical Detail:** Optimized to extract rigid geometric boundaries of rooftops. By utilizing a high inference threshold (0.88), the model successfully ignores complex urban shadows and spectral noise from roads.



### 2. Cotton Crop Identification (Sentinel-2)
* **Sensor:** Sentinel-2 Satellite (10m Multi-spectral).
* **Metric:** **0.93 Validation IoU.**
* **Technical Detail:** Leveraged Near-Infrared (NIR) and Red-Edge bands. Implemented a hybrid **BCE + Dice Loss** to handle class imbalance, ensuring accurate field boundaries for agricultural acreage calculation.



---

## 🛰️ Section 2: Object Detection (YOLOv8)
**Goal:** Rapid localization and counting of features across large-scale geographic areas.

### Building Detection & Counting
* **Model:** YOLOv8 (Ultralytics).
* **Data:** NAIP High-Resolution Imagery (R,G,B bands used)
* **Application:** Designed for rapid urban census, disaster impact assessment, and monitoring of informal settlements.
* **Advantage:** While U-Net provides exact shapes, this YOLO implementation allows for high-speed "point-based" detection and counting across massive tiles where processing time is a constraint.



---

##  Technical Methodology
* **Data Engineering:** Used **Rasterio** and **NumPy** to process multi-spectral Geotiff files into training-ready tensors.
* **Spectral Normalization:** Developed custom **Channel-wise Min-Max scaling** to stabilize training across 16-bit (Sentinel-2) and 8-bit (NAIP) datasets.
* **Loss Functions:** Implemented **Dice Loss+Binary Cross Entropy Loss** to solve "Zero Recall" issues, ensuring the model converges even when the target feature (buildings/crops) occupies a small percentage of the image tile.

---

##  Tech Stack
* **Frameworks:** TensorFlow, Keras, PyTorch (Ultralytics).
* **Geospatial:** Rasterio, GDAL, GeoPandas, NumPy.
* **Visualization:** Matplotlib, Folium, ArcGIS/QGIS for validation.

---

##  Repository Structure
* `building_segmentation_naip.ipynb` - U-Net workflow for urban features.
* `cotton_segmentation_sentinel2.ipynb` - U-Net workflow for multi-spectral crops.
* `building_detection_yolo.ipynb` - YOLOv8 implementation.
* `results/` - Folder containing performance plots and visual predictions.

---
**Contact:** [Sandeep Gautam] – [gtmsandeep2@gmail.com]
