```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
```


```python
df = pd.read_csv('world-data-2023.csv')
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country</th>
      <th>Density\n(P/Km2)</th>
      <th>Abbreviation</th>
      <th>Agricultural Land( %)</th>
      <th>Land Area(Km2)</th>
      <th>Armed Forces size</th>
      <th>Birth Rate</th>
      <th>Calling Code</th>
      <th>Capital/Major City</th>
      <th>Co2-Emissions</th>
      <th>...</th>
      <th>Out of pocket health expenditure</th>
      <th>Physicians per thousand</th>
      <th>Population</th>
      <th>Population: Labor force participation (%)</th>
      <th>Tax revenue (%)</th>
      <th>Total tax rate</th>
      <th>Unemployment rate</th>
      <th>Urban_population</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>60</td>
      <td>AF</td>
      <td>58.10%</td>
      <td>652,230</td>
      <td>323,000</td>
      <td>32.49</td>
      <td>93.0</td>
      <td>Kabul</td>
      <td>8,672</td>
      <td>...</td>
      <td>78.40%</td>
      <td>0.28</td>
      <td>38,041,754</td>
      <td>48.90%</td>
      <td>9.30%</td>
      <td>71.40%</td>
      <td>11.12%</td>
      <td>9,797,273</td>
      <td>33.939110</td>
      <td>67.709953</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>105</td>
      <td>AL</td>
      <td>43.10%</td>
      <td>28,748</td>
      <td>9,000</td>
      <td>11.78</td>
      <td>355.0</td>
      <td>Tirana</td>
      <td>4,536</td>
      <td>...</td>
      <td>56.90%</td>
      <td>1.20</td>
      <td>2,854,191</td>
      <td>55.70%</td>
      <td>18.60%</td>
      <td>36.60%</td>
      <td>12.33%</td>
      <td>1,747,593</td>
      <td>41.153332</td>
      <td>20.168331</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>18</td>
      <td>DZ</td>
      <td>17.40%</td>
      <td>2,381,741</td>
      <td>317,000</td>
      <td>24.28</td>
      <td>213.0</td>
      <td>Algiers</td>
      <td>150,006</td>
      <td>...</td>
      <td>28.10%</td>
      <td>1.72</td>
      <td>43,053,054</td>
      <td>41.20%</td>
      <td>37.20%</td>
      <td>66.10%</td>
      <td>11.70%</td>
      <td>31,510,100</td>
      <td>28.033886</td>
      <td>1.659626</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>164</td>
      <td>AD</td>
      <td>40.00%</td>
      <td>468</td>
      <td>NaN</td>
      <td>7.20</td>
      <td>376.0</td>
      <td>Andorra la Vella</td>
      <td>469</td>
      <td>...</td>
      <td>36.40%</td>
      <td>3.33</td>
      <td>77,142</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>67,873</td>
      <td>42.506285</td>
      <td>1.521801</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>26</td>
      <td>AO</td>
      <td>47.50%</td>
      <td>1,246,700</td>
      <td>117,000</td>
      <td>40.73</td>
      <td>244.0</td>
      <td>Luanda</td>
      <td>34,693</td>
      <td>...</td>
      <td>33.40%</td>
      <td>0.21</td>
      <td>31,825,295</td>
      <td>77.50%</td>
      <td>9.20%</td>
      <td>49.10%</td>
      <td>6.89%</td>
      <td>21,061,025</td>
      <td>-11.202692</td>
      <td>17.873887</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 35 columns</p>
</div>




```python
df.shape
```




    (195, 35)




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 195 entries, 0 to 194
    Data columns (total 35 columns):
     #   Column                                     Non-Null Count  Dtype  
    ---  ------                                     --------------  -----  
     0   Country                                    195 non-null    object 
     1   Density
    (P/Km2)                            195 non-null    object 
     2   Abbreviation                               188 non-null    object 
     3   Agricultural Land( %)                      188 non-null    object 
     4   Land Area(Km2)                             194 non-null    object 
     5   Armed Forces size                          171 non-null    object 
     6   Birth Rate                                 189 non-null    float64
     7   Calling Code                               194 non-null    float64
     8   Capital/Major City                         192 non-null    object 
     9   Co2-Emissions                              188 non-null    object 
     10  CPI                                        178 non-null    object 
     11  CPI Change (%)                             179 non-null    object 
     12  Currency-Code                              180 non-null    object 
     13  Fertility Rate                             188 non-null    float64
     14  Forested Area (%)                          188 non-null    object 
     15  Gasoline Price                             175 non-null    object 
     16  GDP                                        193 non-null    object 
     17  Gross primary education enrollment (%)     188 non-null    object 
     18  Gross tertiary education enrollment (%)    183 non-null    object 
     19  Infant mortality                           189 non-null    float64
     20  Largest city                               189 non-null    object 
     21  Life expectancy                            187 non-null    float64
     22  Maternal mortality ratio                   181 non-null    float64
     23  Minimum wage                               150 non-null    object 
     24  Official language                          190 non-null    object 
     25  Out of pocket health expenditure           188 non-null    object 
     26  Physicians per thousand                    188 non-null    float64
     27  Population                                 194 non-null    object 
     28  Population: Labor force participation (%)  176 non-null    object 
     29  Tax revenue (%)                            169 non-null    object 
     30  Total tax rate                             183 non-null    object 
     31  Unemployment rate                          176 non-null    object 
     32  Urban_population                           190 non-null    object 
     33  Latitude                                   194 non-null    float64
     34  Longitude                                  194 non-null    float64
    dtypes: float64(9), object(26)
    memory usage: 53.4+ KB
    


```python
df.drop('Abbreviation', axis=1, inplace=True)
```


```python
df.isnull().sum()
```




    Country                                       0
    Density\n(P/Km2)                              0
    Agricultural Land( %)                         7
    Land Area(Km2)                                1
    Armed Forces size                            24
    Birth Rate                                    6
    Calling Code                                  1
    Capital/Major City                            3
    Co2-Emissions                                 7
    CPI                                          17
    CPI Change (%)                               16
    Currency-Code                                15
    Fertility Rate                                7
    Forested Area (%)                             7
    Gasoline Price                               20
    GDP                                           2
    Gross primary education enrollment (%)        7
    Gross tertiary education enrollment (%)      12
    Infant mortality                              6
    Largest city                                  6
    Life expectancy                               8
    Maternal mortality ratio                     14
    Minimum wage                                 45
    Official language                             5
    Out of pocket health expenditure              7
    Physicians per thousand                       7
    Population                                    1
    Population: Labor force participation (%)    19
    Tax revenue (%)                              26
    Total tax rate                               12
    Unemployment rate                            19
    Urban_population                              5
    Latitude                                      1
    Longitude                                     1
    dtype: int64




```python
df[df.isnull().any(axis=1)].head(20)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country</th>
      <th>Density\n(P/Km2)</th>
      <th>Agricultural Land( %)</th>
      <th>Land Area(Km2)</th>
      <th>Armed Forces size</th>
      <th>Birth Rate</th>
      <th>Calling Code</th>
      <th>Capital/Major City</th>
      <th>Co2-Emissions</th>
      <th>CPI</th>
      <th>...</th>
      <th>Out of pocket health expenditure</th>
      <th>Physicians per thousand</th>
      <th>Population</th>
      <th>Population: Labor force participation (%)</th>
      <th>Tax revenue (%)</th>
      <th>Total tax rate</th>
      <th>Unemployment rate</th>
      <th>Urban_population</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>164</td>
      <td>40.00%</td>
      <td>468</td>
      <td>NaN</td>
      <td>7.20</td>
      <td>376.0</td>
      <td>Andorra la Vella</td>
      <td>469</td>
      <td>NaN</td>
      <td>...</td>
      <td>36.40%</td>
      <td>3.33</td>
      <td>77,142</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>67,873</td>
      <td>42.506285</td>
      <td>1.521801</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Antigua and Barbuda</td>
      <td>223</td>
      <td>20.50%</td>
      <td>443</td>
      <td>0</td>
      <td>15.33</td>
      <td>1.0</td>
      <td>St. John's, Saint John</td>
      <td>557</td>
      <td>113.81</td>
      <td>...</td>
      <td>24.30%</td>
      <td>2.76</td>
      <td>97,118</td>
      <td>NaN</td>
      <td>16.50%</td>
      <td>43.00%</td>
      <td>NaN</td>
      <td>23,800</td>
      <td>17.060816</td>
      <td>-61.796428</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Australia</td>
      <td>3</td>
      <td>48.20%</td>
      <td>7,741,220</td>
      <td>58,000</td>
      <td>12.60</td>
      <td>61.0</td>
      <td>Canberra</td>
      <td>375,908</td>
      <td>119.8</td>
      <td>...</td>
      <td>19.60%</td>
      <td>3.68</td>
      <td>25,766,605</td>
      <td>65.50%</td>
      <td>23.00%</td>
      <td>47.40%</td>
      <td>5.27%</td>
      <td>21,844,756</td>
      <td>-25.274398</td>
      <td>133.775136</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Austria</td>
      <td>109</td>
      <td>32.40%</td>
      <td>83,871</td>
      <td>21,000</td>
      <td>9.70</td>
      <td>43.0</td>
      <td>Vienna</td>
      <td>61,448</td>
      <td>118.06</td>
      <td>...</td>
      <td>17.90%</td>
      <td>5.17</td>
      <td>8,877,067</td>
      <td>60.70%</td>
      <td>25.40%</td>
      <td>51.40%</td>
      <td>4.67%</td>
      <td>5,194,416</td>
      <td>47.516231</td>
      <td>14.550072</td>
    </tr>
    <tr>
      <th>11</th>
      <td>The Bahamas</td>
      <td>39</td>
      <td>1.40%</td>
      <td>13,880</td>
      <td>1,000</td>
      <td>13.97</td>
      <td>1.0</td>
      <td>Nassau, Bahamas</td>
      <td>1,786</td>
      <td>116.22</td>
      <td>...</td>
      <td>27.80%</td>
      <td>1.94</td>
      <td>389,482</td>
      <td>74.60%</td>
      <td>14.80%</td>
      <td>33.80%</td>
      <td>10.36%</td>
      <td>323,784</td>
      <td>25.034280</td>
      <td>-77.396280</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Bahrain</td>
      <td>2,239</td>
      <td>11.10%</td>
      <td>765</td>
      <td>19,000</td>
      <td>13.99</td>
      <td>973.0</td>
      <td>Manama</td>
      <td>31,694</td>
      <td>117.59</td>
      <td>...</td>
      <td>25.10%</td>
      <td>0.93</td>
      <td>1,501,635</td>
      <td>73.40%</td>
      <td>4.20%</td>
      <td>13.80%</td>
      <td>0.71%</td>
      <td>1,467,109</td>
      <td>26.066700</td>
      <td>50.557700</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Belarus</td>
      <td>47</td>
      <td>42.00%</td>
      <td>207,600</td>
      <td>155,000</td>
      <td>9.90</td>
      <td>375.0</td>
      <td>Minsk</td>
      <td>58,280</td>
      <td>NaN</td>
      <td>...</td>
      <td>34.50%</td>
      <td>5.19</td>
      <td>9,466,856</td>
      <td>64.10%</td>
      <td>14.70%</td>
      <td>53.30%</td>
      <td>4.59%</td>
      <td>7,482,982</td>
      <td>53.709807</td>
      <td>27.953389</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Bhutan</td>
      <td>20</td>
      <td>13.60%</td>
      <td>38,394</td>
      <td>6,000</td>
      <td>17.26</td>
      <td>975.0</td>
      <td>Thimphu</td>
      <td>1,261</td>
      <td>167.18</td>
      <td>...</td>
      <td>19.80%</td>
      <td>0.42</td>
      <td>727,145</td>
      <td>66.70%</td>
      <td>16.00%</td>
      <td>35.30%</td>
      <td>2.34%</td>
      <td>317,538</td>
      <td>27.514162</td>
      <td>90.433601</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Bolivia</td>
      <td>11</td>
      <td>34.80%</td>
      <td>1,098,581</td>
      <td>71,000</td>
      <td>21.75</td>
      <td>591.0</td>
      <td>Sucre</td>
      <td>21,606</td>
      <td>148.32</td>
      <td>...</td>
      <td>25.90%</td>
      <td>1.59</td>
      <td>11,513,100</td>
      <td>71.80%</td>
      <td>17.00%</td>
      <td>83.70%</td>
      <td>3.50%</td>
      <td>8,033,035</td>
      <td>-16.290154</td>
      <td>-63.588653</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Bosnia and Herzegovina</td>
      <td>64</td>
      <td>43.10%</td>
      <td>51,197</td>
      <td>11,000</td>
      <td>8.11</td>
      <td>387.0</td>
      <td>Sarajevo</td>
      <td>21,848</td>
      <td>104.9</td>
      <td>...</td>
      <td>28.60%</td>
      <td>2.16</td>
      <td>3,301,000</td>
      <td>46.40%</td>
      <td>20.40%</td>
      <td>23.70%</td>
      <td>18.42%</td>
      <td>1,605,144</td>
      <td>43.915886</td>
      <td>17.679076</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Brunei</td>
      <td>83</td>
      <td>2.70%</td>
      <td>5,765</td>
      <td>8,000</td>
      <td>14.90</td>
      <td>673.0</td>
      <td>Bandar Seri Begawan</td>
      <td>7,664</td>
      <td>99.03</td>
      <td>...</td>
      <td>6.00%</td>
      <td>1.61</td>
      <td>433,285</td>
      <td>64.70%</td>
      <td>NaN</td>
      <td>8.00%</td>
      <td>9.12%</td>
      <td>337,711</td>
      <td>4.535277</td>
      <td>114.727669</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Burundi</td>
      <td>463</td>
      <td>79.20%</td>
      <td>27,830</td>
      <td>31,000</td>
      <td>39.01</td>
      <td>257.0</td>
      <td>Bujumbura</td>
      <td>495</td>
      <td>182.11</td>
      <td>...</td>
      <td>19.10%</td>
      <td>0.10</td>
      <td>11,530,580</td>
      <td>79.20%</td>
      <td>13.60%</td>
      <td>41.20%</td>
      <td>1.43%</td>
      <td>1,541,177</td>
      <td>-3.373056</td>
      <td>29.918886</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Cambodia</td>
      <td>95</td>
      <td>30.90%</td>
      <td>181,035</td>
      <td>191,000</td>
      <td>22.46</td>
      <td>855.0</td>
      <td>Phnom Penh</td>
      <td>9,919</td>
      <td>127.63</td>
      <td>...</td>
      <td>59.40%</td>
      <td>0.17</td>
      <td>16,486,542</td>
      <td>82.30%</td>
      <td>17.10%</td>
      <td>23.10%</td>
      <td>0.68%</td>
      <td>3,924,621</td>
      <td>12.565679</td>
      <td>104.990963</td>
    </tr>
    <tr>
      <th>33</th>
      <td>Central African Republic</td>
      <td>8</td>
      <td>8.20%</td>
      <td>622,984</td>
      <td>8,000</td>
      <td>35.35</td>
      <td>236.0</td>
      <td>Bangui</td>
      <td>297</td>
      <td>186.86</td>
      <td>...</td>
      <td>39.60%</td>
      <td>0.06</td>
      <td>4,745,185</td>
      <td>72.00%</td>
      <td>8.60%</td>
      <td>73.30%</td>
      <td>3.68%</td>
      <td>1,982,064</td>
      <td>6.611111</td>
      <td>20.939444</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Chad</td>
      <td>13</td>
      <td>39.70%</td>
      <td>1,284,000</td>
      <td>35,000</td>
      <td>42.17</td>
      <td>235.0</td>
      <td>N'Djamena</td>
      <td>1,016</td>
      <td>117.7</td>
      <td>...</td>
      <td>56.40%</td>
      <td>0.04</td>
      <td>15,946,876</td>
      <td>70.70%</td>
      <td>NaN</td>
      <td>63.50%</td>
      <td>1.89%</td>
      <td>3,712,273</td>
      <td>15.454166</td>
      <td>18.732207</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Comoros</td>
      <td>467</td>
      <td>71.50%</td>
      <td>2,235</td>
      <td>NaN</td>
      <td>31.88</td>
      <td>269.0</td>
      <td>Moroni, Comoros</td>
      <td>202</td>
      <td>103.62</td>
      <td>...</td>
      <td>74.80%</td>
      <td>0.27</td>
      <td>850,886</td>
      <td>43.30%</td>
      <td>NaN</td>
      <td>219.60%</td>
      <td>4.34%</td>
      <td>248,152</td>
      <td>-11.645500</td>
      <td>43.333300</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Cuba</td>
      <td>106</td>
      <td>59.90%</td>
      <td>110,860</td>
      <td>76,000</td>
      <td>10.17</td>
      <td>53.0</td>
      <td>Havana</td>
      <td>28,284</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>8.42</td>
      <td>11,333,483</td>
      <td>53.60%</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.64%</td>
      <td>8,739,135</td>
      <td>21.521757</td>
      <td>-77.781167</td>
    </tr>
    <tr>
      <th>43</th>
      <td>Cyprus</td>
      <td>131</td>
      <td>12.20%</td>
      <td>9,251</td>
      <td>16,000</td>
      <td>10.46</td>
      <td>357.0</td>
      <td>Nicosia</td>
      <td>6,626</td>
      <td>102.51</td>
      <td>...</td>
      <td>43.90%</td>
      <td>1.95</td>
      <td>1,198,575</td>
      <td>63.10%</td>
      <td>24.50%</td>
      <td>22.40%</td>
      <td>7.27%</td>
      <td>800,708</td>
      <td>35.126413</td>
      <td>33.429859</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Denmark</td>
      <td>137</td>
      <td>62.00%</td>
      <td>43,094</td>
      <td>15,000</td>
      <td>10.60</td>
      <td>45.0</td>
      <td>Copenhagen</td>
      <td>31,786</td>
      <td>110.35</td>
      <td>...</td>
      <td>13.70%</td>
      <td>4.01</td>
      <td>5,818,553</td>
      <td>62.20%</td>
      <td>32.40%</td>
      <td>23.80%</td>
      <td>4.91%</td>
      <td>5,119,978</td>
      <td>56.263920</td>
      <td>9.501785</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Djibouti</td>
      <td>43</td>
      <td>73.40%</td>
      <td>23,200</td>
      <td>13,000</td>
      <td>21.47</td>
      <td>253.0</td>
      <td>Djibouti City</td>
      <td>620</td>
      <td>120.25</td>
      <td>...</td>
      <td>20.40%</td>
      <td>0.22</td>
      <td>973,560</td>
      <td>60.20%</td>
      <td>NaN</td>
      <td>37.90%</td>
      <td>10.30%</td>
      <td>758,549</td>
      <td>11.825138</td>
      <td>42.590275</td>
    </tr>
  </tbody>
