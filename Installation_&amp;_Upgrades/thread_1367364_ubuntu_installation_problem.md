---
title: "ubuntu installation problem"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by everdhil on 2009-12-29
hi every one,
i am new to linux and ubuntu,
before a week i installed ubuntu 9.04 on my desktop, where my windows XP is also there.
while i up-grading to latest version of ubunto through internet,  my power went off, once again i restarted and logged in ubuntu the linux OS get crashed due to partial upgration and i once again formated remaining space and partioned the hard disc using live CD,
the installation process started normal and i filled the required login details, installation started with 15% and with in a very few seconds, installation process gone back to the live CD,
the installation didnt completed and it continues in live CD.
i tried many time formating and partision the remaining space , the same problem persists 

help me to get ride of this problem and help me to install the full version in hard drive..

---

### Post by zvacet on 2009-12-30
When during installation proces came to the partitioning choose manual way and delete existing Ubuntu partition and on that free space install Ubuntu again.

---

### Post by DarrenMayLin on 2010-01-05
Hi,
I have a similar problem to everdhil's.  I believe a partial update from 9.04 to 9.10 was accepted accidentally after about only 350 of the 1500 files.  The notebook now boots to a log in screen (a window that has a picture of a computer at the top and "(none)" written below it).  I have two selections available, my username from the 9.04 install and "Other".  The mouse pointer shows but can't be moved from the trackpad.  I can log in through both options using the keyboard and the previous username and password but after initially showing only the brown Ubuntu background the background turns white.  No buttons or menus are available at any stage, only the mousepointer that doesn't move.

I now have the Ubuntu 9.10 CD which offers two options, "Install Ubuntu" or "Rescue a broken system".  I am endeavoring to retrieve all my data files uncorrupted from amongst the 9.04 installation and aren't sure where they are stored.  

Install Option:
Use Manual Partioning Method 
SCSI1 (0,0,0) (sda) - 250.1 GB ATA Samsung HM250JI
         #1 primary 244.3 GB B      ext3
         #5 logical       5.8 GB     F  swap      swap
I think in the suggestion to everdhil is to delete #1.  Will my data be deleted too?

There is also the Rescue Option:
Of sda1, sda2 or sda5 I guess I should choose to reinstall GRUB boot loader to "/dev/sda1"
Will I loose data in this option?

Any help would be greatly appreciated.

---

