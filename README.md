# Amazon-Web-Scraping-Project
Web scraping is the process of collecting and parsing raw data from the Web, and the Python community has come up with some pretty powerful web scraping tools. I have made use of Beautifulsoup and requests modules imported as python libraries in the code for the extraction of data from the amazon website. You can extract any type of data from the website when we cannot get the help from APIs.In such scenarios, we'll be marching towards web scraping using python which will prove to be a great alternative. So here's the code performed in jupyter notebook:
# import libraries
from bs4 import BeautifulSoup
import requests
import time
import datetime


# CONNECT TO WEBSITE AND PULL IN THE DATA 
URL = 'https://www.amazon.in/Seek-Buy-Love-Spreadsheet-Accountant/dp/B0CYXL86PN/ref=sr_1_10?crid=23OKE25P1XFUX&dib=eyJ2IjoiMSJ9.EkFu8ZndNLnSqdsrbxi1MS0zvZIDby-x_CYoX0zD7pjX7WBTzomK9qQ-9Pan22laSZqD-3ZiYx9qFCUd087ZjReFMqtAaqr0EtFEgyNVBLrCaWleYeTFeTIh3oLrtaHrh-SLr64-mJ5bb0voWvLJCsBFtRiHSvGsHK66hAHeCsWu1Cw8nBNhIJNVpKgxboYm-ENtodG8KchoG0pApaoMI_wmOoADTBTdFhLjxVgGMA0TC9SZnjskm-PCE4gqeX17CsvOiT5X_IXWdjYefgXIH8aMePTvVA3bQu5wYEkgSmw.F9JwuvFIc59sdtHd9J0PVoeCSTKtQPp6K96VtViGq44&dib_tag=se&keywords=data%2BAnalyst%2Btshirt&qid=1713894429&sprefix=data%2Banalyst%2Btshirt%2Caps%2C207&sr=8-10'
headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}
page = requests.get(URL, headers=headers)
soup = BeautifulSoup(page.content, "lxml")

title = soup.find(id='productTitle').getText()
print(title)
facts = soup.find(id='productFactsDesktopExpander').getText()
print(facts)
# OUTPUT
  Seek Buy Love Relax Spreadsheet Funny T-Shirt, Accountant Financial Analyst Tee, Casual Office Humor Graphic Shirt, Unisex Cotton Top (Large, Black)       
   Product details    
Material composition 
  
Cotton 
    
Fit type 
  
Regular Fit 
    
Sleeve type 
  
Short Sleeve 
    
Length 
  
Standard Length 
    
Neck style 
  
Crew Neck 
    
Style 
  
Western 
    
Country of Origin 
  
India 
    About this item   UNIQUE DESIGN MAGIC - Stand out with our vibrant, trending designs, perfect for those who dare to be different. Each shirt is a canvas of creativity, aligning with the pulse of street fashion.   PURE COTTON COMFORT - Experience unparalleled comfort in our 100% cotton tees. Soft on your skin, perfect for all-day wear, whether you're lounging at home or out conquering the streets.   SIZE PERFECTION GUARANTEED - Find your perfect fit from our wide size range, designed to flatter and fit all body types impeccably, ensuring you look and feel your best. ADD TO CART now.   GIFT-GIVING HERO - Be the champion of Christmas gifts for men or birthday gift for guys. Our crew t shirts are wearable expressions of personality, making them perfect cool gifts for guys.   FUNNY T-SHIRT CHARM - Laugh out loud with our funny t-shirts for men. They're not just tees; they're cheer spreaders, ideal for lightening the mood and bringing smiles wherever you go.    Additional Information    
Manufacturer 
  
Seblo, 9312915036 
    
Packer 
  
Seblo 
    
Item Dimensions LxWxH 
  
71.1 x 53.3 x 2.5 Centimeters 
    
Net Quantity 
  
1.00 count 


# tracking when the data was collected
import datetime

today = datetime.date.today()
print(today)
# OUPTUT
2024-04-23

# create CSV and write headers and data into file

import csv

header = ['Heading','About','Date']
data = [title,facts,today]

with open('AmazonWebScraperDataset.csv', 'w', newline='', encoding='UTF8')as f:
   writer = csv.writer(f)
   writer.writerow(header)
   writer.writerow(data)

   # reading csv file data and getting the data 
import pandas as pd 

df= pd.read_csv(r'C:\Users\nisht\AmazonWebScraperDataset.csv')
print(df)

# now we are appending data to the csv

with open('AmazonWebScraperDataset.csv', 'a+', newline='', encoding='UTF8')as f:
    writer = csv.writer(f)
    writer.writerow(data)

    
# reading the csv file again after the updated price has been checked from the website for the product.
import pandas as pd 

df= pd.read_csv(r'C:\Users\nisht\AmazonWebScraperDataset.csv')
print(df)
# OUTPUT
 Heading  \
0          Seek Buy Love Relax Spreadsheet Funny ...   
1          Seek Buy Love Relax Spreadsheet Funny ...   
2          Seek Buy Love Relax Spreadsheet Funny ...   
3          Seek Buy Love Relax Spreadsheet Funny ...   
4          Seek Buy Love Relax Spreadsheet Funny ...   

                                               About        Date  
0     Product details    \nMaterial composition \...  2024-04-23  
1     Product details    \nMaterial composition \...  2024-04-23  
2     Product details    \nMaterial composition \...  2024-04-23  
3     Product details    \nMaterial composition \...  2024-04-23  
4     Product details    \nMaterial composition \...  2024-04-23  



