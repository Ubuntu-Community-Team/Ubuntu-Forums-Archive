---
title: "R-Statistical Package:  Rollback: Have: 3.0.2  Want: 3.0.1"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by Jonathan_Nowacki on 2016-06-20
[FONT=arial]So I'm trying to sync up software versions across servers.  I'm debugging a weird phenomenon where I get slightly different answers on different computers.

Software in question is R-Statistical Package.

[https://www.r-project.org/](https://www.r-project.org/)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]How do I roll back 3.0.2 (2013-09-25) -- "Frisbee Sailing" to  3.0.1 (2013-05-16) -- "Good Sport" on "Ubuntu 14.04.4 LTS"[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I tried this protocol but apt-get can't find the rbase package.


[/FONT]> ~$ sudo apt-get install r-base=3.0.2-1precise0Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '3.0.2-1precise0' for 'r-base' was not found

[FONT=arial][http://askubuntu.com/questions/435232/install-older-version-of-software-and-dependencies](http://askubuntu.com/questions/435232/install-older-version-of-software-and-dependencies)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]===========================================================================

[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]jnowacki@Ubuntu-Z800F:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS"
NAME="Ubuntu"
VERSION="14.04.4 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.4 LTS"
VERSION_ID="14.04"
HOME_URL="[http://www.ubuntu.com/](http://www.ubuntu.com/)"
SUPPORT_URL="[http://help.ubuntu.com/](http://help.ubuntu.com/)"
BUG_REPORT_URL="[http://bugs.launchpad.net/ubuntu/](http://bugs.launchpad.net/ubuntu/)"
jnowacki@Ubuntu-Z800F:~$
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]===========================================================================[/FONT]
[FONT=arial]R version 3.0.2 (2013-09-25) -- "Frisbee Sailing"
Copyright (C) 2013 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu (64-bit)


R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.


  Natural language support but running in an English locale


R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.


Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.


> R.Version();
$platform
[1] "x86_64-pc-linux-gnu"


$arch
[1] "x86_64"


$os
[1] "linux-gnu"


$system
[1] "x86_64, linux-gnu"


$status
[1] ""


$major
[1] "3"


$minor
[1] "0.2"


$year
[1] "2013"


$month
[1] "09"


$day
[1] "25"


$`svn rev`
[1] "63987"


$language
[1] "R"


$version.string
[1] "R version 3.0.2 (2013-09-25)"


$nickname
[1] "Frisbee Sailing"


============================================================================




[nowackj1@dmduv030 ~]$ R


**R version 3.0.1 (2013-05-16) -- "Good Sport"**
Copyright (C) 2013 The R Foundation for Statistical Computing
Platform: x86_64-unknown-linux-gnu (64-bit)


R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.


  Natural language support but running in an English locale


R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.


Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.


> R.Version();
$platform
[1] "x86_64-unknown-linux-gnu"


$arch
[1] "x86_64"


$os
[1] "linux-gnu"


$system
[1] "x86_64, linux-gnu"


$status
[1] ""


$major
[1] "3"


$minor
[1] "0.1"


$year
[1] "2013"


$month
[1] "05"


$day
[1] "16"


$`svn rev`
[1] "62743"


$language
[1] "R"


$version.string
[1] "R version 3.0.1 (2013-05-16)"


$nickname
[1] "Good Sport"
[/FONT]

---

