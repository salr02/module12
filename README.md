# module12
---
title: "Book mod 12"
author: "Salma Rahmouni"
date: "2024-11-18"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown
Hello, I am Salma and I am testing out an R Markdown file.  
In this analysis, we compare the ratings of various books by Brandon Sanderson. 
#libraries
```{r, library}
library(ggplot2)
library(dplyr)
library(tidyr)
```
#datasets(I will be using Open Library API for real-time data collection for the final))
```{r, data}
book_data <- data.frame(
  book_title = c("Mistborn", "The Way of Kings", "Elantris", "Words of Radiance", "Oathbringer"),
  goodreads_rating = c(4.4, 4.7, 4.1, 4.6, 4.8),
  amazon_rating = c(4.5, 4.6, 4.3, 4.7, 4.9)
)


book_data_long <- book_data %>%
  pivot_longer(cols = c(goodreads_rating, amazon_rating), 
               names_to = "platform", 
               values_to = "rating")


## Including Plots


ggplot(book_data_long, aes(x = book_title, y = rating, fill = platform)) + 
  geom_bar(stat = "identity", position = "dodge") + 
  theme_minimal() + 
  labs(title = "Comparison of Book Ratings (Goodreads vs Amazon)", 
       x = "Book Title", 
       y = "Rating") + 
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```