</table>
<p>20 rows × 34 columns</p>
</div>




```python
transform = [ 'Agricultural Land( %)',  'Armed Forces size','Land Area(Km2)','Density\n(P/Km2)',
'Forested Area (%)', 'Co2-Emissions','CPI', 'CPI Change (%)', 'Gasoline Price', 'GDP',
'Gross primary education enrollment (%)','Gross tertiary education enrollment (%)',
'Minimum wage', 'Out of pocket health expenditure', 'Urban_population','Population: Labor force participation (%)',
'Population' ,'Tax revenue (%)', 'Unemployment rate','Total tax rate']
df[transform] = df[transform].applymap(lambda x: float(str(x).replace(',', '').replace('$', '').replace('%', '')))

```

    C:\Users\hp\AppData\Local\Temp\ipykernel_8452\106012158.py:6: FutureWarning: DataFrame.applymap has been deprecated. Use DataFrame.map instead.
      df[transform] = df[transform].applymap(lambda x: float(str(x).replace(',', '').replace('$', '').replace('%', '')))
    


```python
df['Urban_percent'] = df['Urban_population'] / df['Population'] * 100
```


```python
df['Agricultural Land(%)'] = pd.to_numeric(df['Agricultural Land( %)'], errors='coerce')
```


```python
df['Country'] = df['Country'].str.replace("S�����������", "Sao Tome and Principe")

```


