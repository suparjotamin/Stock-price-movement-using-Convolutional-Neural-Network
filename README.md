# Stock-price-movement-using-Convolutional-Neural-Network 

## Creator/ Contributor
Suparjo

## Purpose of Project
to create a model that can predict the stock price movement with the input of the candlestick and then do a simulation of trading

## Content CNN
### Data acquisition
in this project, I will use 10 stocks from LQ45, Indonesia. I loaded the tabular data that consist of date, Open, High, Low, Close. I obtained the data by using Yahoo Finance API package https://pypi.org/project/yfinance/. 
```
!pip install yfinance
import yfinance as yf
data = yf.download(stock,start_date,end_date)
```

### Data Transfromation
After we obtain the tabular data, we will convert the tabular data into images of candlestick by using the mlpfinance package https://github.com/matplotlib/mplfinance
```
!pip install mpl_finance
from mpl_finance import candlestick2_ochl
candlestick2_ochl(....)
```

### Variation of input and model
there are two jargon that will be frequently be used
1. Timestep<br>
Timestep is the number of candlestick that will be used for the input. we will variate the timestep with 20, 40, and 60

2. Timegap<br>
is the number of day for the movement to be predicted or output of model. we will variate the timegap with 1,7, and 14<br>
eq : if timestep is 14, we will predict the movement of stock price (up or down) 14 days from today

for the convolutional neural network, we will variate the size of filter (3 and 5) and the number of filter and pooling in pair ( 3 and 4)
https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53
by : Sumit Saha.
for the explanation of Convolutional Neural Network.

### Data Segmentation
because we use 36 variation, we will segment the data with the principle predict a year with the last four year to train the model. for example, we will use data of candlestick from 2016 until 2019 to be used to predict data of 2020

the notebook of **data aquisition**, **data transformation**, **variation of input and model**, and **data segmentation can be found** [here](https://github.com/suparjotamin/Stock-price-movement-using-Convolutional-Neural-Network/blob/master/Stock_Price_Movement_Prediction_Best_variation.ipynb)

and the notebook to review or the result to show which variation can be found [here](https://github.com/suparjotamin/Stock-price-movement-using-Convolutional-Neural-Network/blob/master/Stock_Price_Movement_Prediction_Best_Variation_Review.ipynb)

the most dominant variation to give the highest accuracy (73.3%) is variation with **timestep 60** and **timegap 14**. also, for the CNN model **with filter size 3 and 4 pairs of convolution and pooling**

## Simulation
we will simulate the trading of stock with the target to get the most profit. This step may variate and can be optimized later. Because of the Timestep we used is 14, it means we will predict the 14 later day movement relative to the latest day. we will use the deposit technique to resolve the timestep problem.

result :
all of the simulation with model can outperform the simulation by investing (buy and hold)
the notebook that do the simulation can be found [here](https://github.com/suparjotamin/Stock-price-movement-using-Convolutional-Neural-Network/blob/master/Stock_Price_Movement_Prediction_%2B_Simulation.ipynb)

