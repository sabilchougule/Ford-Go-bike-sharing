# 🚲 Ford GoBike Sharing System — Exploratory Data Analysis (EDA)

## 📌 Project Overview
The **Ford GoBike Sharing System** is a public bike-sharing service providing an affordable, convenient, and eco-friendly mode of urban transportation. This project analyzes the complete **2018 Ford GoBike trip dataset** (comprising 12 monthly CSV archives consolidated into over **1.86 million trip records**).

Through structured data cleaning, feature engineering, and Exploratory Data Analysis (EDA), this repository uncovers customer riding behaviors, peak demand periods, station usage, and demographic trends to drive actionable business recommendations.

---

## 🎯 Business Problem & Objectives
To optimize fleet allocation, improve customer satisfaction, and maximize revenue, this analysis addresses key operational questions:
* **User Segmentation:** How do riding habits differ between recurring **Subscribers** and casual **Customers**?
* **Temporal Patterns:** What are the peak hours, days of the week, and times of day for bike rentals?
* **Trip Characteristics:** What is the typical ride duration, and how does it vary across user types?
* **Demographics:** How do rider age and gender influence system usage?
* **Infrastructure Demand:** Which stations experience the highest trip volume and require additional bike/dock capacity?

---

## 📂 Repository Structure
```text
Ford-Go-bike-sharing/
│
├── analysis.ipynb                                               # Main EDA notebook with data cleaning & visualizations
├── Data-Exploration-with-Bike-Data(Sample solution).ipynb       # Reference EDA notebook
├── Data-Finding-Slide-Deck-with-Bike-Data (Sample solution).ipynb # Notebook for explanatory presentation visuals
├── Sample_EDA_Submission_Template.ipynb                         # Structured EDA template
├── Ford Bike Sharing Data.pptx                                  # Executive presentation slide deck
├── 201801-fordgobike-tripdata.csv.zip                           # Monthly trip data (Jan - Dec 2018)
├── ...
├── 201812-fordgobike-tripdata.csv.zip
└── README.md                                                    # Project documentation
```

---

## 🛠️ Tech Stack & Libraries
* **Language:** Python 3
* **Environment:** Jupyter Notebook
* **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `glob`, `zipfile`, `warnings`, `datetime`

---

## 🧹 Data Wrangling & Feature Engineering
1. **Data Consolidation:** Merged all 12 monthly trip files from 2018 into a master dataset of **1,863,721 rows and 16 columns**.
2. **Data Cleaning:**
   * Dropped `11,771` records missing start/end station IDs and names (retaining `1,851,950` valid trips).
   * Converted `start_time` and `end_time` strings to `datetime` objects.
   * Verified zero duplicate rows and zero negative/zero-second trip durations.
   * Filtered out `31` records with unrealistic birth years (`< 1900`), leaving **1,851,919 clean records**.
   * Imputed missing `member_gender` entries (`~5.9%`) as `"Unknown"` to preserve trip volume data.
3. **Feature Engineering:**
   * `ride_duration_min`: Converted trip duration from seconds to minutes.
   * `ride_year`, `ride_month`, `month_name`, `ride_day`, `day_name`, `ride_hour`: Extracted granular temporal features.
   * `time_of_day`: Categorized hours into *Morning* (5–11), *Afternoon* (12–16), *Evening* (17–20), and *Night* (21–4).
   * `age` & `age_group`: Computed rider age as of 2018 and segmented users into brackets (`Below 18`, `18-25`, `26-35`, `36-45`, `46-55`, `56+`).

---

## 📊 Key Findings & Business Insights

### 1. User Type Dominance
* **Subscribers** account for **85%** (`1,574,965` rides) of all trips, while casual **Customers** make up **15%** (`276,954` rides).
* **Insight:** The service relies heavily on recurring commuters. Introducing promotional trials or discounted first-month passes can help convert high-frequency casual Customers into Subscribers.

### 2. Commute-Driven Peak Hours
* Usage peaks in the **Morning** (`676,447` rides) and **Evening** (`557,575` rides), dropping sharply at **Night** (`120,269` rides).
* **Insight:** Fleet rebalancing should prioritize high-traffic commuter hubs prior to morning and evening rush hours, while scheduling bike maintenance during overnight lulls.

### 3. Ride Duration Patterns
* Overall ride durations are right-skewed, with most trips lasting between **5 and 15 minutes**.
* **Customers** take significantly longer trips (higher median duration) than **Subscribers**.
* **Insight:** Subscribers use the service for quick, point-to-point daily commutes, whereas Customers use bikes for leisure and sightseeing.

### 4. Rider Demographics
* **Age:** The **26–35** age group is the largest user segment (`789,490` rides), followed by **36–45** (`389,122` rides) and **18–25** (`284,441` rides).
* **Gender:** Male riders represent the majority (`1,279,525` rides), followed by Female riders (`435,361` rides) and Unknown/Other (`137,033` rides).
* **Insight:** Targeted marketing campaigns and safety/accessibility initiatives can help expand adoption among female riders and university students (`18–25`).

---

## 💡 Business Recommendations
1. **Peak-Hour Fleet Optimization:** Increase bike availability during Morning and Evening rush hours to satisfy commuter demand.
2. **Dynamic Redistribution:** Monitor top start and end stations to proactively rebalance bikes and prevent dock shortages.
3. **Off-Peak Promotions:** Offer discounted rides or promotional campaigns during afternoons, weekends, and winter months to boost off-peak utilization.
4. **Customer-to-Subscriber Conversion:** Launch targeted free trials and referral incentives aimed at frequent casual riders.

---

## 🚀 How to Run Locally
1. **Clone the repository:**
   ```bash
   git clone https://github.com/<your-username>/Ford-Go-bike-sharing.git
   cd Ford-Go-bike-sharing
   ```
2. **Extract the monthly datasets:**
   Unzip all `2018XX-fordgobike-tripdata.csv.zip` files into the project directory.
3. **Install dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
4. **Update the folder path & run:**
   Open `analysis.ipynb` in Jupyter Notebook, update `folder_path` in Step 2 to point to your local directory (`folder_path = "."`), and run all cells.