```python
df_sorted_unemployment = df.sort_values(by='Unemployment rate', ascending=False)

top_unemployment_countries = df_sorted_unemployment[['Country', 'Unemployment rate']].head(50)

print(top_unemployment_countries)
```

                                  Country  Unemployment rate
    161                      South Africa              28.18
    95                            Lesotho              23.41
    146                       Saint Lucia              20.71
    119                           Namibia              20.27
    61                              Gabon              20.00
    147  Saint Vincent and the Grenadines              18.88
    97                              Libya              18.56
    21             Bosnia and Herzegovina              18.42
    22                           Botswana              18.19
    66                             Greece              17.24
    7                             Armenia              16.99
    166                             Sudan              16.53
    178                           Tunisia              16.02
    115                        Montenegro              14.88
    86                             Jordan              14.72
    186                     United States              14.70
    63                            Georgia              14.40
    164                             Spain              13.96
    72                              Haiti              13.78
    179                            Turkey              13.49
    150             Sao Tome and Principe              13.37
    192                             Yemen              12.91
    80                               Iraq              12.82
    153                            Serbia              12.69
    1                             Albania              12.33
    29                         Cape Verde              12.25
    163                       South Sudan              12.24
    23                             Brazil              12.08
    71                             Guyana              11.85
    40                         Costa Rica              11.85
    2                             Algeria              11.70
    193                            Zambia              11.43
    79                               Iran              11.38
    160                           Somalia              11.35
    0                         Afghanistan              11.12
    171                        Tajikistan              11.02
    51                              Egypt              10.76
    11                        The Bahamas              10.36
    14                           Barbados              10.33
    47                           Djibouti              10.30
    83                              Italy               9.89
    6                           Argentina               9.79
    37                           Colombia               9.71
    108                        Mauritania               9.55
    39              Republic of the Congo               9.47
    24                             Brunei               9.12
    62                         The Gambia               9.06
    116                           Morocco               9.02
    183                           Ukraine               8.88
    190                         Venezuela               8.80
    


