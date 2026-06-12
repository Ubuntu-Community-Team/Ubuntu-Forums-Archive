---
title: "Grub error 18: not sorting out"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by i.m.raziel on 2008-05-03
Hi! I'm new to linux community. I have a Compaq Presario 5130 desktop (PII 347 MHz, 192 MB RAM, 160 GB HDD(IDE)). I installed Xubuntu 8.04 and had the following error.
Grub loading stage 1.5......
Error 18.

I searched the net and figured out that it was due to old BIOS with new HDD. I downloaded Super Grub Disk and tried it but in vain. It did not show the partitions containing the Xubuntu Installation. I however tried the command
grub> root (hd0,10)
which returned the error 18.
I then reintalled grub with WINGRUB. Now it shows only windows in the boot menu.
The Partition Table of my hard disk is as follows:
Name   LDrv FS          Size
hd0,0  C    FAT32       4097M
hd0,1  -    ExtendedX   148515M
hd0,4  F    NTFS        25604M
hd0,5  D    FAT32       15359M
hd0,6  J    FAT32       15364M
hd0,7  G    NTFS        66563M
hd0,8  H    FAT32       10240M
hd0,9  I    NTFS        5146M
hd0,10 -    Linux Ext2  9750M
hd0,11 -    Linux Swap  486M

Now, is there a way out by configuring Grub so that Xubuntu can be booted? If yes please show detailed steps.

---

### Post by Pumalite on 2008-05-03
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by bobnutfield on 2008-05-03
When you start your computer and first see the Grub scree, hit the down arrow to stop the automatic boot.  Move to your linux boot line and type "e" (without the quotes).  That will display the parameters that Grub is using to boot your linus partition.  It would be helpful if you could post these lines back (you may just have to copy them down) and post them back here.

Bob

---

### Post by i.m.raziel on 2008-05-03
Sir after reinstalling grub (vide supra) all I see in the GRUB screen in Windows and no other OS. Help me to configure the menu.lst file so that the xubuntu partition can be added.

---

### Post by Pumalite on 2008-05-03
Post:
sudo fdisk -l
cat /boot/grub/menu.lst
You might need to boot Live CD and mount your partition.

---

### Post by i.m.raziel on 2008-05-03
@ Pumalite:
fdisk -1 lists only the windows partitions and not the linux partitions. (see my HDD partition table).
grub> rootnoverify (hd0,10) gives no error while
grub> root (hd0,10) gives error 18.
how to mount the linux partitio? LIve CD also does not display the linux partitions in the file manager or by fdisk -1.
The partition table I have given above is reported by WINGRUB.

---

### Post by dstew on 2008-05-03
The disk you have may be too big for your BIOS. See [Herman's grub error 18 page]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors") as recommended by Pumalite. You may be able to update the BIOS, but it might be too old. You might do better to put in a smaller hard disk. You can also try to re-install Xubuntu but make a 100 Mb ext3 partition at the front of the drive, and give it the mount point /boot. But, your drive is so big, I think your BIOS is choking on it.

---

### Post by Pumalite on 2008-05-03
You have to copy and paste the complete output here.

---

### Post by DBrocks on 2008-05-03
Basically it means that your boot partition is much too big for the hard drive. Use Gparted to make a new 200 mb partition for booting. Then boot the disk in recovery mode, press "esc" to select, and click "partition". Then select your 200 meg partition, and select it to mount "/boot".

---

### Post by i.m.raziel on 2008-05-05
Thank you for your kind help. It was indeed the BIOS problem.I used gParted to make a 200 mb primary partition by resizing drive C: (/dev/sda1) and mounted it as /boot followed by reinstallation. It worked!! But unfortunately I lost booting up Win98.
It'd take really a lot of time understanding Linux. Configuring everything is too complex. All I do is copy paste commands without even understanding a bit about it. I'm afraid that I might fall back to WinXP soon.

---

