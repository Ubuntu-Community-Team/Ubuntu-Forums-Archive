---
title: "should i remove before installation"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by karlb1483 on 2011-11-03
Hi 

I have been testing and enjoying Ubuntu for several weeks now and have decided to go for a windows dual boot (got to keep windows for work)

I have Ubuntu 11.10 running happily and with no problems on a Lenovo SL 500 and was wondering if i need to remove the Wubi instal from windows before taking the dip.

Also are there any know issue with my Thinkpad Lenovo sl500, i cant seem to find any and everything is running great.

Cheers

---

### Post by darkod on 2011-11-03
I would personally remove wubi first. For dual boot you will need to free some unallocated space, and by keeping wubi that will also take up space on the windows partition.

Make sure you copy any files you want to keep, google for the correct procedure to remove it (not using wubi myself), using windows disk management shrink your windows partition to create unallocated space (if running vista or 7 it has the tool to shrink), and then just install onto the unallocated space.

---

### Post by Frogs Hair on 2011-11-03
Wubi can interfere with running the ISO cd in some cases . As stated above I use Windows disk management to shrink the disk volume and use that space for Ubuntu .

---

### Post by bcbc on 2011-11-03
There's no reason to remove wubi before doing a dual boot installation - except as stated by *darkod*: to make more space. It cannot interfere with a dual boot install.

You can even [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi so you don't have to set everything up again.

---

