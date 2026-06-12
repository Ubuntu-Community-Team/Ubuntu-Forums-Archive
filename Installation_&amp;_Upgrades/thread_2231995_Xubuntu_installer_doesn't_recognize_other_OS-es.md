---
title: "Xubuntu installer doesn't recognize other OS-es"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by numiz on 2014-06-29
I already have a dual boot of Win XP and Win 7. I wanted to add Xubuntu from live USB, but the installer doesn't give me the option to install it alongside other systems.

Output od sudo fdisk -lu:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a779a77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156299326    78149632    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b153b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    73400319    36700128+   7  HPFS/NTFS/exFAT
/dev/sdb2        73400922   320159384   123379231+   f  W95 Ext'd (LBA)
/dev/sdb5        73400985   320159384   123379200    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 4051 MB, 4051697664 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe16cd6ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7887914     3943926    b  W95 FAT32


```

Output of sudo parted -l
```
Model: ATA WDC WD800JD-00HK (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  80.0GB  80.0GB  primary  ntfs         boot


Model: ATA Maxtor 6L160M0 (scsi)
Disk /dev/sdb: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  37.6GB  37.6GB  primary   ntfs         boot
 2      37.6GB  164GB   126GB   extended               lba
 5      37.6GB  164GB   126GB   logical   ntfs


Model: JetFlash Transcend 4GB (scsi)
Disk /dev/sdc: 4052MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4039MB  4039MB  primary  fat32        boot

```

Gparted shows all partitions fine. The only exception is the installer which seems not to recognize one hard disk (/dev/sda). Windows shows partitions as basic with simple layout and MBR table. I don't know if it uses AHCI or IDE since it is nowhere in BIOS to change. Any suggestions would be greatly appreciated. I have been searching for a solution for a few days, but for most people, the problem turns out to be GPT table. I checked for this using fixparts and it found nothing (as it shouldn't since the computer is quite old. It did have Win 8.1 on it once though.).

[ATTACH=CONFIG]254333[/ATTACH][ATTACH=CONFIG]254330[/ATTACH][ATTACH=CONFIG]254331[/ATTACH][ATTACH=CONFIG]254332[/ATTACH]

---

### Post by Bucky Ball on 2014-06-29
Welcome. Where exactly are you intending to install it? You have no free space on either drive. Ubuntu can't install alongside Windows if there is no free space to install to. 

You need to shrink a partition to create free space.

---

### Post by numiz on 2014-06-29
But I installed it on my laptop that way just fine. By free space you  mean unallocated space? Laptop had no unallocated space, and the  installer let me choose the size of a new partition. It had a simpler  setup though, single partition with Win 8 on it.

---

### Post by Bucky Ball on 2014-06-29
You are talking about Wubi? Install Ubuntu inside Windows? If you are installing Ubuntu successfully and have no free space to start with, you must be. 

Wubi is no longer supported by Canonical and you will get very little help with it here. Please read:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Good luck.

---

### Post by numiz on 2014-06-29
What is Wubi? xD

I used a live USB in both cases.

EDIT: Looked it up, no, I'm not using Wubi. Just a normal install from inside the live environment.

---

### Post by Bucky Ball on 2014-06-29
Okay, well if you are successfully installing Ubuntu with no unallocated space to install to to begin with, you have me totally stumped, sorry. :-k

---

### Post by numiz on 2014-06-29
I have no idea, the installer offered me the "Install Xubuntu alongside Windows" option, then it let me adjust the size with a slider. Note that this is another computer (the laptop); the one I'm having problems with and for which I posted this thread is desktop, because it doesn't offer me this option.

It looked similar to this:
[http://www.dedoimedo.com/images/computers_years/2014_1/dual-boot-windows-7-xubuntu-installation-type.jpg](http://www.dedoimedo.com/images/computers_years/2014_1/dual-boot-windows-7-xubuntu-installation-type.jpg)

---

### Post by Bucky Ball on 2014-06-29
Yep, now I'm with you.

Which drive are you trying to install to? sda or b?

---

### Post by numiz on 2014-06-29
a, but I'm not particularly picky. I could squeeze it on sdb5 too. And it doesn't show sda in installer at all.

---

### Post by numiz on 2014-06-30
If I make some free space myself and install Xubuntu there, will it mess up boot of other OSes?
[B]
EDIT:[/B] Solved! Turns out sda had some spare RAID data on it. I ran sudo dmraid -rE and that did the trick.

---

### Post by numiz on 2014-07-02
Sorry, but where should the bootloader be installed, since I have Windows XP on one hard disk and 7 on the other hard disk?

---

### Post by sudodus on 2014-07-02
Congratulations to finding the raid data and solving the problem :KS

I would install grub to the same drive as Xubuntu (which I think is **/dev/sda**). Install it to the head of the drive (there should be no partition number). You may have to change the boot order in the BIOS menu system, so that the computer looks for the bootloader in that drive.

---

### Post by numiz on 2014-07-02
Thank you. I thought I'd install it there too, but the fact that Windows 7 is on /dev/sdb (and its bootloader governs both 7 and XP) confused me.

---

### Post by sudodus on 2014-07-02
I think it will work without any manual intervention.

If you have problems, you might be able to chainload to /dev/sdb and the Windows versions. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

---

### Post by numiz on 2014-07-02
OK, one last question (sorry, I'd rather not mess the boot up): sudo os-prober returns this:
```
/dev/sda1:Windows 7 (loader):Windows:chain
```
Where is Windows XP?

---

### Post by sudodus on 2014-07-02
I think you get from grub to a second menu (of Windows 7), where you can select between the two Windows versions.

---

### Post by numiz on 2014-07-02
Yeah, I read it's supposed to work that way.

OK then, here goes the installation! :D

---

### Post by yancek on 2014-07-02
> I think you get from grub to a second menu (of Windows 7), where you can select between the two Windows versions. 		

That has been my experience also.  Windows bootloaders are backward compatible meaning if you install windows 7 after xp, the 7 bootloader will detect and create an entry for xp.  It is possible to do the reverse but from what I have seen at the microsoft sit, it gets pretty messy and includes manual modificaation of the various boot files.  If you have xp on sda, I would not be surprised if the windows 7 boot files are there also.

---

