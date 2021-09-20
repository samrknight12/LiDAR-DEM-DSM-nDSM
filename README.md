# LiDAR-DEM-DSM-nDSM
Digital Elevation Model, Digital Surface Model, and normalized Digital Surface Model generated from a LiDAR point cloud.

## Data
### Source
The point cloud used for this project was aquired from LidarBC - Open Lidar Data Portal. This can be found at: https://governmentofbc.maps.arcgis.com/apps/MapSeries/index.html?appid=d06b37979b0c4709b7fcf2a1ed458e03
The represented area is Southern Lower Gibsons BC Canada.

### Spatial Reference
![img](/img1/ele1.PNG) ![img](/img1/ele2.PNG) ![img](/img1/ele3.PNG)

### Data Specifics
Number of data points: 49,012,056
Units: Meters
Classification Codes:
1: Unassigned , Point Count: 42,879,481 , %: 87.49
2: Ground , Point Count: 5,612,411 , %: 11.45
3: Low Noise , Point Count: 520,164 , %: 1.06

## Process
### Make LAS Dataset Layers
Using ArcGIS Pro's 'Make LAS Dataset' Geoprocessing tool, two layers were made:
1) Ground points LAS
Using the classification code 2 which corresponds to ground points from the original LAS dataset, and all return values this layer was generated.

2) First Returns LAS
Using all classification codes, and return value 'First Returns' this layer was generated

### Calculate Statistics
Using ArcGIS Pro's LiDAR statistics tool, the statistics for the original .lasd was calculated. This is very important, especially when we need to know the point spacing of the data set. 
These statistics can be found in the repo files.

### Generate Rasters
Using ArcGIS Pro's 'Export LAS to Raster' tool the DEM and DSM were created. The DEM's input LAS was the ground points LAS layer. the DSM's input was the first returns layer.

To create the normalized digital surface model, I utilized the raster functions 'Minus' tool. With this tool I subtracted the DEM from the DSM. The nDSM created contains the heights of objects relative to the surface elevation instead of the vertical reference of the data. 

## Results
### DEM
![img](/img1/ele4.PNG)

### DSM
![img](/img1/ele5.PNG)

### nDSM
![img](/img1/ele6.PNG)


### Note: A full pdf map of the 3 models is in the repo files.
