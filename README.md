## Fly Smarter

by CrazyCats

Forecasting Flight Prices to Help You Save Big! 

Explore real-time intelligence in the Microsoft Fabric architecture to gain insights into flight prices.


---

### **1. Data Pipeline**

#### **a. Setting Up**
1. **Create a new pipeline**:  
   - Set up a new data pipeline in your environment.
2. **Create a new Dataflow Activity**:  
   - Add a new activity to the pipeline for data processing.
3. **Choose/Create a Dataflow**:  
   - Select an existing dataflow or create a new one that fits the data processing requirements.
4. **Create a new Notebook**:  
   - Set up a new notebook for processing, feature engineering, and model training.
5. **Link Dataflow and Notebook**:  
   - Connect the dataflow with the newly created notebook to allow seamless data flow and analysis.
6. **Set a Pipeline Schedule**:  
   - Schedule the pipeline to run at desired intervals for continuous data processing.

---

### **2. Dataflow Gen2**

#### **a. Source**
- **SerpApi**:  
- Add a step to retrieve flight price as JSON document from SerpApi web contents in real-time.

#### **b. Transform Data**
1. **Expand Columns**:  
   - Select the relevant columns from SerpApi data.
2. **Select Columns**:  
   - Choose the necessary columns for further data processing.
3. **Change Column Data Types**:  
   - Ensure the correct data types for each column to avoid errors during analysis.

#### **c. Store Data in KQL**
- **Store Transformed Data**:  
  - Store the transformed flight data in the **flights** table in KQL for querying and further analysis.

---

### **3. Notebook**

#### **a. Check KQL URI and Credentials**
1. **KQL URI**:  
   - Ensure you have the correct Azure Data Explorer (KQL) URI.
2. **Authentication**:  
   - Verify the necessary credentials (e.g., client ID, secret) to authenticate the connection.

#### **b. Connect to KQL Database**
- Use the proper connection string and credentials to establish a connection with the KQL database.

#### **c. Ingest Data from KQL**
- Retrieve flight data from the **flights** table using KQL queries.
- Load the retrieved data into a **Pandas DataFrame** for further analysis.

---

### **4. Exploratory Data Analysis (EDA) & Data Processing**

- **Initial Data Exploration**:  
  Start by inspecting the dataset, displaying the first few rows and checking the data types. Look for any missing values or anomalies that need to be addressed.

- **Data Summary Statistics**:  
  Utilize fabric notebook visualization to view statistics (e.g., mean, median, standard deviation) and understand the distributions and detect potential outliers.

- **Visualizations**:  
  Visualize the data to uncover trends and relationships:
  - **Correlation Heatmaps**: Identify correlations between features.
  - **Histogram**: Visualize the distribution of flight prices to understand how they vary across different ranges.
  - **Boxen Plot**: Visualize the distribution of flight prices across different arrival airports. This plot highlights the spread, outliers, and patterns in the price distribution for each airport, providing insights into how prices vary depending on the arrival airport.


---

### **5. Feature Engineering & Data Processing**

#### **a. Data Cleaning**
- Handle missing values by dropping rows based on the context of the data.

#### **b. Feature Scaling**
- Normalize numerical features to ensure consistency in scale across all features, which helps avoid bias during model training.

#### **c. Feature Encoding**
- Make use of the One-Hot Encoding method to encode important categorical features like airlines and airports, which allows training models on the encoded data.

---

### **6. Feature Selection & Model Training**

#### **a. Feature Selection**
- Using a heatmap is an effective way to visualize the correlation between different features in a dataset and is an effective way to determine the features for selection.

#### **b. Train Machine Learning Models**
- Train machine learning models such as **ExtraTreesRegressor** and **XGBoost** on the processed data and selected features.

#### **c. Model Evaluation**
- Evaluate the model's performance by comparing predicted values with actual values, using metrics like **Mean Squared Error (MSE)**, **Accuracy**, **R²**.

#### **d. Model Versioning**
- Save the trained models with versioning information, allowing to track and load the correct version for future updates.

---

### **7. KQL Databases**

#### **a. Flights Table**
- **flights**:  
  - Stores the raw flight data from SerpApi after transformation.

#### **b. FlightVisualization Table**
- **flightVisualization**:  
  - Stores the transformed data from the notebook for real-time dashboard visualizations.

#### **c. Process Table**
- **process**:  
  - Tracks the last processed date of the data to avoid redundant processing and ensure up-to-date information.

---

### **8. Real-Time Dashboard**

#### **a. Create Tiles**
- Set up tiles on the dashboard to display real-time visualizations and insights.

#### **b. Write KQL Queries**
- Write KQL queries to retrieve and filter data for visualizations, pulling data from the **flightVisualization** table.

#### **c. Customize Charts**
- Customize the visualizations by adjusting chart labels, types, colors, and other settings to enhance readability and clarity.

#### **d. Add Filter Parameters**
- Enable users to dynamically filter the data by adding filter parameters to the dashboard, providing flexibility in data exploration.

#### **e. Set Auto-Refresh**
- Configure auto-refresh to ensure that the dashboard updates with the latest data automatically, providing real-time insights.

---
