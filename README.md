## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

```
 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df

```
<img width="327" height="437" alt="image" src="https://github.com/user-attachments/assets/1bdbe8f5-acaa-404b-8bd2-88bb2c8fd729" />

```

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

```

<img width="194" height="212" alt="image" src="https://github.com/user-attachments/assets/179adec0-ce5e-4961-9a1e-8dd2958c027c" />

```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
<img width="392" height="427" alt="image" src="https://github.com/user-attachments/assets/79091582-bf72-4526-93f3-514c6a2ff249" />

```
 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc

```
<img width="381" height="427" alt="image" src="https://github.com/user-attachments/assets/20165b41-dabc-4e53-a2fb-85f525e83583" />

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2
```

<img width="511" height="437" alt="image" src="https://github.com/user-attachments/assets/01b26fee-7017-4acd-85fd-96365cd323ff" />

```
pd.get_dummies(df2,columns=["nom_0"])
```
<img width="803" height="454" alt="image" src="https://github.com/user-attachments/assets/0185f25a-babe-4702-b41b-2f8d66f77636" />

```
pip install category_encoders
```
<img width="1530" height="324" alt="image" src="https://github.com/user-attachments/assets/2976a171-acf7-432e-8fca-6251ed203c5c" />

```
from category_encoders import BinaryEncoder
 df=pd.read_csv("data.csv")
 df
```

<img width="583" height="438" alt="image" src="https://github.com/user-attachments/assets/5bbb006a-8e3e-4884-858c-cc8e143ed6e0" />

```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
```

<img width="580" height="441" alt="image" src="https://github.com/user-attachments/assets/4a9cd7e8-51fb-497b-a7c6-b0857a6aa0b1" />

```
dfb=pd.concat([df,nd],axis=1)
dfb
```
<img width="839" height="437" alt="image" src="https://github.com/user-attachments/assets/6b840d05-d0d0-494d-adf2-430e62a9b2e8" />

```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
<img width="662" height="435" alt="image" src="https://github.com/user-attachments/assets/deee9b58-b818-4f8d-bc33-22f9e21d067c" />

```
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df
```
<img width="964" height="493" alt="image" src="https://github.com/user-attachments/assets/940029a5-2d2e-484b-b4b9-b7ecd26609ab" />

```
df.skew()
```
<img width="353" height="251" alt="image" src="https://github.com/user-attachments/assets/dd36c296-13b3-4cfc-bae1-07006bda09bc" />

```
np.log(df["Highly Positive Skew"])
```
<img width="330" height="559" alt="image" src="https://github.com/user-attachments/assets/20b04778-8983-4e17-ab69-43ffaf5f2a56" />

```
 np.reciprocal(df["Moderate Positive Skew"])
```
<img width="322" height="551" alt="image" src="https://github.com/user-attachments/assets/3e5a31fb-c850-4de4-a457-5db109728d57" />

```
 np.sqrt(df["Highly Positive Skew"])
```
<img width="307" height="552" alt="image" src="https://github.com/user-attachments/assets/bcd91e57-71eb-4629-aa09-32215c511e85" />

```
np.square(df["Highly Positive Skew"])
```
<img width="329" height="551" alt="image" src="https://github.com/user-attachments/assets/70dc72c9-59f4-415a-b1a5-3168c583ebb8" />

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
<img width="1229" height="517" alt="image" src="https://github.com/user-attachments/assets/5164882a-5234-4de5-a8cc-4de74d88bfc1" />

```
df.skew()
```
<img width="393" height="291" alt="image" src="https://github.com/user-attachments/assets/0f9dfb39-a82b-4563-a2c8-fc7aa40408b5" />

```
 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
 df.skew()
```
<img width="418" height="327" alt="image" src="https://github.com/user-attachments/assets/3becab78-a526-460a-a168-465d68603b15" />
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```

<img width="1675" height="534" alt="image" src="https://github.com/user-attachments/assets/32eec058-aef4-4800-9ab5-e8c9a6002464" />

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="723" height="534" alt="image" src="https://github.com/user-attachments/assets/33f5a862-242d-483f-a9af-179025cda841" />

```
 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()
```
<img width="706" height="527" alt="image" src="https://github.com/user-attachments/assets/849079ee-7c65-488c-8208-fff443fbca93" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="703" height="530" alt="image" src="https://github.com/user-attachments/assets/3db60d3c-83a9-4b74-9424-aeb6dcbdbdb3" />

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```
<img width="701" height="531" alt="image" src="https://github.com/user-attachments/assets/d79968b0-74d7-4027-b212-d011ef1b69c6" />

```
dt=pd.read_csv("titanic_dataset.csv")
dt
```

<img width="1429" height="505" alt="image" src="https://github.com/user-attachments/assets/ab2e3cd7-fc20-419c-93d6-bc5f33de30d6" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45') 
plt.show()
```
<img width="698" height="535" alt="image" src="https://github.com/user-attachments/assets/0414318c-7cda-4be6-8d58-7d5b15c5a307" />

```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```
<img width="697" height="531" alt="image" src="https://github.com/user-attachments/assets/1c35f35c-bac1-4350-a75b-d2ca92507784" />

# RESULT:

Thus the given data, Feature Encoding, Transformation process and save the data to a file
was performed successfully.

       
