---
title: "Segmentation Fault in partman"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by 10011010 on 2010-05-27
Ok, this isn't the first time I have installed Ubuntu or Linux in general, but the first time I've encountered this error.  I'm running the 10.04 Alternate CD or an old machine, can verify the CD, make it through the installation up to the point of partitioning.  

Now when it reads my disks, the dialog box throws a disk choice as ??? ????.  I try to run it anyways and it always faults.

I know there used to be some workaround back in the day when SATA was new to make it ATAPI, is there something I need to do for this old drive?  It is old EIDE (8 GB), but cannot be upgraded.

Disclaimer, I already tried disabling dmraid, set the fb=false option, noacpi option, and even tried the edd=on option.  If there is a simple installer flag, I haven't been able to find it in the Wiki.

Running the alt install, text based, on  a celeron 600mhz, 64mb RAM.

Thanks for the help!

BTW, there is no fdisk on this cd :(

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by 10011010 on 2010-05-27
It is a memory loss issue, running out of mem.

---

