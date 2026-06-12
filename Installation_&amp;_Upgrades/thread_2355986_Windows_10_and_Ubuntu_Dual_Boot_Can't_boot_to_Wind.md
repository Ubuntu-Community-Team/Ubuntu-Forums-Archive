---
title: "Windows 10 and Ubuntu Dual Boot: Can't boot to Windows"
date: 2017-03-18
forum: Installation &amp; Upgrades
---

### Post by zimo133 on 2017-03-18
Hi All,

So a couple of weeks ago I attempted to dual boot my desktop with Ubuntu 14.04, when Windows 10 was already installed, however ever since then no matter how hard I tried I couldn't boot it to my Windows Partition. I also couldn't use any networking on the old 14.04 version so just recently I upgraded it to 16.10 Ubuntu. The output of fdisk is seen below which makes me think that I didn't destroy all of my windows data, but no matter How many solutions I try online I can't figure it out. 


```
Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x15ef9b1a

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048 247572479 247570432 118.1G  7 HPFS/NTFS/exFAT
/dev/sdb2       247572480 248494079    921600   450M 27 Hidden NTFS WinRE
/dev/sdb4       248496126 461944831 213448706 101.8G  5 Extended
/dev/sdb5       248496128 461944831 213448704 101.8G 83 Linux
```

I am still pretty new to Linux so I took my computer to a guy that fixes Linux computers and he told me that I was missing my Windows Bootloader. Any help would be greatly appreciated.

---