```python
df_sorted_unemployment_asc = df.sort_values(by='Unemployment rate', ascending=True)
top_unemployment_countries_asc = df_sorted_unemployment_asc[['Country', 'Unemployment rate']].head(50)
print(top_unemployment_countries_asc)
```

                          Country  Unemployment rate
    141                     Qatar               0.09
    125                     Niger               0.47
    159           Solomon Islands               0.58
    92                       Laos               0.63
    30                   Cambodia               0.68
    12                    Bahrain               0.71
    173                  Thailand               0.75
    144                    Rwanda               1.03
    176                     Tonga               1.12
    121                     Nepal               1.41
    27                    Burundi               1.43
    118                   Myanmar               1.58
    42                       Cuba               1.64
    101                Madagascar               1.76
    182                    Uganda               1.84
    34                       Chad               1.89
    44             Czech Republic               1.93
    172                  Tanzania               1.98
    191                   Vietnam               2.01
    175                      Togo               2.04
    57                   Ethiopia               2.08
    138               Philippines               2.15
    90                     Kuwait               2.18
    18                      Benin               2.23
    85                      Japan               2.29
    19                     Bhutan               2.34
    184      United Arab Emirates               2.35
    68                  Guatemala               2.46
    135          Papua New Guinea               2.46
    70              Guinea-Bissau               2.47
    88                      Kenya               2.64
    130                      Oman               2.67
    177       Trinidad and Tobago               2.69
    127               North Korea               2.74
    96                    Liberia               2.81
    76                    Iceland               2.84
    64                    Germany               3.04
    122               Netherlands               3.20
    117                Mozambique               3.24
    137                      Peru               3.31
    103                  Malaysia               3.32
    28                Ivory Coast               3.32
    129                    Norway               3.35
    31                   Cameroon               3.38
    75                    Hungary               3.40
    110                    Mexico               3.42
    106                     Malta               3.47
    139                    Poland               3.47
    20                    Bolivia               3.50
    33   Central African Republic               3.68
    


