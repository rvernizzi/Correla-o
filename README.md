# Neste projeto melhorei o meu conheciemento sobre técnicas de ETL e correlação
# Objetivo deste estudo: Comparar os gastos através da análise de correlação entre gastos com saúde e outras variáveis de um banco de dados
# Ferramenta utilizada: R
# Pacotes: library(car); library(haven); library(QuantPsyc); library(boot); library(magrittr); library(openxlsx); library(tibble); library(forcats); library(tibble)
# Código:

library(car)
library(haven)
library(QuantPsyc)
library(boot)
library(magrittr)
library(openxlsx)
library(tibble)
library(forcats)
library(tibble)

#Load data
data<-read.xlsx("C:/Users/rafael/OneDrive/Documentos/Reglinear_Isaias/budget_8.xlsx","tab1")

View(data)

str(data)
data<-as_tibble(data)
str(data$profession)

prof<-factor(data$profession)
str(prof)
levels(prof)<-c("Doctor","Enginner")
prof
table(prof)
table(data$profession)
data$profession<-prof


str(data$Marital.status)
marital_status<-factor(data$Marital.status)
str(marital_status)
levels(marital_status)<-c("Single","Married","Divorced","Widower")
table(data$Marital.status)
data$Marital.status<-marital_status

str(data$income)
income_2<-factor(data$income)
levels(income_2)<-c("<1SM","1 - 3 SM","3 - 5 SM",">5SM")
table(data$income)
table(income_2)
data$income<-income_2

str(data$number.of.children)


sum(is.na(data))


## x? y?
Y = Health Spending
x = Age, Yers of study, Leisure spending,
Education spending, num of children


names(data)
data_num<-data[,c(2,6,8,9,10,11)]
cor(data_num)
pairs(data_num)
