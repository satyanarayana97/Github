
# BMI Table(Question 1) #
import json
data =({'Gender': 'Male', 'HeightCm': 171, 'WeightKg': 96},
 {'Gender': 'Male', 'HeightCm': 161, 'WeightKg': 85},
 {'Gender': 'Male', 'HeightCm': 180, 'WeightKg': 77},
 {'Gender': 'Female', 'HeightCm': 166, 'WeightKg': 62},
 {'Gender': 'Female', 'HeightCm': 150, 'WeightKg': 70},
 {'Gender': 'Female', 'HeightCm': 167, 'WeightKg': 82})
data
import pandas as pd
BMI=pd.DataFrame(columns=["Gender","HeightCm","WeightKg"])
for i in range(0,len(data)):
    currentitem= data[i]
BMI.loc[i]=[data[i]["Gender"],data[i]["HeightCm"],data[i]["WeightKg"]]
for ind,row in BMI.iterrows():
    BMI.loc[ind,"BMI"]=(row['WeightKg'])/((row['HeightCm']/100)**2)
BMI['BMI Category'] =["Underweight" if i<=18.4 else "Normal weight" if i>=18.5 and i<=24.9 else "Overweight" if i>=25 and i<=29.9 else "Moderately obese" if i>=30 and i<=34.9 else "Severely obese" if i>=35 and i<=39.9 else "Very severely obese" for i in BMI.BMI]
BMI['Health Risk'] =["Malnutrition risk" if i<=18.4 else "Low risk" if i>=18.5 and i<=24.9 else "Enhanced risk" if i>=25 and i<=29.9 else "Medium risk" if i>=30 and i<=34.9 else "High risk" if i>=35 and i<=39.9 else "Very high risk" for i in BMI.BMI]
BMI


# Total Overweight(Question 2) #

Totaloverweight =list(BMI['BMI Category']).count('Overweight')
Totaloverweight 

# Frequency Table for BMI Category (Additional) #

BMI['BMI Category'].value_counts()
