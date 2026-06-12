---
title: "Ubuntu 14.04 installation crashes with &quot;???&quot; message after selecting drive"
date: 2014-07-04
forum: Installation &amp; Upgrades
---

### Post by Brian_Schmitz on 2014-07-04
[SIZE=4]**The Gist:**

[SIZE=2]I have been trying to erase my disk and install Ubuntu 14.04 LTS on my laptop [SIZE=4][SIZE=2]as my sole operating system.[/SIZE][/SIZE] I can boot "Try Ubuntu" or "Install Ubuntu" from a USB stick. During the graphical install, after I select "Erase disk and install Ubuntu" as my installation type, I have a choice to select between one of two RAID0 drives on which to install Ubuntu. (One is 18.2GB and the other is 439GB, so I naturally pick the larger one.) Regardless of which drive I select, one of two bad things generally happens.

In the first case, I get an error message saying "???" as soon as I proceed to the next screen. In the second case, I successfully manage get past the next screen, get 75% of the way through installing updates and packages, and then the installer crashes.[/SIZE]

**Precisely what I did before reaching this state:**[SIZE=2]
[/SIZE]
[LIST=1]
[*][SIZE=2]Downloaded Ubuntu 14.04 LTS (Trusty Tahr) 64-bit  PC (AMD64) desktop image.
[/SIZE] 
[*][SIZE=2]Ran **md5sum** on the file and checked that it matched the hash on Ubuntu hashes. It matched correctly.
[/SIZE] 
[*][SIZE=2]Used [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") (on Windows) to format my USB drive (FAT32) and mount the image on my drive.
[/SIZE] 
[*][SIZE=2]Re-booted with the USB drive plugged in, entered the boot menu, and selected "Try Ubuntu." Ubuntu successfully loads.
[/SIZE] 
[*][SIZE=2]Clicked icon on desktop labeled "Install Ubuntu 14.04 LTS" to open Graphical Installation.
[/SIZE] 
[*][SIZE=2]Chose all recommended options up until the screen that says "Installation type", where I selected "Erase disk and install Ubuntu."
[/SIZE] 
[*][SIZE=2]I then had a choice between two drives on which to install Ubuntu: an 18.2GB drive labeled RAID0RST and a 439.2GB drive labeled RAID0SYS. I selected the larger drive.
[/SIZE] 
[*]**[SIZE=2]I reach a time zone screen, then an error message saying "???" appears. I can't click anything. My screen goes black and freezes.[/SIZE]** [SIZE=4][SIZE=2][SIZE=4][SIZE=2]I tried this installation approach a few  different ways, each time with the same result.[/SIZE][/SIZE][/SIZE][/SIZE] 
[*][SIZE=2]At this point, I wanted to  start over fresh, so I opened GParted, deleted all of my partitions, and rebooted as before. When I do this, I usually manage to get past the screen with the "???" message [SIZE=4][SIZE=2]successfully[/SIZE][/SIZE], although **the installation crashes 75% of the way through installing updates at the end**.
[/SIZE] 
[*][SIZE=2]Now I have two different partial Ubuntu installations on my boot menu, both of which I can open[SIZE=4].[SIZE=2] However, I don't trust either of them because[/SIZE][/SIZE] both show several obvious signs of an incomplete installation.[/SIZE] 
[/LIST]
 **Potentially relevant info ([SIZE=4][B]partitions, **[/SIZE]hardware, etc):[/B][SIZE=3]

Partitions info[/SIZE]

[SIZE=2]**Running **```
sudo fdisk -l
```[B] produces the following warnings:

[COLOR=#ff0000][/COLOR][/B]```
[COLOR=#ff0000][/COLOR][B][COLOR=#ff0000]
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb doesn't contain a valid partition table

WARNING:  GPT (GUID Partition Table) detected on  '/dev/mapper/isw_dbdbgfbgbe_RAID0SYS'! The util fdisk doesn't support  GPT. Use GNU Parted.

Disk /dev/mapper/isw_dbdbgfbgbe_RAID0SYS2 doesn't contain a valid partition table

WARNING:  GPT (GUID Partition Table) detected on  '/dev/mapper/isw_dbdbgfbgbe_RAID0SYS3'! The util fdisk doesn't support  GPT. Use GNU Parted.

Disk /dev/mapper/isw_dbdbgfbgbe_RAID0SYS3 doesn't contain a valid partition table

WARNING:  GPT (GUID Partition Table) detected on  '/dev/mapper/isw_dbdbgfbgbe_RAID0RST'! The util fdisk doesn't support  GPT. Use GNU Parted.[/COLOR][/B][COLOR=#ff0000][/COLOR]

```[COLOR=#ff0000][/COLOR][B]

and the following output:[/B]

```

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   964690431   482345215+  ee  GPT

Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x695f6563


Disk /dev/mapper/isw_dbdbgfbgbe_RAID0SYS: 493.9 GB, 493921501184 bytes
255 heads, 63 sectors/track, 60049 cylinders, total 964690432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dbdbgfbgbe_RAID0SYS1               1   964690431   482345215+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/isw_dbdbgfbgbe_RAID0SYS1: 537 MB, 537657344 bytes
255 heads, 63 sectors/track, 65 cylinders, total 1050112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

                                Device Boot      Start         End      Blocks   Id  System

Disk /dev/mapper/isw_dbdbgfbgbe_RAID0SYS2: 484.9 GB, 484913971200 bytes
255 heads, 63 sectors/track, 58954 cylinders, total 947097600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/isw_dbdbgfbgbe_RAID0SYS3: 8469 MB, 8469348352 bytes
255 heads, 63 sectors/track, 1029 cylinders, total 16541696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0xc62b49f5


Disk /dev/mapper/isw_dbdbgfbgbe_RAID0RST: 18.2 GB, 18181521408 bytes
255 heads, 63 sectors/track, 2210 cylinders, total 35510784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dbdbgfbgbe_RAID0RST1               1    35510783    17755391+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 15.6 GB, 15610576896 bytes
119 heads, 55 sectors/track, 4658 cylinders, total 30489408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    30489407    15240672    c  W95 FAT32 (LBA)

```
[/SIZE]
[SIZE=4][SIZE=3]Hardware

[SIZE=2]Asus Zenbook Ux51Vz-XH71
Brand new, sexy.
Came with Windows 8 Pro 64-bit out-of-the-box.
[SIZE=4][SIZE=3][SIZE=2]Specs are listed [here]("http://www.asipartner.com/128854.html")[/SIZE][/SIZE][/SIZE].

PNY 16GB USB 2.0 stick ([P-FD16GATT03-GE]("http://www.amazon.com/PNY-Attache-Flash-Drive-P-FD16GATT03-GE/dp/B003SGQQQU")).
New.
FAT32 formatted out-of-the-box.[/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by yancek on 2014-07-04
What does GParted show?  It's on the Ubuntu installation medium.  When you have RAID, multiple disks are shown as one.  It appears you have two disk of about 250GB??  I believe the problem is a combination of RAID and GPT, two things I know nothing about but I'm sure someone will come along.

---

### Post by Brian_Schmitz on 2014-07-05
I also suspect RAID or GPT may have something to do with it, although I'm also clueless about them.

Opening GParted always triggers this error message:

[IMG]http://imagizer.imageshack.us/a/img843/7694/48da.png[/IMG]

I X out the message and look at the devices in GParted.

The first is RAID0RST (Apparently Intel had a purpose for it at one time, but it's not used for anything now as far as I know.):

[IMG]http://imageshack.com/a/img850/8466/dokj.png[/IMG]

The second is RAID0SYS. (This is the drive I tried to install on when I received the "???" message):

[IMG]http://imageshack.com/a/img840/4296/ejg.png[/IMG]

The third is sda. (Note the exclamation mark and the fact that the partition table couldn't be recognized; this apparently couldn't be read properly according to the error message):

[IMG]http://imageshack.com/a/img855/3382/x8w0.png[/IMG]

The fourth is sdb. (Again note the exclamation mark and the fact that the partition table is unrecognized.):

[IMG]http://imageshack.com/a/img823/3050/9afw.png[/IMG]

Finally we have sdc, which is simply the USB drive with the installer. (Note also the warnings in the background. These occurred when I opened GParted and when I X'd the error message):

[IMG]http://imageshack.com/a/img840/3991/kouo.png[/IMG]

---

