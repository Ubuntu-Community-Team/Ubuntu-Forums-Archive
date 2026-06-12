---
title: "How Do I Copy My Slave (Ubuntu) Drive?"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by casparov on 2008-08-25
Hi, Everyone...

I dual boot Windows 2000 and Ubuntu, using the slave drive for Linux.

I am building a new PC and will copy my Windows drive using the standard software that comes w/ the new Seagate drive.  (I assume that this will copy the GRUB boot manager?)  But how does one go about copying the slave drive to another (new) slave drive?  I really like my Ubuntu experience and would like to keep things going but would like to avoid rebuilding Ubuntu from scratch.   

Many thanks to anyone who reads this and/or posts a reply. 

Regards, 

Casp

---

### Post by prshah on 2008-08-25
> **casparov said:**
>  But how does one go about copying the slave drive to another (new) slave drive?  

Take a look at [Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643") for a good many. easy to use and detailed tips.

From the above, I'd use the "dd" command, and avoid partimage, unless you have only one partition.

Even if the two HDDs are different sizes, you can still use the "dd" command, then resize the partitions later.

---

### Post by casparov on 2008-08-25
Thank-you, prshah, I will return once I have reviewed your suggestion.

All Regards, 

Casp

---