```python
df_sorted_Urban = df.sort_values(by='Urban_percent', ascending=False)
top_Urban_pop= df_sorted_Urban[['Country', 'Urban_percent']].head(50)
print(top_Urban_pop)
```

                      Country  Urban_percent
    113                Monaco     100.000000
    156             Singapore     100.000000
    90                 Kuwait     100.000000
    141                 Qatar      99.188014
    16                Belgium      98.040997
    12                Bahrain      97.700773
    149            San Marino      97.368576
    187               Uruguay      95.425992
    106                 Malta      94.678038
    76                Iceland      93.854912
    82                 Israel      92.501000
    6               Argentina      91.991001
    122           Netherlands      91.875998
    85                  Japan      91.725869
    86                 Jordan      91.203000
    61                  Gabon      89.740994
    94                Lebanon      88.758004
    190             Venezuela      88.240002
    46                Denmark      87.994008
    3                 Andorra      87.984496
    123           New Zealand      87.974799
    168                Sweden      87.707999
    35                  Chile      87.643002
    100            Luxembourg      87.618629
    184  United Arab Emirates      86.788996
    23                 Brazil      86.207256
    59                Finland      85.446009
    8               Australia      84.779334
    151          Saudi Arabia      84.065000
    185        United Kingdom      83.651999
    11            The Bahamas      83.131955
    32                 Canada      82.797626
    129                Norway      82.616004
    186         United States      82.459000
    49     Dominican Republic      81.828004
    110                Mexico      81.440824
    162           South Korea      81.430001
    37               Colombia      81.104000
    130                  Oman      80.712974
    60                 France      80.709000
    164                 Spain      80.565001
    97                  Libya      80.393000
    40             Costa Rica      80.076001
    132                 Palau      79.476773
    66                 Greece      79.388003
    15                Belarus      79.044004
    137                  Peru      78.099001
    24                 Brunei      77.942001
    47               Djibouti      77.914972
    107      Marshall Islands      77.416611
    


