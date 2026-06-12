---
title: "trouble installing Ubuntu"
date: 2015-03-19
forum: Installation &amp; Upgrades
---

### Post by Robert_Holden on 2015-03-19
i am trying to install ubuntu 14.10 form a usb drive onto a partition on my hardrive and the 2 errors i have encountered are dual boot wont show up on another partition. the other is when i install from within windows i select drive c with 30gb but when i restart it says there are too many primary partition then gives the no root directory. can anyone help me?

---

### Post by yancek on 2015-03-19
Do you have a partition on your hard drive already formatted with a Linux filesystem?  You can't do that from windows.  Also, installing from within windows was done in the past by the "wubi installer" which is no longer supported and probably won't work.  Best bet is to resize (shrink) your windows partition and create unallocated space on which to install Ubuntu.  You can create partitions and format during the installation.  If you haven't done this before, I would suggest reading the very detailed tutorial at the link below.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Robert_Holden on 2015-03-19
that is what i did but i think the boot loader is not installing correctly or something similar to dual boot problems

---

### Post by yancek on 2015-03-19
You need to post which version of windows you are using, it makes a difference.  If you have windows 8, the setup will probably be different as it uses UEFI/GPT to boot so you would need to install Ubuntu in UEFI/GPT mode also.  Can you boot the Ubuntu installation medium and select Try Ubuntu and when you get to the Desktop, open a terminal and enter the following command and post the output here:

```
sudo fdisk -l
``` 

If you have the standard MBR partitioning method, you can only have four primary partitions and the output of the command above should give us that info.

---

### Post by Robert_Holden on 2015-03-19
ran the command on try ubuntu

```


Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x62484ec3
 
Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2       718848 621040663 620321816 295.8G  7 HPFS/NTFS/exFAT
 
Disk /dev/sdb: 28.9 GiB, 31009800192 bytes, 60566016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3ede457
 
Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        8064 60566015 60557952 28.9G  c W95 FAT32 (LBA)


```

am running windows 8.1

---

### Post by yancek on 2015-03-19
Your attempt to install Ubuntu didn't work.  You have two windows partitions and you have about 2GB of unallocated space at the very end of the disk.  That is not enough on which to install Ubuntu.  As I suggested above, you need to shrink the larger windows partition to make room for Ubuntu.  Since you have windows 8.1 installed, you are probably using UEFI/GPT for booting and partitioning setup.  You should have an option when rebooting the computer with the DVD or flash drive containing the Ubuntu install medium set to first boot priority in the BIOS setup to install in UEFI.  I don't use it myself and if you don't know how to access the BIOS, watch the screen when the manufacturer logo appears immediately on boot.  It will tell you which key to press to "enter setup".

---

### Post by Impavidus on 2015-03-20
Output from fdisk -l does not indicate UEFI/GPT. Was this Windows not preinstalled?

Shrink the Windows partition using Windows tools. First defragging the Windows partition may speed things up. Then reboot a couple of times to allow Windows to run its disk checks and do some cleanup after the resize. Make sure the faststartup or whatever it's called (the semi-hibernation state Win 8 may use for faster booting) is disabled, to allow Ubuntu to properly detect Windows.

---

### Post by Robert_Holden on 2015-03-20
i understand how the partitioning works but when i  start up i cant figure out how to get to the bios on this laptop i've looked everywhere this is an upgraded windows from windows 7

update: i found out how to get into the bios but in order to disable fast boot i have to turn on UEFI only which breaks windows because the hard drive is not even on as a boot option
is it possible for me to install an old version of ubuntu say 12.10 and then upgrade is to 14.10?

---

### Post by Mark Phelps on 2015-03-20
The boot-related option in Win8 that is the problem is FastStartup, and that is different from Fast Boot.  You only need to disable FastStartup in Win8 if you intend to access the Windows filesystem when in Ubuntu -- actually, a bad idea as that can lead to filesystem corruption.

You don't need to access the BIOS or UEFI to shrink the Windows filesystem partition; you do that using Disk Management in Win8.1

---

### Post by Robert_Holden on 2015-03-20
i know how to partition the reason i only had 2 for windows is because i was trying the wubi installer but that did not work

---

