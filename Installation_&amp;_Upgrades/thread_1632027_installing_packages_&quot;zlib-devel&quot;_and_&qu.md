---
title: "installing packages &quot;zlib-devel&quot; and &quot;ncurses-devel&quot;"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by 71GA on 2010-11-27
Hello!

I wanted to install packages "zlib.devel" and "ncurses-devel", but when i insert following commands, 
```
sudo apt-get install ncurses-devel
``````
sudo apt-get install zlib-devel
```terminal in both cases returns,
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package zlib-devel
```.

This means it cant find them, so i went browsing and found both of them, 
[http://ftp.gnu.org/pub/gnu/ncurses/](http://ftp.gnu.org/pub/gnu/ncurses/) 
[http://www.zlib.net/](http://www.zlib.net/).

I downloaded them and i got 2 files, 
```
ncurses-5.7.tar.gz
``````
zlib-1.2.5.tar.bz2
```[B]
My question is how to install those 2?[/B]


Thank you!

---

### Post by andrewthomas on 2010-11-27
how about 
[B]  ```
sudo apt-get install zlib1g-dev libncurses5-dev
```?
[/B]

---

### Post by 71GA on 2010-11-27
OK this worked! TY andrewtomas :popcorn:

I really have to complain about something. When i tried to install 3rd party program terminal said i need zlib-devel and ncurses-devel and not ncurses-dev and zlib-dev... 

**Is it sooooo hard to specify exact packages name omg?!**

---

### Post by karthick87 on 2010-11-27
Try apt-get update and then install the packages,

```
sudo apt-get update
```

---

