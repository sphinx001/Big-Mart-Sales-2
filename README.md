# Big-Mart-Sales-2
second plot
setwd("C:\\Users\\Stella\\Desktop\\Data")  # set workig directory
library(data.table) # used for reading and manipulation of data
library(dplyr)      # used for data manipulation and joining
library(ggplot2)    # used for ploting 
# open requested files
train = fread("Train_BigMart.csv") 
test = fread("Test_BigMart.csv")
submission = fread("SampleSubmission_BigMart.csv")
test[,Item_Outlet_Sales := NA]
combi = rbind(train, test)
# Item_Weight vs Item_Outlet_Sales
p9 = ggplot(train) + 
     geom_point(aes(Item_Weight, Item_Outlet_Sales), colour = "violet", alpha = 0.3) +
     theme(axis.title = element_text(size = 8.5))
# Item_Visibility vs Item_Outlet_Sales
p10 = ggplot(train) + 
      geom_point(aes(Item_Visibility, Item_Outlet_Sales), colour = "violet", alpha = 0.3) +
      theme(axis.title = element_text(size = 8.5))
# Item_MRP vs Item_Outlet_Sales
p11 = ggplot(train) + 
      geom_point(aes(Item_MRP, Item_Outlet_Sales), colour = "violet", alpha = 0.3) +
      theme(axis.title = element_text(size = 8.5))
second_row_2 = plot_grid(p10, p11, ncol = 2)
plot_grid(p9, second_row_2, nrow = 2)