```python
non_positive_mask = df['Tax revenue (%)'] <= 0

if non_positive_mask.any():
    df = df[~non_positive_mask]
fig = px.scatter(df, x="Tax revenue (%)", y="Total tax rate",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Dependency of tax revenue on tax rate",hover_name="Country")
fig.show()

```



### Dependency of tax revenue on tax rate

With this graph we can come to a conclusion that tax revenue is not dependent on tax rate



```python
non_positive_mask = df['Tax revenue (%)'] <= 0

if non_positive_mask.any():
    df = df[~non_positive_mask]
fig = px.scatter(df, x="Tax revenue (%)", y="Population",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Dependency of tax revenue on population",hover_name="Country")
fig.show()

```



### Dependency of tax revenue on population

With this graph we can come to a conclusion that lower the population the percentage of revenue from tax increases.


```python


fig = px.scatter(df, x="Infant mortality", y="Maternal mortality ratio",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Maternal mortality rate dependency on infant mortality rate",hover_name="Country")
fig.show()

```



### Maternal mortality rate dependency on infant mortality rate

This graphs shows that the death of both mother and child are codependent.


```python
df['GDP_per_capita'] = (df['GDP'] / df['Population'])/1000
```


```python

fig = px.scatter(df, x="GDP_per_capita", y="Infant mortality",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Do high income means less infant mortality?",hover_name="Country")
fig.show()

```



