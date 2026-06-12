---
title: "Install instead of boot from CD?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by Enigmaman on 2008-01-24
At the moment I am booting Ubuntu from CD - how can I get to physically install it on the hard disk without losing Windows?:confused:

---

### Post by djgrandmarquis on 2008-01-24
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

This is a nice walk-through for installing from the CD. If you're unsure about anything (e.g. disk partitioning), I would recommend searching these forums or searching with Google.

---

### Post by wolfen69 on 2008-01-24
here [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) is a tutorial for dual booting ubuntu and windows.

---

### Post by browndruid on 2008-01-24
Just as a warning, when I tried this the first time, it killed Windows. It just wouldn't work at all. And then Ubuntu did the same. So I highly recommend backing up your system before you do this.

And, just as a disclaimer, I'm not blaming Ubuntu. Something just didn't work on my system. I now run ONLY Gutsy. Windows is GONE.

---

### Post by CadetD on 2008-01-24
> **browndruid said:**
> Just as a warning, when I tried this the first time, it killed Windows. It just wouldn't work at all. And then Ubuntu did the same. So I highly recommend backing up your system before you do this.

And, just as a disclaimer, I'm not blaming Ubuntu. Something just didn't work on my system. I now run ONLY Gutsy. Windows is GONE.

Is Windows REALLY gone? Or are you not seeing it in the boot menu? 
It could be that the Windows partition is still there and you can mount it and access the data. Heck, you could also add it back to the boot loader. 

Try the following: 
```
fdisk -l
```
 
This will list the partitions on your machine. If the Windows partition is still there, then you can mount it.

---

### Post by Enigmaman on 2008-01-25
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

That's the output :confused:

---

### Post by djgrandmarquis on 2008-01-25
I believe that CadetD's comment was in response to browndruid's comment. In general, you will not need to run fdisk to install Ubuntu via the LiveCD.

---

