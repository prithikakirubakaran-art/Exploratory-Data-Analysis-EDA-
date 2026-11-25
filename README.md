# Exp No.2 : Exploratory Data Analysis (EDA)

## Aim
To perform Exploratory Data Analysis (EDA) on the heart disease dataset to understand the data distribution, relationships, and key patterns useful for business insights and model building.

## Dataset
The dataset used for this experiment is `heartdisease.csv`. It contains medical and demographic information such as age, sex, cholesterol levels (`totChol`), `BMI`, blood pressure, and target values (`TenYearCHD`) indicating heart disease presence.

## Algorithm
1. Import required Python libraries (`numpy`, `pandas`, `seaborn`, `matplotlib`).
2. Load the dataset into a Pandas DataFrame.
3. Display the dataset structure, shape, and descriptive statistics.
4. Check for missing values and duplicate rows.
5. Examine correlations among numeric features using a correlation matrix and heatmap.
6. Visualize univariate distributions using histograms, boxplots, and countplots.
7. Analyze bivariate and multivariate relationships using scatter plots and pairplots.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Basic Exploration** | `df.info()` | Inspect dataset structure and data types |
| | `df.describe()` | Generate descriptive statistics |
| | `df.isnull().sum()` | Detect missing values in each column |
| | `df.duplicated().sum()` | Identify duplicate rows |
| | `df.corr()` | Find correlations between numeric variables |
| **Univariate Analysis** | `sns.histplot()` | Plot histogram (distribution of single variable) |
| | `sns.boxplot()` | Identify outliers using boxplot |
| | `sns.countplot()` | Count occurrences of categorical variables |
| **Bivariate Analysis** | `sns.scatterplot()` | Display relationship between two variables |
| | `sns.heatmap()` | Show correlation matrix visually |
| **Multivariate Analysis** | `sns.pairplot()` | Show pairwise relationships across variables |
| **Visualization Controls** | `plt.figure()`, `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display plotted charts |

## Program & Output
    import numpy as np
    import pandas as pd
    import seaborn as sns
    import matplotlib.pyplot as plt
    
    # Load dataset
    df = pd.read_csv("heartdisease.csv")
    
    # Basic exploration
    print("Dataset Information:")
    df.info()
    
    print("\nDataset Shape:")
    print(df.shape)
    
    print("\nDescriptive Statistics:")
    print(df.describe())
    
    # Check missing values and duplicates
    print("\nMissing Values:")
    print(df.isnull().sum())
    
    print("\nDuplicate Rows:")
    print(df.duplicated().sum())
    
    # Correlation matrix
    corr = df.corr(numeric_only=True)
    
    print("\nCorrelation Matrix:")
    print(corr)
    
    # Correlation heatmap
    plt.figure(figsize=(10, 6))
    sns.heatmap(corr, annot=True, cmap="coolwarm")
    plt.title("Correlation Heatmap")
    plt.show()
    
    # Histogram for Age
    plt.figure(figsize=(6, 4))
    sns.histplot(df["Age"], kde=True)
    plt.title("Age Distribution")
    plt.xlabel("Age")
    plt.show()
    
    # Boxplot for Cholesterol
    plt.figure(figsize=(6, 4))
    sns.boxplot(y=df["Totalcholestrol"])
    plt.title("Cholesterol Distribution")
    plt.show()
    
    # Countplot for Heart Disease
    plt.figure(figsize=(6, 4))
    sns.countplot(x="TenYearCHD", data=df)
    plt.title("Heart Disease Count")
    plt.show()
    
    # Scatter plot for Age vs Cholesterol
    plt.figure(figsize=(6, 4))
    sns.scatterplot(x="Age", y="Totalcholestrol",
                    hue="TenYearCHD", data=df)
    plt.title("Age vs Cholesterol")
    plt.show()
    
    # Pairplot for selected features
    sns.pairplot(
        df[["Age", "Totalcholestrol", "BMI", "TenYearCHD"]],
        hue="TenYearCHD"
    )
    plt.show()
    
    print("\nEDA Completed Successfully!")



##  OUTPUT

        Dataset Information:
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 250 entries, 0 to 249
    Data columns (total 17 columns):
     #   Column           Non-Null Count  Dtype  
    ---  ------           --------------  -----  
     0   S. No            250 non-null    int64  
     1   Gender           250 non-null    object 
     2   Age              250 non-null    int64  
     3   Education        250 non-null    int64  
     4   currentsmoker    250 non-null    int64  
     5   Cigsperday       250 non-null    int64  
     6   BPMeds           250 non-null    int64  
     7   Prevalentstroke  250 non-null    int64  
     8   PrevalentHyp     250 non-null    int64  
     9   Diabetes         250 non-null    int64  
     10  Totalcholestrol  250 non-null    int64  
     11  SysBP            250 non-null    float64
     12  DiaBP            250 non-null    float64
     13  BMI              250 non-null    float64
     14  Heartrate        250 non-null    int64  
     15  Glucose          250 non-null    int64  
     16  TenYearCHD       250 non-null    int64  
    dtypes: float64(3), int64(13), object(1)
    memory usage: 33.3+ KB
    
    Dataset Shape:
    (250, 17)
    
    Descriptive Statistics:
                S. No         Age  Education  currentsmoker  Cigsperday  \
    count  250.000000  250.000000  250.00000     250.000000  250.000000   
    mean   125.500000   50.088000    2.48000       0.456000    6.688000   
    std     72.312977   12.268755    1.08735       0.499059    9.368336   
    min      1.000000   30.000000    1.00000       0.000000    0.000000   
    25%     63.250000   38.250000    2.00000       0.000000    0.000000   
    50%    125.500000   51.500000    2.00000       0.000000    0.000000   
    75%    187.750000   61.000000    3.00000       1.000000   12.000000   
    max    250.000000   70.000000    4.00000       1.000000   30.000000   
    
               BPMeds  Prevalentstroke  PrevalentHyp    Diabetes  Totalcholestrol  \
    count  250.000000       250.000000    250.000000  250.000000       250.000000   
    mean     0.108000         0.024000      0.256000    0.080000       235.192000   
    std      0.311003         0.153356      0.437297    0.271837        37.276498   
    min      0.000000         0.000000      0.000000    0.000000       120.000000   
    25%      0.000000         0.000000      0.000000    0.000000       207.250000   
    50%      0.000000         0.000000      0.000000    0.000000       237.500000   
    75%      0.000000         0.000000      1.000000    0.000000       260.750000   
    max      1.000000         1.000000      1.000000    1.000000       320.000000   
    
               SysBP       DiaBP         BMI   Heartrate     Glucose  TenYearCHD  
    count  250.00000  250.000000  250.000000  250.000000  250.000000  250.000000  
    mean   129.42760   83.491200   26.288400   84.220000   88.012000    0.184000  
    std     18.92353   11.649065    4.588731   16.377438   24.685407    0.388261  
    min     85.00000   55.600000   16.000000   55.000000   45.000000    0.000000  
    25%    118.02500   74.425000   23.200000   71.000000   72.000000    0.000000  
    50%    129.10000   84.050000   25.950000   86.000000   89.000000    0.000000  
    75%    141.75000   91.475000   29.375000   99.000000  103.000000    0.000000  
    max    180.90000  114.100000   41.700000  110.000000  163.000000    1.000000  
    
    Missing Values:
    S. No              0
    Gender             0
    Age                0
    Education          0
    currentsmoker      0
    Cigsperday         0
    BPMeds             0
    Prevalentstroke    0
    PrevalentHyp       0
    Diabetes           0
    Totalcholestrol    0
    SysBP              0
    DiaBP              0
    BMI                0
    Heartrate          0
    Glucose            0
    TenYearCHD         0
    dtype: int64
    
    Duplicate Rows:
    0
    
    Correlation Matrix:
                        S. No       Age  Education  currentsmoker  Cigsperday  \
    S. No            1.000000  0.023186   0.020635       0.064990    0.150244   
    Age              0.023186  1.000000   0.038365       0.019656    0.000624   
    Education        0.020635  0.038365   1.000000      -0.005329   -0.042405   
    currentsmoker    0.064990  0.019656  -0.005329       1.000000    0.781306   
    Cigsperday       0.150244  0.000624  -0.042405       0.781306    1.000000   
    BPMeds           0.024733  0.109068  -0.035153       0.043677    0.063991   
    Prevalentstroke -0.134356 -0.001127  -0.093446       0.066328    0.125433   
    PrevalentHyp     0.094362  0.141004   0.061487      -0.169007   -0.191191   
    Diabetes         0.061291  0.017148  -0.008152      -0.033156   -0.054816   
    Totalcholestrol -0.075021  0.045776  -0.028441      -0.090646   -0.069116   
    SysBP           -0.012314 -0.064074   0.115269      -0.106715   -0.091499   
    DiaBP            0.013581 -0.005452  -0.003121      -0.069217   -0.080823   
    BMI              0.037638  0.027889   0.108976       0.025117   -0.044656   
    Heartrate       -0.048050  0.017012   0.049524       0.078579    0.076698   
    Glucose         -0.130046 -0.036722   0.010408       0.066383    0.067743   
    TenYearCHD      -0.008439  0.034526  -0.086376      -0.082408   -0.096773   
    
                       BPMeds  Prevalentstroke  PrevalentHyp  Diabetes  \
    S. No            0.024733        -0.134356      0.094362  0.061291   
    Age              0.109068        -0.001127      0.141004  0.017148   
    Education       -0.035153        -0.093446      0.061487 -0.008152   
    currentsmoker    0.043677         0.066328     -0.169007 -0.033156   
    Cigsperday       0.063991         0.125433     -0.191191 -0.054816   
    BPMeds           1.000000         0.029640      0.032128 -0.102608   
    Prevalentstroke  0.029640         1.000000     -0.032099 -0.046241   
    PrevalentHyp     0.032128        -0.032099      1.000000 -0.037838   
    Diabetes        -0.102608        -0.046241     -0.037838  1.000000   
    Totalcholestrol -0.079740        -0.069657     -0.150850 -0.016979   
    SysBP           -0.013815        -0.051156      0.016226 -0.069446   
    DiaBP           -0.006388         0.016530     -0.047489 -0.014869   
    BMI              0.063636        -0.020148     -0.062559 -0.020502   
    Heartrate       -0.013357         0.018677     -0.012382  0.010464   
    Glucose         -0.044111        -0.030841     -0.097759  0.035167   
    TenYearCHD       0.034323         0.127883      0.052606  0.126330   
    
                     Totalcholestrol     SysBP     DiaBP       BMI  Heartrate  \
    S. No                  -0.075021 -0.012314  0.013581  0.037638  -0.048050   
    Age                     0.045776 -0.064074 -0.005452  0.027889   0.017012   
    Education              -0.028441  0.115269 -0.003121  0.108976   0.049524   
    currentsmoker          -0.090646 -0.106715 -0.069217  0.025117   0.078579   
    Cigsperday             -0.069116 -0.091499 -0.080823 -0.044656   0.076698   
    BPMeds                 -0.079740 -0.013815 -0.006388  0.063636  -0.013357   
    Prevalentstroke        -0.069657 -0.051156  0.016530 -0.020148   0.018677   
    PrevalentHyp           -0.150850  0.016226 -0.047489 -0.062559  -0.012382   
    Diabetes               -0.016979 -0.069446 -0.014869 -0.020502   0.010464   
    Totalcholestrol         1.000000 -0.117847  0.003185  0.067296   0.021363   
    SysBP                  -0.117847  1.000000 -0.000752 -0.004210  -0.076207   
    DiaBP                   0.003185 -0.000752  1.000000  0.049928   0.008641   
    BMI                     0.067296 -0.004210  0.049928  1.000000  -0.016863   
    Heartrate               0.021363 -0.076207  0.008641 -0.016863   1.000000   
    Glucose                 0.053086  0.112820 -0.036708  0.053558   0.054133   
    TenYearCHD             -0.078204  0.114203  0.028685  0.026675  -0.044918   
    
                      Glucose  TenYearCHD  
    S. No           -0.130046   -0.008439  
    Age             -0.036722    0.034526  
    Education        0.010408   -0.086376  
    currentsmoker    0.066383   -0.082408  
    Cigsperday       0.067743   -0.096773  
    BPMeds          -0.044111    0.034323  
    Prevalentstroke -0.030841    0.127883  
    PrevalentHyp    -0.097759    0.052606  
    Diabetes         0.035167    0.126330  
    Totalcholestrol  0.053086   -0.078204  
    SysBP            0.112820    0.114203  
    DiaBP           -0.036708    0.028685  
    BMI              0.053558    0.026675  
    Heartrate        0.054133   -0.044918  
    Glucose          1.000000   -0.015735  
    TenYearCHD      -0.015735    1.000000  
    
    
    
  <img width="851" height="622" alt="image" src="https://github.com/user-attachments/assets/c73f75ba-e13f-4e1e-9d61-ecc488b4ad80" />
 <img width="531" height="393" alt="image" src="https://github.com/user-attachments/assets/215ff488-0661-4049-9d8d-e42d27225f84" />
<img width="531" height="393" alt="image" src="https://github.com/user-attachments/assets/a14c2b14-0aa6-4fb7-9083-c0efbb388a67" />
<img width="540" height="393" alt="image" src="https://github.com/user-attachments/assets/e1439596-e0cd-49c7-ae89-ae4a4508ee31" />
<img width="540" height="393" alt="image" src="https://github.com/user-attachments/assets/d8667253-3a80-4c00-9ae6-f27a06ceff90" />
<img width="842" height="741" alt="image" src="https://github.com/user-attachments/assets/cad5f034-d185-4263-b5c2-f46455871edc" />

  
    
    
    EDA Completed Successfully!

## Result
Thus, Exploratory Data Analysis (EDA) was successfully performed on the heart disease dataset using Python libraries. The dataset was examined using descriptive statistics, missing-value analysis, and correlation analysis. Histograms, boxplots, countplots, scatter plots, heatmaps, and pairplots were generated to understand data distributions, relationships, and patterns useful for further model building.
