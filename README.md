# Final_Project-DATA-607

## Overview

This repository contains the complete work for the **DATA 607 Final Project**.

**Project Title:**  
**Beyond Magnitude: Analyzing Earthquake Risk Through Seismic Activity and Population Exposure**

The goal of this project is to analyze earthquake risk by combining seismic activity data with population exposure data. The main idea is that earthquake risk should not be understood only through earthquake frequency or magnitude. A moderate earthquake in or near a highly populated country may represent a different exposure concern than a stronger earthquake in a remote area.

This project uses earthquake event data from the **USGS Earthquake Catalog API/GeoJSON source** and combines it with **World Bank Population, total (`SP.POP.TOTL`) CSV data**. The analysis creates country-level earthquake summaries, joins them with population data, and develops exposure-related metrics such as earthquakes per million people and a custom earthquake exposure score.

---

## Repository Structure

```text
Final_Project-DATA-607/
│
├── data/
│   └── raw/
│       ├── API_SP.POP.TOTL_DS2_en_csv_v2_127039.csv
│       ├── Metadata_Country_API_SP.POP.TOTL_DS2_en_csv_v2_127039.csv
│       ├── Metadata_Indicator_API_SP.POP.TOTL_DS2_en_csv_v2_127039.csv
│       └── .gitkeep
│
├── Final_Project_Codebase.qmd          # Main final project report, code, analysis, and conclusions
├── Final_Project_LLM_Transcript.pdf    # LLM usage transcript
├── Final_Project_Video_Explainer.mp4   # Recorded final presentation / video explainer
├── README.md                           # Project documentation
├── .gitignore
└── LICENSE
````

---

## Technologies Used

* **R**
* **Quarto (.qmd)**
* **tidyverse**
* **jsonlite**
* **lubridate**
* **scales**
* **sf**
* **rnaturalearth**
* **leaflet**
* **broom**
* **knitr**
* **htmltools**
* **ggplot2**

---

## Data Sources

This project uses two different data source types:

### 1. USGS Earthquake Catalog API / GeoJSON

The earthquake event data was acquired from the **USGS Earthquake Catalog API**.

The dataset includes information such as:

* Earthquake magnitude
* Event time
* Latitude and longitude
* Depth
* Place description
* Tsunami flag
* Event significance

The final analysis uses earthquake events for the selected study period with magnitude **4.5 or greater**.

### 2. World Bank Population CSV

The population data comes from the **World Bank Population, total** indicator:

```text
SP.POP.TOTL
```

The raw World Bank CSV files are stored in this repository under:

```text
data/raw/
```

The main population file is loaded in the codebase through a raw GitHub URL to support reproducibility.

---

## Project Workflow

The project follows a reproducible data science workflow:

1. Acquire earthquake data from the USGS API
2. Load World Bank population data from GitHub/raw CSV
3. Clean and transform earthquake event records
4. Convert event timestamps into date fields
5. Extract longitude, latitude, and depth from GeoJSON coordinates
6. Create magnitude and depth categories
7. Convert earthquake coordinates into spatial point data
8. Use country boundaries to assign earthquakes to countries
9. Reshape World Bank population data from wide to long format
10. Select the latest available population year
11. Join country-level earthquake summaries with population data
12. Create exposure metrics
13. Conduct exploratory and statistical analysis
14. Build visualizations that describe the data and support conclusions
15. Add static and interactive geospatial maps
16. Interpret findings, limitations, and reproducibility considerations

---

## Key Transformations

Important transformations in this project include:

* Converting USGS earthquake timestamps into readable date fields
* Classifying earthquakes into magnitude categories
* Classifying earthquake depth into shallow, intermediate, and deep categories
* Extracting spatial coordinates from GeoJSON data
* Performing a spatial join between earthquake points and country boundaries
* Reshaping World Bank population data from wide to long format
* Selecting the latest available population values
* Joining earthquake summaries with population data by country code
* Creating exposure-related metrics

---

## Exposure Metrics

The project creates several metrics to compare earthquake activity and population exposure:

* **Earthquake count**
* **Average magnitude**
* **Maximum magnitude**
* **Weighted seismic activity**
* **Earthquakes per million people**
* **Weighted activity per million people**
* **Custom exposure score scaled from 0 to 100**

The custom exposure score combines weighted seismic activity with a population exposure factor. This allows the analysis to compare countries using more than just raw earthquake counts or magnitude alone.

---

## Statistical Analysis

The project includes statistical analysis to support the conclusions, including:

* Correlation analysis between population, earthquake activity, and exposure metrics
* Regression modeling of the custom exposure index
* Ranking comparison between earthquake count and exposure score

The analysis shows that earthquake risk interpretation can change depending on the metric used. Countries with the highest earthquake counts are not always the same as countries with the highest population-adjusted or exposure-weighted risk.

---

## Visualizations

The final report includes several visualizations, including:

* Magnitude distribution histogram
* Earthquake count by magnitude category
* Magnitude vs. depth scatterplot
* Top countries by earthquake event count
* Top countries by custom exposure score
* Population vs. weighted seismic activity scatterplot
* Earthquakes per million people by country
* Static global earthquake map
* Interactive `leaflet` earthquake map

The static map ensures that the geographic analysis displays reliably in the published report, while the interactive `leaflet` map allows users to explore event-level earthquake information.

---

## Feature Beyond Class

This project includes features beyond the standard course workflow:

* **Static and interactive geospatial mapping**
* **Spatial joins using country boundary data**
* **Custom earthquake exposure scoring system**

The `leaflet` map allows interactive exploration of earthquake locations, while the exposure score provides a custom ranking system that compares countries using both seismic activity and population exposure.

---

## Key Findings

The final report identifies the countries with:

* The highest earthquake count
* The highest custom exposure score
* The highest earthquakes-per-million rate among countries with at least 1 million people

The main conclusion is that earthquake risk should not be evaluated only by magnitude or event count. Population exposure adds important context and can change how earthquake risk is interpreted.

---

## Challenges

Two major challenges were addressed in this project:

1. **Assigning earthquakes to countries**
   The USGS `place` field is not always a clean country name, and many earthquakes occur offshore. To address this, earthquake latitude and longitude values were converted into spatial points and joined with country boundary data.

2. **Cleaning World Bank population data**
   The World Bank CSV includes metadata rows and stores years as separate columns. The codebase skips the metadata rows and reshapes the population data from wide to long format before selecting the latest available year.

---

## Reproducibility

This project is designed to be reproducible.

The codebase does **not** depend on local machine paths such as OneDrive, Desktop, or Downloads. The World Bank CSV files are stored in the GitHub repository and loaded using raw GitHub URLs. The USGS earthquake data is acquired through a public API/GeoJSON query.

To reproduce the project:

1. Clone or download this repository.
2. Open `Final_Project_Codebase.qmd`.
3. Install the required R packages if needed.
4. Render the Quarto file.
5. The report will reproduce the data acquisition, cleaning, analysis, visualizations, and conclusions.

---

## Links

* **GitHub Repository:**
  [https://github.com/suffyankhan77/Final_Project-DATA-607](https://github.com/suffyankhan77/Final_Project-DATA-607)

* **RPubs Published Report:**
  [https://rpubs.com/suffyankhan77/1431120](https://rpubs.com/suffyankhan77/1431120)

* **Codebase:**
  [https://github.com/suffyankhan77/Final_Project-DATA-607/blob/main/Final_Project_Codebase.qmd](https://github.com/suffyankhan77/Final_Project-DATA-607/blob/main/Final_Project_Codebase.qmd)

---

## Video Presentation

A recorded final project presentation will be included here:

```text
Final_Project_Video_Explainer.mp4
```

---

## LLM Usage

ChatGPT was used to support selected technical parts of the project, including:

* Cleaning and transforming USGS earthquake and World Bank population data
* Reshaping population data from wide to long format
* Designing earthquake exposure metrics
* Creating a custom exposure score
* Adding static and interactive geospatial mapping
* Troubleshooting RPubs/HTML map display issues
* Refining the final codebase structure and interpretation

The full LLM transcript is included in:

```text
Final_Project_LLM_Transcript.pdf
```

---

## References

* USGS Earthquake Catalog API
  [https://earthquake.usgs.gov/fdsnws/event/1/](https://earthquake.usgs.gov/fdsnws/event/1/)

* World Bank Population, total indicator (`SP.POP.TOTL`)
  [https://data.worldbank.org/indicator/SP.POP.TOTL](https://data.worldbank.org/indicator/SP.POP.TOTL)

* Natural Earth country boundary data through the `rnaturalearth` R package

* R Documentation:

  * tidyverse
  * jsonlite
  * lubridate
  * sf
  * rnaturalearth
  * leaflet
  * broom
  * scales
  * knitr

* OpenAI ChatGPT  
  OpenAI. (2026). ChatGPT (GPT-5.5 Thinking) [Large language model]. https://chat.openai.com.
