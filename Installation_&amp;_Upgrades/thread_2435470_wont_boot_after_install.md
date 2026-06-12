---
title: "wont boot after install"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by yaniv862 on 2020-01-21
im trying to install lubuntu on an old laptop
i set the partitions
/
swap
/home
and after install the bios not detecting the OS
its not UEFI because it does not support it i set the drive to mbr
what am i doing wrong?

i also tried the boot-repair it keeps showing me that its not a live usb
and i cant try it from ubuntu because the system gets stuck on this os

---

### Post by guiverc on 2020-01-21
Some more details may help.

What release of Lubuntu?
Did you verify the ISO & write to install media?
([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck))
What architecture? or some machine specs please

I'll provide the manual - [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)

I'm not sure what you meant by "BIOS" not detecting the OS if it's not UEFI. I did four installs today on various non-UEFI boxes and I very much doubt the BIOS on any of the boxes would know what OS (Lubuntu 18.04.4 & 20.04) I installed. 

 BIOS by default boots a specific drive (BIOS does control which drive) & runs the first 512 bytes (called MBR or master boot record) which boots the system, ie. it doesn't know what OS is on the disk itself. BIOS only controls which disk in the machine (if multiple drives), loading and executing that first 512 bytes of code.

---

### Post by yaniv862 on 2020-01-21
> **guiverc said:**
> Some more details may help.

What release of Lubuntu?
Did you verify the ISO & write to install media?
([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck))
What architecture? or some machine specs please

I'll provide the manual - [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)

I'm not sure what you meant by "BIOS" not detecting the OS if it's not UEFI. I did four installs today on various non-UEFI boxes and I very much doubt the BIOS on any of the boxes would know what OS (Lubuntu 18.04.4 & 20.04) I installed. 

BIOS by default boots a specific drive (BIOS does control which drive) & runs the first 512 bytes (called MBR or master boot record) which boots the system, ie. it doesn't know what OS is on the disk itself. BIOS only controls which disk in the machine (if multiple drives), loading and executing that first 512 bytes of code.

i installed the 19.10 64bit one
and what i mean about the bios that it does not detect any bootable and boots directly to the boot menu of the laptop after it does not detect bootable drive and even after selecting the drive manually
and the verification im trying it now but i dont think its the problem because it did not show any problems during the installation
edit: no errors found in the check

---

### Post by Bashing-om on 2020-01-21
yaniv862: Hello -

Show us what we are working with:

Boot from the liveUSB in "try ubuntu" mode and post back the result of terminal command:
```

sudo fdisk -lu

```
so we see how the drive is identified and partitioned.

Then we consider properly installing the boot loader, grub, to the drive's boot sector.

[INDENT]all in the process
[/INDENT]

---

### Post by yaniv862 on 2020-01-22
> **Bashing-om said:**
> yaniv862: Hello -

Show us what we are working with:

Boot from the liveUSB in "try ubuntu" mode and post back the result of terminal command:
```

sudo fdisk -lu

```
so we see how the drive is identified and partitioned.

Then we consider properly installing the boot loader, grub, to the drive's boot sector.
[INDENT]all in the process
[/INDENT]

ok i got boot-repair to work but still no diffrenrce
and here is the the result of the command
Disk /dev/loop0: 1.47 GiB, 1568382976 bytes, 3063248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Hitachi HTS54505
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x78d1c0c4


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048 209717247 209715200   100G 83 Linux
/dev/sda2       209717248 210765823   1048576   512M 82 Linux swap / Solaris
/dev/sda3       210765824 976768064 766002241 365.3G 83 Linux








Disk /dev/sdb: 3.75 GiB, 4008706048 bytes, 7829504 sectors
Disk model: STORE N GO      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0524f6f1


Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 7829503 7827456  3.8G  c W95 FAT32 (LBA)




Disk /dev/zram0: 461.61 MiB, 484020224 bytes, 118169 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/zram1: 461.61 MiB, 484020224 bytes, 118169 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

---

### Post by yancek on 2020-01-22
You need to be more specific about what 'old' is.  Post some details on the hardware such as processor, RAM, etc.

You indicate that you have used boot repair but you haven't posted a link to the output you get from boot repair which would give a lot of details on your system so do that.

If it boots to the boot menu on the laptop and since you have given no information on any other OS being installed, then we would expect it to boot Lubuntu.  Do you have another OS on the laptop and if so, what?  Did you install Lubuntu on another drive?

---

### Post by yaniv862 on 2020-01-22
> **yancek said:**
> You need to be more specific about what 'old' is.  Post some details on the hardware such as processor, RAM, etc.

You indicate that you have used boot repair but you haven't posted a link to the output you get from boot repair which would give a lot of details on your system so do that.

If it boots to the boot menu on the laptop and since you have given no information on any other OS being installed, then we would expect it to boot Lubuntu.  Do you have another OS on the laptop and if so, what?  Did you install Lubuntu on another drive?

ok its toshiba sattelite c660 with pentium p6100 and 2gb of ram

i installed lubuntu 19

i dont have any other os i want it to be the primary

here is the output of the boot repair: [https://paste.ubuntu.com/p/ctcVzPr4b6/](https://paste.ubuntu.com/p/ctcVzPr4b6/)

and somehow after boot-repair while trying with lubuntu 18 version it worked if it means anything to you
i still want to install the 19 one but good to know that this is the scond option

---

### Post by yaniv862 on 2020-01-23
well in conclusion im just gonna use the lubuntu 18 but thanks for the help

---

