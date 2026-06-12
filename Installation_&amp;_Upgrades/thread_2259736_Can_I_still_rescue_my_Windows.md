---
title: "Can I still rescue my Windows?"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by hektor2 on 2015-01-06
Hi guys,
I'm new around here and a linux noob (not planning to stay a noob for a long time though).

But right now I need your help. I had the idea to get my hands on linux a bit but was not ready to give up windows entirely. So after doing some research online I decided to run a version of linux from a USB flash drive (Puppy) but I couldn't get it to work so I tried another version, lubuntu this time. While I managed to get lubuntu to the USB flash drive now I think my grub2 is screwed. I'm trying for a while to find a solution, have seen a similar thread here too but it is not exactly the same so the solution of that thread doesn't work for me. 

My situation now is as follows: I have a Laptop (pretty old, Compaq from 2010) with four partitions hard drive. On the first one is (was?!) Windows 7 installed the other partitions contained file (mostly e-books and software).  I downloaded a .iso file of lubuntu 11.04, put it to a USB flash drive with unetbootin and rebooted. It didn't work the first time so I tried Universal USB Installer I guess it workd somehow but after rebooting there was no option to boot either Windows 8 or Lubuntu, the Laptop just booted into Lubuntu. There were some options on the screen like: try lubuntu, install lubuntu, boot from first hard drive, advanced... I chose the first option, try lubuntu it booted and works nicely (I'm writing this from lubuntu) but after some time I rebooted to see if I can boot into windows, with no luck. I chose the option boot from first hard drive but still it didn't work. I tried removing the USB flash drive from the computer that didn't work either, just a blinking, white underscore in the top left corner of the screen. I suppose somehow the grub(2) got messed up but even after looking all over the internet I couldn't figure a way to resolve this.

Any answer appreciated. Thnx in advance. :KS

---

### Post by LostFarmer on 2015-01-06
First lets see how your hdd partitions look like.  from lubuntu's menu-Accesories-click on "LXTerminal" - type in below command and press enter and post its output.
```
sudo fdisk -l
``` (l is a small L, not a 1)

---

### Post by hektor2 on 2015-01-06
> **LostFarmer said:**
> First lets see how your hdd partitions look like.  from lubuntu's menu-Accesories-click on "LXTerminal" - type in below command and press enter and post its output.
```
sudo fdisk -l
``` (l is a small L, not a 1)


Thnx for the answer.

```
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 628.3 MiB, 658841600 bytes, 1286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop1: 2.4 GiB, 2555379712 bytes, 4990976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x31d2810f

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 241647935 241441088 115.1G  7 HPFS/NTFS/exFAT
/dev/sda3       241651712 283596799  41945088    20G  f W95 Ext'd (LBA)
/dev/sda4       283596800 488392703 204795904  97.7G  7 HPFS/NTFS/exFAT
/dev/sda5       241653760 275208191  33554432    16G  7 HPFS/NTFS/exFAT
/dev/sda6       275210240 283596799   8386560     4G 83 Linux

Partition table entries are not in disk order.
Disk /dev/sdb: 7.2 GiB, 7754219520 bytes, 15144960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0004af3d

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15144959 15142912  7.2G  c W95 FAT32 (LBA)

Disk /dev/zram0: 872.3 MiB, 914616320 bytes, 223295 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
lubuntu@lubuntu:~$  
```

---

### Post by yancek on 2015-01-06
The Grub bootloader installation didn't work for some reason.  You still have 4 windows partition and one small Linux partition at the end of the drive.  Probably the best place to start is to get more information to post on boot files which you can do using the boot repair utility.  Take a look at the site below and you can download and burn it to a CD.  You will need to select the option to Create Bootinfo summary and use the Ubuntu installation media.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hektor2 on 2015-01-06
> **yancek said:**
> The Grub bootloader installation didn't work for some reason.  You still have 4 windows partition and one small Linux partition at the end of the drive.  Probably the best place to start is to get more information to post on boot files which you can do using the boot repair utility.  Take a look at the site below and you can download and burn it to a CD.  You will need to select the option to Create Bootinfo summary and use the Ubuntu installation media.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Unfortunately that didn't resolve my issue. This is the link it printed out. 
[http://paste.ubuntu.com/9684901/](http://paste.ubuntu.com/9684901/) 

Thank You for the reply.

---

### Post by yancek on 2015-01-06
Your output shows a Linux partition on sda6 but no boot files.  On sda4, a windows partition, you show some wubi files.  Wubi is not supported any longer.  You don't have any Grub files anywhere on the disk per the summary.  You have syslinux bootloader installed to the master boot record of both hard drives rather than the standard Grub bootloader.

---

### Post by oldfred on 2015-01-07
You so not show grub in MBR, wubi boots using the Windows boot loader and will just show grub as it is standard Ubuntu boot loader, but it is not part of the Windows boot and choice between Windows & Ubuntu.

Wubi was last supported with 12.04. And you need to be using the current versions of Ubuntu or Lubuntu. 

If you cannot boot Windows that is most likely Windows issues. Boot-Repair only does very minor repairs to Windows, you need your Windows installer or a Windows repairCD or flash drive. If Windows starts to boot, you may be able to use f8 to get into the internal repair console.

 [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by mastablasta on 2015-01-07
did you actually install Linux or are you just trying it form the try it option? if you are just trying it there shouldn't be anything written on hard disk.

---

