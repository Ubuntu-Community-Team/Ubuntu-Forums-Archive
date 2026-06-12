---
title: "Cannot create Ext3 Filesystem"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Totalchaos02 on 2008-04-13
I have been using Ubuntu on my laptop and love it but I have had some trouble getting it on my desktop computer. After booting the live CD I got an error at 5% through the installation. All it said was that the Ext3 filesystem could not be created and then it would quit the install process. I tried setting up the partitions manually but it would just lock up when attempting to make changes.

I have tried with 4 different versions (6.10 32 bit, 7.04 64 bit, 7.10 64 bit, 8.04 64 bit) and have no luck with any of them. All four of those versions have made successful installs before. I have tried from installing to this hard drive from multiple computers and also as an external drive. I have pretty much come to the conclusion that this is a problem with the hard drive itself (I have had issues getting Vista on it in the past but eventually got it to work). It is pretty dated at this point and could use a new one anyway but before I went out spent any money I was curious if anyone else has run into this issue and knows if there is another option. Thank you in advanced for any help.

Also one quick note, I tried using the Wubi installer just to get Ubuntu on my system in any form (so tired of Vista's constant problems) and got the same error at 5%. Not sure if that helps diagnose the issue but thought I would mention it.

---

### Post by tamoneya on 2008-04-13
why dont you do some tests on it.
```
hdparm -t /dev/sda
``` That will test to see how quickly you can read from the drive.  This is assuming that is it /dev/sda.  Also try to make a partition on it without the ubuntu installer.  Use fdisk or gparted and see what happens.

---

### Post by Totalchaos02 on 2008-04-13
> **tamoneya said:**
> why dont you do some tests on it.
```
hdparm -t /dev/sda
``` That will test to see how quickly you can read from the drive.  This is assuming that is it /dev/sda.  Also try to make a partition on it without the ubuntu installer.  Use fdisk or gparted and see what happens.

I cannot do the hdparm test right (the Ubuntu discs were borrowed) but I can tell that I have used the built in Vista partitioner to resize my Vista partition. Ill try doing the test as soon as I can. Thank you for the suggestions.

---

