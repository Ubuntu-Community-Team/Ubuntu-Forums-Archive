---
title: "Live CD 'manual partition edit' bug fixed"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2009-01-14
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/310083/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/310083/)

Can anyone tell me how to find out when this makes its way on to the daily builds?  Hopefully I'll soon be able to install Jaunty after several weeks without....

---

### Post by jerrylamos on 2009-01-14
There was an attempt to fix manual partition edit in today's 20090114 however looked VERY DANGEROUS to me.  I got further on manual edit partition but failed again!

Just doing a format partition wanted to REWRITE THE ENTIRE PARTITION TABLE!  

This is a quad boot, and I DON'T WANT THE PARTITION TABLE REWRITTEN!

Interesting to see if anyone else has this trouble...yes, they did, launchpad bug #313452.

Jerry

---

### Post by DavidONE on 2009-01-15
Good catch.  I'll keep an eye on that bug.

---

