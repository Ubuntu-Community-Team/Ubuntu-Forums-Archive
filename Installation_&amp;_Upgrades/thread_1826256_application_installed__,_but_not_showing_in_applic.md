---
title: "application installed  , but not showing in application listv"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by raja.genupula on 2011-08-16
i have installed d4x its not showing in Ubuntu 11.04 dash but its showing as installed in software center . i have tried the command of " which d4x " and i got nothing . please help on this . 

```
assassin@genupulas:~$ sudo dpkg --configure d4x
[sudo] password for assassin: 
dpkg: warning: there's no installed package matching d4x
```



```
assassin@genupulas:~$ which d4x
assassin@genupulas:~$ 

```

---

### Post by raja.genupula on 2011-08-17
come on , please guys i need a good GUI downloader and i got it as d4 . please help to out of this issue

---

### Post by jerrrys on 2011-08-17
try this.  open a terminal and enter:

sudo apt-get install d4x

if it says the same thing, d4x is already installed.  try opening it in terminal.

---

### Post by raja.genupula on 2011-08-18
thanks for pickup 


```
assassin@genupulas:~$ sudo apt-get install d4x
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package d4x is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  d4x-common

E: Package 'd4x' has no installation candidate
assassin@genupulas:~$ 

```

---

### Post by jerrrys on 2011-08-18
ok, i looked it up and it is not available in 11o4.  you need to find another one

[http://www.ubuntugeek.com/list-of-download-managers-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-download-managers-available-in-ubuntu.html)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=download+manager&sa=Search&cof=FORID:9#986](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=download+manager&sa=Search&cof=FORID:9#986)

and firefox has plugins (download managers)

---

### Post by raja.genupula on 2011-08-18
man i am not able to get any thing i want . i have got another downlaod manager i got the problem as dependencies .

---

