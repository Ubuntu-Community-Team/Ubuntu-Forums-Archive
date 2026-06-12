---
title: "feisty will not install...help!"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by ZephyrQ on 2007-07-14
I have had several problems trying to install Feisty on my 4 year old system.  I've tried the alt install CD and it keeps freezing at one point or another...usually during partitioning.   I've tried installing CentOS (not my favorite, but I've got to get a working system ASAP) but it doesn't recognize the ReiserFS partitions I have (and have to keep).  I have 4 partitions that cannot be formatted (to keep the data), so wiping the big drive (hda-60G) is not an option.

I have also been getting 'atkbd.c' errors, which, when I looked them up, seem to be kernel errors. 

Here is my hardware config:
1.3 gig cpu (AMD Duron) with 3 drives: hda, hdb, hdd
I've unplugged all peripherals save the mouse and keyboard (which are usb ports) and the printer
512M memory, same for video memory 
drive config:
   hda: hda1--65M (old boot, I'm just ignoring this partition)
           hda2--3.7G (new boot)
           hda5--5.8G (/)
           hda6--9.7G (/usr)
           hda7--5.5G (/tmp)
           hda8--3.3G (/var)
           hda9-hda11 are drives that cannot be formatted (including hda11 which is a 20G ReiserFS)
   hdb: hdb1--7.4G backup partition with is also ReiserFS
           hdb5--swap (only 435M)
   hdd: hdd1--30G--this is a drive that, when I tried to repartition with GParted, crashed the system and is why I am trying to install Feisty.  I've tried to install with and without this drive (having the install not mount it).

I would really appreciate the help.  Thank you.

---

### Post by davidjmayo on 2007-07-14
AFAIK (i may be wrong) but the install CD uses GParted  which does not resize ReiserFS partitions. I think this is your problem

---

### Post by ZephyrQ on 2007-07-14
How do I fix it?  I can't seem to copy the info from the partitions (this is info I have to keep).  Is there a work around?  If I could copy (dd?) to another partition, then I could reformat the ReiserFS stuff.  As it is now, there is no OS on the computer (I abandoned Windows back at 3.1) and I couldn't figure out how to use the live CD to copy information already on the system.

---

### Post by ZephyrQ on 2007-07-17
I am just posting this for others if this happens to them.

I finally did a net install of Debian Edge (latest stable) which allowed me to 'turn off' the drive that seems to be affecting my system.  I tried doing this with Feisty installs (several tries of both desktop and alt-install), but while  there were options to not mount the drive, the install would still freeze up, mostly around the partitioning part.

Did I miss this option with the Feisty install?

Now I have a stable Debian system, and while I will be using Ubuntu (specifically Edubuntu) on some school laptops (they are letting me try an experiment...), Feisty seems to not like my desktop--pity, I had been using it since before Dapper.

I hope this helps.

---

