---
title: "cant partition a disk"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by hhtuer on 2006-12-28
im trying intall ubuntu 6.10 (alternate live cd) ,i've two partitions on my disk ( one the main one with windows and everything else , the the second one with the installation of windows xp ). so when it come to partition a disk , im choosing to partition the first one (with the windows) and its telling me that there is not enough space ( there is 200 gb wonder why ?? ). but when i choose partition a whole drive, its telling me that all the partition are going to be deleted . does that mean that im going to looose everything whats in it? ?? im new to linux, but also sick of windows, so its time to change. my graphic card geforce 6600 gt is not compatible with linux so i need to use the alternate live cd.  i know that i need to have 3 linux partitions "/" , "swap" and "/home" , but i havn't got a clue how to do it? will i loose all the data if i partition a whole drive ??

---

### Post by hhtuer on 2006-12-28
Please Help!!!!!!!!!!

---

### Post by wpshooter on 2006-12-28
Yes, I believe you will.  But if you are wanting to switch over to Ubuntu, what would that matter ?

Have you tried installing from the DESKTOP CD using the safe graphics mode parameter ?

---

### Post by hhtuer on 2006-12-28
yes, it doesn't work, one guy told me to install the alternate version and then update the video card in command line ( i got the instruction ). so the only way is to do it on altaranate Cd, but i cant partition it, is there any way to do it ?? or am i doing something wrong ?? i might borrow some other video card off someone , but i would love to install it on my one...

---

### Post by louieb on 2006-12-28
I believe the alternate CD uses cfdisk for its partitioner software.  cfdisk is limited in that it cannot resize partitions. If you are sure there is nothing on the the first partition you want to keep then you can use the manual partitioning option to delete it. This will create unallocated space needed to install Ubuntu. 
I don't feel very good about giving you an answer because I am not sure about how you have your drive partitioned or if you have a partition you can loose. Partitioning is the one point of the install process that can destroy all the data on the computer and turn it into a door stop. 
In your case because you have data you can't afford to loose and do not have it backed up.  I don't believe I would  install Ubuntu at this time. 
My favorite way of Dual booting in cases like yours is to go out and get a second hard drive. Unplug  the current hard drive and plug in the new. That way if you make a mistake, its ok just try again until you get it right.

---

### Post by hhtuer on 2006-12-28
i might get another video card off someone, and install the proper desktop cd . thanks anyway...

---

