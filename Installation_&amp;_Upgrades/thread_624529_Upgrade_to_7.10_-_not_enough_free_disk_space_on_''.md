---
title: "Upgrade to 7.10 - not enough free disk space on '/'"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by antiemptyv on 2007-11-27
OK, so I finally want to upgrade to Gutsy.  I ran into a slight problem when doing so via Update Manager.  The situation seems similar to some experienced by other folks out there, but it's different than I have seen.  It tells me I do not have enough free space on disk '/'.  I have read other threads about there not being enough space on '/root' but not on '/'.  I have attached a picture of the error message it gives me.

So I thought, I have an 80GB hdd, I couldn't have used it all up already!  Sure enough Disk Usage Analyzer tells me I have only used 16GB and have 61.4GB free.  I have attached an image of this, too.

I have a fairly normal partition setup.  "fdisk -l" gives:
```
BLKGETSIZE ioctl failed on /
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2            9355        9729     3012187+   5  Extended
/dev/sda3             609        9354    70252245   83  Linux
/dev/sda5            9355        9729     3012156   82  Linux swap / Solaris

Partition table entries are not in disk order
```


"dh" outputs:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              4806904   3403312   1159408  75% /
varrun                  517888        96    517792   1% /var/run
varlock                 517888         0    517888   0% /var/lock
procbususb              517888        88    517800   1% /proc/bus/usb
udev                    517888        88    517800   1% /dev
devshm                  517888         0    517888   0% /dev/shm
lrm                     517888     33788    484100   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda3             69149916   6198348  59438956  10% /home
/dev/hda               7248598   7248598         0 100% /media/FRIENDS_SEASON_5_DISC4
```

Am I missing something?

---

### Post by forestpixie on 2007-11-27
you've got plenty of room on /home but not on / - how big is the sda1 partition

Edit - and / is root afaik

---

### Post by antiemptyv on 2007-11-27
oh yeah duh.  so i guess the first line on the output od "df" tells that.  that line is: 

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              4806904   3403312   1159408  75% /

so i guess there isn't enough room.  dangit.  so i need to resize the root partition?

---

### Post by forestpixie on 2007-11-27
no - try making sure there's nothing in trash - and in root's trash - there's prob a cli way but I ```
gksudo nautilus
``` and check trash there for root

also do ```
sudo apt-get clean
``` to clear the apt cache and try again

---

### Post by antiemptyv on 2007-11-27
yep.  did those.  so i gues this is in fact the same exact problem.

i'd rather not do any partition resizing.  i've heard horror stories.

---

### Post by forestpixie on 2007-11-27
well I don't know of any other files/directories you could clean or delete having not been here long enough - although if you've got a lot of old kernels you could lose those

as far as resizing partitions go though I've not had any problems personally 

the alternative would be to reinstall rather than upgrade

---

