---
title: "will not install"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by udornf4 on 2010-06-28
Laptop is Dell 640 running Win XP, 1G of memory, 
 
Ubuntu 10.04 will not install. Created a separate partition (15G) for Ubuntu.
 
I have downloaded the OS twice and burned to two different CDs - makes no difference. Still get the same errors below.
 
Everytime I boot from the CD I get "unrecoverable error" message. Then I get the OS to run on the CD.  Then, I try to install from the desk top installation file. I get the following (I believe step three):
 
"No root system defined. Please correct this from the partitioning menu"
 
I consider myself above average Windows guy - but do not know what a "partitioning menu" is (or where to find it)
 
Hate to whine and complain - but I been trying to install Ubuntu 10.04 for two days now:mad:

---

### Post by bumanie on 2010-06-28
Read through [this]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml") - hope it helps answer the problem you are having.

---

### Post by udornf4 on 2010-06-29
Installed OK in the "side by side" mode (with XP as the other OS).

It should be noted that Ubuntu doesn't install in a pre-made BLANK partition. I made a partition for Ubuntu using Acronis Disk Director - then tried to install Ubuntu there. - Nope! I think it would have worked if I had let Ubuntu installer make the Partition...

Thanks :popcorn:

---

### Post by ronparent on 2010-06-29
The message "No root system defined. Please correct this from the partitioning menu" occurs because you need to select "/" for the root system. "/" is the linux designation for the root file system. If you omit this selection then the installer doesn't know what you want installed to the partition you selected for the install.

---

