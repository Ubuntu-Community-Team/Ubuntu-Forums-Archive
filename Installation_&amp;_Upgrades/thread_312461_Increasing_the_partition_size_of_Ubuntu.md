---
title: "Increasing the partition size of Ubuntu"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2006-12-04
Hi,
I installed Ubuntu on my desktop a month or so ago and I have been very impressed by Ubuntu. When I initially installed Ubuntu, I used the in-built program to auto create a partition, and I believe it created a 40GB partition and reserved it for Ubuntu. I have two hard disks - one PATA 80GB disk (which has XP Home on it) and the other one is a SATA 160GB disk (this has 3 partitions - with Ubuntu installed on one of the partitions). The thing is - after being so impressed with Ubuntu, I would like to use more disk space (about 120GB from my SATA drive to run Ubuntu). The question is, how can I increase the space of my current partition without having to re-install Ubuntu. (I mean theoretically, I can format my current partition and do a new install of Ubuntu with the right disk size, however, I would not want to remove the stuff that I have already installed on Ubuntu).

All help is greatly appreciated.

Thanks,
DB

---

### Post by rsambuca on 2006-12-04
I would recommend using the gParted liveCD.  Works like a charm for me.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Herman on 2006-12-04
Hello dhavalbbhatt,
I use and recommend   [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") for that type of work. It's free and only around 30mB to download and it's really good. It's very simple to use, you won't need to worry about unmounting and using  the swapoff command, and it can resize a Linux partition from the beginning of the partition now as well as the end. Not very many disk partitioners can do that. 
GParted LiveCD is based on GnuParted, which is already in  Ubuntu (just type 'sudo parted'  and you'll see what I mean. (Press your 'h' key for a list of commands, 'q' key to quit) , so it is 100% compatible for use with Ubuntu and other Linux, (and Windows FAT32 and NTFS as well).  
No matter how good the disk partitioner you use is, you should still make a backup of at least your most important data before working with partitions.
Regards, Herman :D

---

### Post by dhavalbbhatt on 2006-12-04
Thanks - will try using GParted once I get to my PC.

---

