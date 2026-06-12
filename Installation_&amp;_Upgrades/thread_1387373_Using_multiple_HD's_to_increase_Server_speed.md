---
title: "Using multiple HD's to increase Server speed"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by cilbuper on 2010-01-21
Greetings, 

I am curious if it is possible to use multiple hard drives to increase server speed.  I know I could run stripped drives or RAID0, but was wondering if there is any other way to do it within Linux.  

My default 9.10 Server install has 3 partitions as a default.  Would splitting these on three drives make it any faster?   

What suggestions do you have, if any?

(I have anywhere from 7-15 HD's available)

---

### Post by tgalati4 on 2010-01-21
phoronix has some robust benchmarks that you can install and test your own server's performance.

"One test is worth a thousand expert opinions."

Web speed depends on several things:
PHP, Ruby on Rails, static html?
What is your uplink speed?
How much RAM in your server and what is your clock speed?  Many web languages are CPU bound and are helped with better processors and more/faster cache.

Striping will give you 2x to 3x speeds of a single drive, but only testing will tell if it really helps at the user end.

---

### Post by cilbuper on 2010-01-21
Thank you.  I have 8GB ram and am running a Q6600 on a I45 ASUS Mobo.  

Is that program you mentioned available via apt-get?

---

### Post by tgalati4 on 2010-01-22
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

No, you have to install each test individually.  Most are BSD/Unix-based and are recompiled as you install them.  Some don't compile properly, but there are so many tests to choose from.  You only need a handful to compare your machine with results posted for similar hardware.

That way you can compare your performance with what other folks are getting for similar hardware.

Quick and dirty measurements:

sudo hdparm -tT /dev/sda
sudo hdparm -tT /dev/sdb

sudo hdparm -tT /dev/mdm0 (or whatever your raid device is called)

Comparing the single drive speed with the striped RAID speed will generally show the 2x to 3x speed.

---

