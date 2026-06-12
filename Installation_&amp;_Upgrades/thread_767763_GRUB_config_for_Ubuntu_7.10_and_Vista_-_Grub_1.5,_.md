---
title: "GRUB config for Ubuntu 7.10 and Vista - Grub 1.5, Error 21"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by kjcearns on 2008-04-25
I have done some searching on this topic, but have not come across anything that helps me get GRUB working on my system.

I am running a P35 Gigabyte motherboard, where 3 drives are set up in a RAID5 configuration using the Intel RAID SATA controller.  A single hard drive on the Gigabyte SATA controller holds Vista and Ubuntu 7.10.  Problem is I can't get GRUB to recognize my hard drive.  Attached below is the  fdisk -l output.  

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde4b3220

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976765952    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde4b3220

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121602   976765952    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7451bc34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       49621   398579102    7  HPFS/NTFS
/dev/sdd2           49622       50837     9767520   83  Linux
/dev/sdd3           50838       51323     3903795   82  Linux swap / Solaris
/dev/sdd4           51324       60801    76132035    b  W95 FAT32

I tried to manually configure the grub in the terminal window when booting with the Live CD, but get the the same error (21).  I thought maybe the RAID is confusing the drive numbering (since the 3 drives appear as only one drive in Vista), so I also tried root (hd1,1) with the same error (actually, I tried all possible configurations between (hd0,1) and (hd3,1).  Same lack of results...

grub> root (hd3,1)

Error 21: Selected disk does not exist

grub> root (hd1,1)

Error 21: Selected disk does not exist

grub> 

Any suggestions?  Thanks in advance.

---

### Post by Teefs on 2008-04-26
I am having a similar problem. I have have a raid 10 using intel's ich9r and another single drive. I installed Hardy on the single drive fine, but when i rebooted grub gave me the same error.

---

### Post by MaddMatt on 2008-04-26
I also just had the same problem with my new Hardy installation, and found it an easy fix - the Grub installer seemed to have just misread the BIOS disk order... It was trying to boot hd1,3 instead of hd0,3.. so an easy fix for me, just booted the live cd and edited the menu.list It also didn't detect the second ubuntu installation I have on hd0,1, so it might be a bug with Grub on muliple discs? or maybe sda and hda combinations... not sure, but keep playing with the menu.list and i"m sure you'll get a config that works... The error is indicitave of pointing to the wrong partition, not that there's actually an error. Good luck!

---

### Post by Teefs on 2008-04-26
Hey Thanks! After the error appeared I selected the first option and edited it by pressing 'e' I changed the"root hd(4,2)" to "root hd(0,2)" and everything started working!

EDIT: Actually this doesn't work 100% Those changes to the boot menu are only temporary. They change back when I reboot. Does anyone know how to make the changes permanent?

---

### Post by tosoth on 2008-04-26
> **Teefs said:**
> Hey Thanks! After the error appeared I selected the first option and edited it by pressing 'e' I changed the"root hd(4,2)" to "root hd(0,2)" and everything started working!

EDIT: Actually this doesn't work 100% Those changes to the boot menu are only temporary. They change back when I reboot. Does anyone know how to make the changes permanent?

You have to edit file /boot/grub/menu.lst

---

### Post by kjcearns on 2008-05-09
Thanks Everyone - gone for a week for work, got back and once I figured out how to mount my installed drive when using the LiveCD - I was in business.  VERY Happy Now !  On to discover the next problem...

---

