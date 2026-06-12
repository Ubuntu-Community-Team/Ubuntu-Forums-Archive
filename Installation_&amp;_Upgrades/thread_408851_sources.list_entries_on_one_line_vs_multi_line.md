---
title: "sources.list entries on one line vs multi line"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by clickwir on 2007-04-13
As far as apt-get is concerned, is there a difference between: 

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **main restricted universe multiverse**
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates **main restricted universe multiverse**


and 

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **main restricted**
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **universe multiverse**
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates **main restricted**
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates **universe multiverse**


In other words. Is there any difference if you put "main" "restricted" "universe" and "multiverse" all on line line or separate lines?

I keep an original copy of my sources.list and a stripped down one that doesn't have all the comments and has the least number of lines. To me it's easier to keep track of and looks cleaner.

---

### Post by amohanty on 2007-04-13
Nope.

AM

---

