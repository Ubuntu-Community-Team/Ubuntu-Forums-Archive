---
title: "Help, i think ubuntu removed my windows installation"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by Morphyxx on 2012-05-13
I just installed Ubuntu with the option 'install alongside windows'
I had a windows 7 installation on my ssd hard drive. 
Now it seems that ubuntu formated the ssd to ext4 format and removed the win 7 installation.

Is there any way to get back my win 7 files?:confused:

---

### Post by wilee-nilee on 2012-05-13
Don't use the SSD as of now is the first thing use a live cd and check with gparted if this is the case, or you just need grub set to see the windows partitions.

Let us know if you are really sure.

---

### Post by darkod on 2012-05-13
Did you create unallocated space in advance, or you used the slider ti split the SSD between windows and ubuntu?

As wilee said, do not try to boot from the ssd any more. Boot with the ubuntu cd/usb in live mode, and check the partitions on the disk in terminal with:
sudo fdisk -l (small L)
sudo parted /dev/sda print all

Post the results if you need help understanding them.

---

### Post by Morphyxx on 2012-05-13
I only clicked the option to install alongside windows and it started right away to install without any confirmation or warnings.

Gparted says that the ssd is now in 3 partions:
one with fat32 on ~100MB with boot flag
one with ext4 on ~52GB
one with linux-swap on ~8GB

can add that the SSD is 64 GB and before the ubuntu installation windows used up about 50GB

---

### Post by darkod on 2012-05-13
Looks bad, there is no ntfs partition on it.

I don't use the auto methods much, so I don't remember the options with all details, but if you use install along windows there has to be a slider or something to select how much of the ssd to leave for windows, and how much to take for ubuntu. Unless you had unallocated space prepared in advance, as I mentioned.

Now, if you are lucky that 52GB partition is only reported as ext4 but in fact it's the windows partition. Download testdisk from live mode and do the deep scan to check what partitions can be discovered and possibly recovered. In the fist step, only do the deep scan, don't try anything else.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by YannBuntu on 2012-05-14
Darkod +1
Also don't forget wilee-nilee's recommendation: don't start your installed Ubuntu any more, and don't write on your disk.
So use TestDisk from a live-CD, not from your installed Ubuntu. It's even better if you make a bit-to-bit copy of your disk before using TestDisk.

Also, from a live-CD, could you browse your installed Ubuntu partition, and attach to your answer a copy of the 2 following files that are in your installed Ubuntu partition :
/var/log/installer/syslog
and
/var/log/installer/partman
(this will help us understand why your Windows has been erased)

---

