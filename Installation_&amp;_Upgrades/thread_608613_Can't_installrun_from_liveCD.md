---
title: "Can't install/run from liveCD"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by rutigl on 2007-11-10
I have the following hardware configuration:
Motheboard - Intel 82865PEMA based on 865 chipset.
Processor - Pentium P4 2.4GHz
Hard disks:
1 - IDE Western Digital 80GB WD800JB
2 - SATA1 Western Digital 250GB WD2500KS
I have installed Win2000 SP4 on 80GB hard disk.
Using Partition Magic I divided my 250GB hard disk into 2 parts, i.e., made 40GB free and un-formatted.
After that I rebooted my PC and put liveCD with Ubuntu 7.10 into drive.
PC recognized the CD, I pressed on Install or Run from CD.
CD scanned my PC, after that appears empty black screen with blinking cursor in the top left corner.
That's it!
I wait for half an hour, nothing happened.
So I rebooted my computer and continued to work with Windows.
What is wrong? Please, explain me, what should I do to install Ubuntu on my computer?

---

### Post by atomkarinca on 2007-11-10
you can always try the alternate cd. on the ubuntu download page you should see a checkbox at the bottom, if you check it you can download the alternate cd image. this will probably solve your problem.

---

### Post by jken146 on 2007-11-10
Hi there.  Perhaps your live CD did not burn properly.  You could try burning it again at the slowest speed available.  If you have no luck with that you could always try the "alternate" install disc instead.  Good luck!

---

### Post by rutigl on 2007-11-13
I checked my liveCD, It has no errors. I also tried to install from alternative CD, and with no result. It can't install X-server.
There are 3 main differencies between my hardware configuration and new computers:
1. 448 pins processor instead of 778 pins, That's can't influent, because doesn't require specific drivers.
2. SATA-1 instead of SATA-2 hard disk. That's also can't be a problem, because Ubuntu installation process makes partition in a proper way.
3. AGP video-card connector and ATI Rageon Video-card.
If this is a problem, please, explain me, if it is possible to install Ubuntu. And if not, please, do me a big fafour, add to your hardware requirements - on-board or PCI-Express video-card!

---

### Post by bulldog on 2007-11-13
I think the ATI card is the problem.
Try the alternate cd which is text based,to install.
Your problem can be solved by installing the drivers for your graphics.
But to do that you have to install first :)

There could be an option on your live cd what says 'safe graphics mode' if there is one try to use it first.
[don't use live cd,so I'm not totally sure about that one]

---

### Post by Newbie1978 on 2007-11-13
Same thing happen to me when I try to run and install the live CD, I have an HP laptop and I find a solution, when the welcome ubuntu screen appears you hit the F6 key and then type "noapic" this works for me, I hope it will for you too :)

---

### Post by rutigl on 2007-11-13
Yes, noapic solved the problem, but only for 7.04 LiveCD. 7.10 LiveCD didn't start anyway, either in standard or in save graphic mode.
But now I have another problem. After successful installation on boot I always get Grub Error 22.
I have the following hard disks:
1. IDE 80GB - with Win2000 FAT32 - Primary
2. SATA1 250GB - divided into 3 parts:
1 - 200GB - NTFS - Primary
2  - 37GB - ext3 - Primary
3 - 2GB - swap - Primary
2 and 3 were created by Ubuntu installer.
So I succeded after these boot errors to recover my Win2000 using fdisk, but how can I make dual boot and how can I force Ubuntu to work?

---

### Post by rutigl on 2007-11-14
Partition Magic Information:
Disk1                                  Size          Status   Pri/Log
(*)                  Unallocated       211.8   None     Primary
Local Disk (C:)   FAT32         76,104.8   Active    Primary (Win2000)

Disk 2
Local Disk (D:)  NTFS          199,999.7   None     Primary (data)
Local Disk (*)  Linux Ext3     37,001.3   Active    Primary (Ubuntu)
(*)                 Extended       1,474.7    None     Primary
SWAPSPACE2  Linux Swap     1,474.7    None     Logical

Please help me to make dual boot, from which I will be able to choose or Win2000 or Ubuntu

---

### Post by rutigl on 2007-11-16
Here is the info from GPartEd:
1 /dev/sda
/unallocated - 211.83 MiB
/dev/sda1 - fat32 - 74.32 GiB

2 /dev/sdb
/dev/sdb1 - ntfs - 195.31 GiB
/dev/sdb2 - ext3 - 36.13 GiB
/dev/sdb3 - extended & swap - 1.44 GiB

and from menu.lst

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=cac071c0-baf8-4fbe-8476-2397a7108ebb ro quiet splash locale=ru_RU
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=cac071c0-baf8-4fbe-8476-2397a7108ebb ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows 2000 Professional RUS
root (hd0,0)
savedefault
makeactive
chainloader +1


Please tell me what to do?

---

### Post by bulldog on 2007-11-16
Don't use Partition Magic on linux file systems,they won't work well together.
Boot the live cd and type in a terminal```
sudo fdisk -l
``` and copy the output to the forum please.

---

### Post by rutigl on 2007-11-16
Disk /dev/sda: 80.0 GB, 80026361856 byte
Device     Load     Begin    End        Blocks         Id  System
/dev/sda1   *          28        9729    77931283+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 byte
Device     Load     Begin    End        Blocks         Id  System
/dev/sdb1               1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2   *       25497       30213    37889302+  83  Linux
/dev/sdb3           30214       30401     1510110    f  W95 extended (LBA)
/dev/sdb5           30214       30401     1510078+  82  Linux swap / Solaris

Sorry, if something wrong, I work in Russian, so translated some words by myself.
Please, help me.
I am really not an expert in Linux, and desperately need in your assistance.

---

