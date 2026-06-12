---
title: "probably been instructed before...(some install Q's)"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by magnethead on 2007-11-25
but I installed ubuntu on my 40 GB drive, with the other disconnected (so CD and 40GB were only system drives recognized), did a manual install with an 18.63 GB boot partition, a 4.67 GB swap file, and a 13.97 GB share partition.

XP boots as it should as default (no bootloader as I scrapped XP pro for typical windows reason so i only have home, hence no need for selection screen), and if i do a F12 boot override I can get to grub as normal. 

How can I configure GRUB to display for 10 seconds, have the 3 standard options (ubuntu, ubuntu recover, ubuntu memtest) plus a fourth option for XP? So that I can chnage my BIOS boot drive to the 40 GB drive primary and SATA drive boot secondary, so when it powers up it goes to the 40 first and displays GRUB, and i can use GRUB to go to windows if i so desire?

Here's my complicated drive layout:

multi(0)disk(0)rdisk(0)partition(1-3) is SATA port 1 (channel 1), 320 GB HDD

Disk multi(0)disk(0)rdisk(0)partition(1): 180 GB NTFS Win XP Home
Disk multi(0)disk(0)rdisk(0)partition(2): 30 GB NTFS storage
Disk multi(0)disk(0)rdisk(0)partition(3): 88 GB NTFS storage


multi(1)disk(0)rdisk(0)partition(1) is channel 4, IDE port master, 320 GB HDD

Disk multi(1)disk(0)rdisk(0)partition(1): 320 GB NTFS storage


multi(1)disk(0)rdisk(1)partition(1) is channel 4, IDE port slave, 40 GB HDD

Disk multi(1)disk(0)rdisk(1)partition(1): 18.63 GB Ubuntu boot EXT3
Disk multi(1)disk(0)rdisk(1)partition(1): 4.67 GB Ubuntu swap
Disk multi(1)disk(0)rdisk(1)partition(1): 13.9 GB Share FAT32


boot.ini:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by magnethead on 2007-11-25
title Windows NT/2000/XP (loader)
root (hd2,1)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 


Is that what i need to do, or something like it (after checking devices.map and changing the variables)?

---

