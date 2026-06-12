---
title: "Problem new install with RAID 5"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by Erwann on 2006-07-29
Hi,

I have a problem with a server Ubuntu using 3 SATA drives in RAID 5.

I had to install again Ubuntu yesterday because of a crash system. My previous Ubuntu distrib was installed on RAID protocol (only /boot was on an IDE drive).

The install software didn't recognize RAID 5 but only 3 SATA drives (sda, sdb and sdc). So, I choice to install Ubuntu on an IDE drive (not only /boot like the first time).

**Today, I don't manage to mount RAID system and read my data files.**

Drives shared with RAID are :
[i]/dev/sda
/dev/sdb
/dev/sdc[/i]

I have created succefully RAID array with the following instruction :
```
mdadm --create --verbose --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc
```
It seems to be operational, on the device /dev/md0

The RAID array had several partitions. I thinks it used EVMS protocol (defaults options of the install software)
How read /dev/md0 to get theses several partitions ?
I tried to use evmsn and "mount /dev/md0 /my_drive" but nothing...

Can you help me ?? Files on the RAID are very importants for me...

Thanks in advance,

---

### Post by fabiand on 2006-07-30
Hey,

please provide the output of ```
sudo fdisk -L /dev/md0
```.

---

