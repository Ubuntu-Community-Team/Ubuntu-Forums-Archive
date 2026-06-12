---
title: "Stuck at Black Screen with Cursor after Installing Ubuntu"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by MadDogTen on 2012-10-07
Hello, and thanks for any help given!

I am trying to install Ubuntu 12.04.1 64 Bit (Had Windows, But used Gparted to delete the partition), however, after the installation completes and I reboot, It stops at a Black Screen with a Cursor (Can't actually do anything myself) and does nothing.

I'v tried reinstalling it again, and come up with the same results.

After looking around a bit, I think its the fact that boot files are to far from the start of the disk, but am unsure if it is, or how to fix it.

My Spec's are-
```
 
Processor:	Intel Core i5-3570K
Motherboard:	ASRock Z77 Pro3
Cooling:	Cooler Master Hyper 212 Plus CPU Cooler
Memory:	Kingston 4GB x 2 - DDR3 1333 CL9
Video Card:	EVGA SuperClocked 01G-P3-1461-KR GeForce GTX 560 (Fermi) 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP
Hard Disk:	Samsung SSD 830 128 GB - Seagate Barracuda 320GB 7200 RPM Hard Drive
CRT/LCD Model:	ASUS VH192D Black 18.5" 5ms Widescreen LCD Monitor 1366 x 768
PSU:	hec X-Power Pro 650 650W Continuous
Software:	Windows 7 64x
```
I use the SDD as my Main Boot Partition, and the Other Drive is Storage.


Here is my "sudo fdisk -l" log-
```

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a499a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   233508863   116753408   83  Linux
/dev/sda2       233510910   250068991     8279041    5  Extended
/dev/sda5       233510912   250068991     8279040   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   499316264   249657108+   7  HPFS/NTFS/exFAT
/dev/sdb2       499316265   625137344    62910540    f  W95 Ext'd (LBA)
/dev/sdb5       499316328   625137344    62910508+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 7801 MB, 7801405440 bytes
5 heads, 32 sectors/track, 95232 cylinders, total 15237120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    15237119     7614528    c  W95 FAT32 (LBA)

```


I'm currently running Ubuntu off of the USB Drive I used to install it.
If you need any more info, Just ask, and Thanks agian for any help given. :)

---

### Post by jerrrys on 2012-10-07
Can you get to console?  **Ctrl **+ **Alt **+ **F1**

If so then enter  **startx**

---

### Post by MadDogTen on 2012-10-07
> **jerrrys said:**
> Can you get to console?  **Ctrl **+ **Alt **+ **F1**

If so then enter  **startx**
Its come up with an Error, and says Server is already active for Display 0.

---

### Post by Wim Sturkenboom on 2012-10-07
Maybe you can post the content of /var/log/Xorg.0.log. Please use code tags

[noparse]```

paste content of logfile here

```
[/noparse]

---

### Post by jerrrys on 2012-10-07
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/935789](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/935789)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GTX+560&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GTX+560&as_qdr=all&sa=Google+Search&lang=en)

---