### Do high income means less infant mortality

As we can see from the graph that as the society earns more people tend to have better health infrastructure and thus have better treatment and care for mother and infant thus having less death.


```python

fig = px.scatter(df, x="GDP_per_capita", y="Life expectancy",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="can we buy life with money?",hover_name="Country")
fig.show()

```



### Can we buy life with money

Its same as infant mortality vs GDP per capita people with money have better life style, eating habits, health infrastructure and better condition to live in.


```python

fig = px.scatter(df, x="Physicians per thousand", y="Life expectancy",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Physicians per thousand vs Life Expectancy",hover_name="Country")
fig.show()
```



### Physicians per thousand vs Life Expectancy

Physicians per thousand show the image of a countries health infrastructure and life expectancy increases with more physicians per thousand.


```python

fig = px.scatter(df, x="GDP_per_capita", y="Physicians per thousand",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Does more money means more life saviours? ", hover_name="Country")
fig.show()
```



### Does more money means more life saviour

Both GDP per capita and Physicians per thousand shows the development of a country and both are co dependent on each other so as gdp per capita increases no. of physicians also increases


```python

fig = px.scatter(df, x="Gross primary education enrollment (%)", y="Infant mortality",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Is infants life is dependent on there parents primary education?",hover_name="Country")
fig.show()
```




```python
fig = px.scatter(df, x="Gross tertiary education enrollment (%)", y="Infant mortality",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Is infants life is dependent on there parents tertiary education?",hover_name="Country")
fig.show()
```



### Dependency of infant mortality on parents education

As the society get educated primarily advanced education they tend to get more aware about practices to take care of mother during pregnanncy and what to do to take care of child after birth like all the vaccines required and dietry habits.


```python
non_positive_mask = df['Gasoline Price'] <= 0

if non_positive_mask.any():
    df = df[~non_positive_mask]
fig = px.scatter(df, x="Gasoline Price", y="Minimum wage",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="Gasoline price vs minimum wage",hover_name="Country")
fig.show()
```




```python
fig = px.scatter(df, x="GDP_per_capita", y="Minimum wage",
                 trendline="ols", trendline_options=dict(log_x=True),
                 title="GDP per capita vs minimum wage", hover_name="Country")
fig.show()
```



### GDP per capita vs minimum wage

Its obvious that GDP per capita increases with the increase in minimum wage.



