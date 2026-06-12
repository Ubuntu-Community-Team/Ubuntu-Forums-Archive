---
title: "How to install xcms package in R"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by paulmilliken on 2010-05-25
To install the xcms package in R on Lucid Lynx (10.04) follow these steps (assuming R is already installed):
1.  In a bash shell type the following to install the necessary dependencies ```
sudo apt-get install libnetcdf-dev build-essential
```
2.  Download the latest xcms_*.*.*.tar.gz file from [http://www.bioconductor.org/packages/release/bioc/html/xcms.html](http://www.bioconductor.org/packages/release/bioc/html/xcms.html)
3.  Navigate to the directory where you downloaded the file (eg. type ```
cd ~/Downloads
``` if that is where you saved it)
4.  Run R as root by typing ```
sudo R
```
5.  At the R prompt, type: ```
install.packages("./xcms_1.23.1.tar.gz")
```

---

