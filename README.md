# Amazon_Vine_Analysis

## Overview

The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.
In this project, we will study a dataset holding reviews for shoes by completing the following steps:

  * Use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin.
  * Use PySpark to determine if there is any bias toward favorable reviews from Vine members in the dataset.
  * Write a summary of the analysis to submit to the SellBy stakeholders.
### Aim
The aim of this project is to analyze Amazon reviews written by members of the paid Amazon Vine program to determine if there is any bias towards reviews that were written as part of the Vine program.
Of the 50 datasets, I chose to analyze reviews that were made by users in the "Toys" category.

## Determine Bias of Vine Reviews
Using PySpark we have extracted the same dataset in a new Google Colab Notebook Vine_Review_Analysis.ipynb . We have recreated the vine_table and we have performed the following steps:

  * Created a new DataFrame to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful and to     avoid having division by zero errors.

  * Filtered the new DataFrame and created a new DataFrame to retrieve all the rows where the number of helpful_votes divided by total_votes is equal to or greater than     50%.

  * Filtered the later DataFrame and created a new DataFrame or table that retrieves all the rows where a review was written as part of the Vine program/paid, and           another one where the review was not part of the Vine program/unpaid.
  
  
  ![ss1](https://user-images.githubusercontent.com/111541268/208183678-a6605637-bcd0-44a3-900e-a516b27c5b70.png)
          Table: Paid Vine Program
  


![ss2](https://user-images.githubusercontent.com/111541268/208183789-ce850aba-97c3-4650-acf8-ede378c3f0ea.png)
      Table:Unpaid Vine Program


  * In the last part, we have calculated the total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for paid and unpaid program.
  
  ## Results
  
  Based on our analysis, we have found the following:

   * The total number of Vine reviews for paid is 16358, while the total number of reviews for unpaid program is 1429109.
   
   
   ![ss3](https://user-images.githubusercontent.com/111541268/208183845-45c0b9ab-9b64-4da7-89ef-0c1831750110.png)
           Fig: total vine paid review

   
   
   ![ss4](https://user-images.githubusercontent.com/111541268/208183917-78832d1e-580b-45af-8dc0-21bd977fcdf4.png)
           Fig: Total vine unpaid review
           
           
           
   * The number of 5-star reviews for paid program is 6432  while it's 801043 for unpaid program.
   
   
   ![ss7](https://user-images.githubusercontent.com/111541268/208184296-4eb4ddc6-8ada-48b7-8bf3-1144f25ea174.png)
               Fig: paid 5-star review
               
               
               
    ![ss8](https://user-images.githubusercontent.com/111541268/208184358-7202853c-10df-453d-b74d-bb5dc777216a.png)
              Fig: unpaid 5-star review


  * The percentage of 5-star reviews for paid program is: 39% which is so close to the percentage of 5-star reviews for unpaid program: 56%
  
  
  ![ss5](https://user-images.githubusercontent.com/111541268/208184027-9b7fc914-63ff-443f-bd8a-cdce04964c77.png)
         Fig: percentage paid review
         
         
  ![ss6](https://user-images.githubusercontent.com/111541268/208184076-3b6682aa-28a6-49cb-969d-cd25074341cd.png)
         Fig: Percentage unpaid review

         
  ## Summary
  
Even if the percentage of 5-star reviews for paid and unpaid program is close one should consider the existence of a bias for reviews in the Vine program due to the considerably big difference between the total number of Vine reviews and non-Vine reviews; In other words, the number of Vine reviews is a not even close to 1% of that of the non-Vine reviews. I would suggest performing a T-test to make sure if there's a statistical difference between the mean of the sample and population distribution.
  
