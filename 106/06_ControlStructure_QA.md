控制流程 課堂練習
================
### 問題

#### 傳統的`if(){ }else{ }`和`ifelse()`函數在本質上有什麼不同?

### 解答

`ifelse()`可一次判斷多個元素，可判斷向量。<br/> 其他條件判斷函數則無法判斷向量，且會產生Warning Message。

<hr/>

### 問題

#### 基於`iris`資料內的`Sepal.Length`欄位，新增一個`Type`欄位<br>

#### 邏輯:

-   如果`Sepal.Length` 大於5.5，`Type`設定為"長"
-   如果`Sepal.Length` 小於等於5.5，`Type`設定為"短"

### 解答

``` r
iris$Type<-""
iris$Type<-ifelse(iris$Sepal.Length>5.5,"長","短")

#為精簡版面僅印出前後六行供同學參考
head(iris)  ##印資料表前六行
```

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species Type
    ## 1          5.1         3.5          1.4         0.2  setosa   短
    ## 2          4.9         3.0          1.4         0.2  setosa   短
    ## 3          4.7         3.2          1.3         0.2  setosa   短
    ## 4          4.6         3.1          1.5         0.2  setosa   短
    ## 5          5.0         3.6          1.4         0.2  setosa   短
    ## 6          5.4         3.9          1.7         0.4  setosa   短

``` r
tail(iris)  ##印資料表最後六行
```

    ##     Sepal.Length Sepal.Width Petal.Length Petal.Width   Species Type
    ## 145          6.7         3.3          5.7         2.5 virginica   長
    ## 146          6.7         3.0          5.2         2.3 virginica   長
    ## 147          6.3         2.5          5.0         1.9 virginica   長
    ## 148          6.5         3.0          5.2         2.0 virginica   長
    ## 149          6.2         3.4          5.4         2.3 virginica   長
    ## 150          5.9         3.0          5.1         1.8 virginica   長

### 提醒

-   選取欄位資料的方法：某資料表的某欄位（如:`iris$Sepal.Length`表示iris 資料表的Sepal.Length）
-   `ifelse(判斷式,判斷式TRUE時執行,判斷式為FALSE時執行)`

<hr/>

### 問題

#### 新增一向量`a`，包含1~20的所有奇數，請撰寫一個for迴圈，逐一印出向量`a`內的元素，但遇到13的倍數時，直接跳出迴圈，不繼續執行

### 解答

``` r
a<-seq(1,20,2)

for (i in a){
    if(i %%13==0){
     break 
    }
    print(i)
}
```

    ## [1] 1
    ## [1] 3
    ## [1] 5
    ## [1] 7
    ## [1] 9
    ## [1] 11


<hr/>

### 問題

#### 務必用`ifelse`搭配`for()`迴圈撰寫！<br/>

#### 在`airquality`中新增一個變數`Outdoor`，描述這天的空氣品質是否適合出門，若臭氧`Ozone`大於20，且太陽光強度`Solar radiation`大於100，`Outdoor`設定為“不適合出門”，若臭氧`Ozone`小於20，且太陽光強度`Solar radiation`小於100，設定為“適合出門”，其他情況請設定為”未知“。<br/>

#### 完成設定後，資料集內有幾天為“不適合出門”、“適合出門”和“未知”？<br/>

#### 請將程式碼貼上，並在後方貼上答案

### 解答

``` r
#ifelse()寫法
airquality$Outdoor<-""
airquality$Outdoor<-
  ifelse(airquality$Ozone>20&airquality$Solar.R>100,"不適合出門",
       ifelse(airquality$Ozone<20&airquality$Solar.R<100,"適合出門","未知"))
table(airquality$Outdoor)
```

    ## 
    ## 不適合出門       未知   適合出門 
    ##         66         29         16

<hr/>

### 問題

#### 請以`for()`迴圈撰寫以下程式碼：

長庚汽車公司生產的汽車都使用數字編碼，因為4結尾很不吉利，所以當個位數是4的時候，此編碼必須跳過不使用，目前長庚汽車公司所生廠的汽車已經從1號編到65號，請逐一印出長庚汽車公司所有生產的汽車編號。 提示：十位數與個位數分開處理、next、break

#### 邏輯

-   單層迴圈：從1印到65，如果汽車編號i除以10等於4的時候，則跳過
-   雙層迴圈：i為十位數，j為個位數，個位數等於4時跳過不印，汽車編號為i\*10+j，而印出的汽車編號需介於1到65之間

### 解答

``` r
##單層迴圈作法
for(i in c(1:65)){
    if(i%%10==4){
      next
    }
    print(i)
}
```

    ## [1] 1
    ## [1] 2
    ## [1] 3
    ## [1] 5
    ## [1] 6
    ## [1] 7
    ## [1] 8
    ## [1] 9
    ## [1] 10
    ## [1] 11
    ## [1] 12
    ## [1] 13
    ## [1] 15
    ## [1] 16
    ## [1] 17
    ## [1] 18
    ## [1] 19
    ## [1] 20
    ## [1] 21
    ## [1] 22
    ## [1] 23
    ## [1] 25
    ## [1] 26
    ## [1] 27
    ## [1] 28
    ## [1] 29
    ## [1] 30
    ## [1] 31
    ## [1] 32
    ## [1] 33
    ## [1] 35
    ## [1] 36
    ## [1] 37
    ## [1] 38
    ## [1] 39
    ## [1] 40
    ## [1] 41
    ## [1] 42
    ## [1] 43
    ## [1] 45
    ## [1] 46
    ## [1] 47
    ## [1] 48
    ## [1] 49
    ## [1] 50
    ## [1] 51
    ## [1] 52
    ## [1] 53
    ## [1] 55
    ## [1] 56
    ## [1] 57
    ## [1] 58
    ## [1] 59
    ## [1] 60
    ## [1] 61
    ## [1] 62
    ## [1] 63
    ## [1] 65

``` r
##雙層迴圈作法
for(i in c(0:6)){
  for(j in c(0:9)){
    if(j==4){
      next
    }else{
        if((i*10+j)>0 & (i*10+j)<66){
            print(i*10+j)
        }
    }
  }
}
```

    ## [1] 1
    ## [1] 2
    ## [1] 3
    ## [1] 5
    ## [1] 6
    ## [1] 7
    ## [1] 8
    ## [1] 9
    ## [1] 10
    ## [1] 11
    ## [1] 12
    ## [1] 13
    ## [1] 15
    ## [1] 16
    ## [1] 17
    ## [1] 18
    ## [1] 19
    ## [1] 20
    ## [1] 21
    ## [1] 22
    ## [1] 23
    ## [1] 25
    ## [1] 26
    ## [1] 27
    ## [1] 28
    ## [1] 29
    ## [1] 30
    ## [1] 31
    ## [1] 32
    ## [1] 33
    ## [1] 35
    ## [1] 36
    ## [1] 37
    ## [1] 38
    ## [1] 39
    ## [1] 40
    ## [1] 41
    ## [1] 42
    ## [1] 43
    ## [1] 45
    ## [1] 46
    ## [1] 47
    ## [1] 48
    ## [1] 49
    ## [1] 50
    ## [1] 51
    ## [1] 52
    ## [1] 53
    ## [1] 55
    ## [1] 56
    ## [1] 57
    ## [1] 58
    ## [1] 59
    ## [1] 60
    ## [1] 61
    ## [1] 62
    ## [1] 63
    ## [1] 65

<hr/>
