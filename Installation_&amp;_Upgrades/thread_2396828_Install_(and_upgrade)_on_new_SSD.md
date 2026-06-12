---
title: "Install (and upgrade) on new SSD"
date: 2018-07-21
forum: Installation &amp; Upgrades
---

### Post by Gillingham on 2018-07-21
Hi 

In the next few weeks I will be upgrading my 16.04 system to 18.04 and getting a new SSD drive to use for the root partition (home and data will remain on the drives where they are).  Are there any special precautions I should be taking or things I could miss when doing this?  The system is a general use / mythtv box.

I know the first thing to do is to make sure I have a full backup before starting.  

Thank you

David

---

### Post by oldfred on 2018-07-21
I suggest just doing a new clean install with 18.04. You then have the old 16.04 install to go back to for any settings you forgot to include in your backups.
I still have 14.04, 16.04 & 18.04 on my SSD, since it is 120GB and each install is 25 or 30GB of drive and I still have some space unallocated.

They do suggest not fully utilizing SSD. Either leave some space unallocated or space unused inside partitions so SSD can manage itself.

Many SSD need firmware updates. Not always easy or possible to do from Linux.

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by Gillingham on 2018-07-22
Great thank you for those useful links.

David

---

