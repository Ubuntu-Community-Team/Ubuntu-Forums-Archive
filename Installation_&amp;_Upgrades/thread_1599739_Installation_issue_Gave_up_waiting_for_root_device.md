---
title: "Installation issue: Gave up waiting for root device"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Budgreg on 2010-10-18
[SIZE=2]Hi there,

this is my first setup of ubuntu. And I´m quite familar to Linux allthoug it´s been a while since my last setup. Anyway, my system is brand new and consist of the following parts:

AMD Athlon X2 240e on MSI [/SIZE][SIZE=2]880GMA-E45 (SB850)
4GB RAM (DDR3)
All drives connected by SATA using onboard SB850 ordered by:
1 LG BluRay optical drive
2 WD Caviar Green WD10EARS 1TB
3 [/SIZE][SIZE=2]WD Caviar Green WD20EARS 2TB
[/SIZE][SIZE=2]4 [/SIZE][SIZE=2]WD Caviar Green WD20EARS 2TB
[/SIZE][SIZE=2]5 [/SIZE][SIZE=2]WD Caviar Green WD20EARS 2TB
[/SIZE][SIZE=2]6 [/SIZE][SIZE=2]WD Caviar Green WD15EARS 1,5TB

I set the SATA controller to AHCI because I want to set up a software raid (level 5) on the three 2TB-disks. The first disk (1TB) should be the ubuntu boot disk (no raid). The last one (1,5TB) is currently not connected - it will be added later.

First I struggled booting the ubuntu server 10.10-CD (x64) from the bluray drive - after succesfull starting the setup procedure it told me that it cannot access the drive. It seems that drivers are missing. No problem - I connected an usb dvd drive to the system and gave it a try.

The boot order was set to usb-dvd, then bluray, then the first harddisk (1TB). Setup seems to run fine using the usb dvd drive. I´ve chosen the first disk (shown as /dev/sda) for the installation. It was automatically configured as one big root-partition and a small swap-partition. Grub was installed on the MBR of the first disk. But after restart GRUB tells me "Gave up waiting for root device" and "ALERT! /dev/disk/by-uuid/whatever  does not exist. Dropping to a shell!". Obviously the boot loader cannot find (or access) the volume containing the kernel.

I made some research and found some other people complaining about some mixup of hdaX and sdaX devices on SATA devices - but these statements where from 2007. Another point is that the USB optical drive is my boot device while the installation runs, but not afterwards - does this matter? I also tried installing Ubuntu server 10.04, but is behaves the same.

Please keep in mind that the goal is to have ubunto server 64bit running on this system - that´s it. No dual boot is needed. And there is no data on any disk that should be taken care. It´s a very new system.

Where should I start to fix this issue? What´s wrong with the current linux boot loader using SATA disks connected to SB850 SATA controller?

Thanks in advance for your support.

br, Gregor.

[/SIZE]

---

### Post by Budgreg on 2010-10-19
Hi there,

this is an update to my case. In the meantime I made some more installation - without success.

This includes manual parititioning of /dev/sda using smaller partitions (100GB for root, 20GB fpr swap) and other filesystems (ext3 instead of ext4). I also booted 10.4 Desktop using the live CD  and gained access to /dev/sda1 successfull, but booting from this partition ist not possible.

Another issue: I´ve found out that each WD Caviar Green harddisk uses the new advanced format (4k sectors) - even the 1GB disk I am using as boot device. So today I will replace this disk with anotherone not using advanced format (WD Caviar Blue 640GB).

Are there any other ideas?

br, Gregor.

---

### Post by coffeecat on 2010-10-19
Even if you change the boot disc for one not using the advanced format, you'll still need to deal with accessing the other advanced format drives. I've seen this link posted in other threads. It has some useful information:

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

### Post by Budgreg on 2010-10-19
> **coffeecat said:**
> Even if you change the boot disc for one not using the advanced format, you'll still need to deal with accessing the other advanced format drives.[]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html")

This is true, but when booting the live CD access to this filesystem was basically possible without problems. I later have to deal with the allignment of the partitions in this disk to gain full performance (but I do not understand how to make this allignment bevore installing the OS).

Anyway till now I thought that advanced format is an issue about performance - maybee it´s also an issue for bootloaders.....

br, Gregor.

---

