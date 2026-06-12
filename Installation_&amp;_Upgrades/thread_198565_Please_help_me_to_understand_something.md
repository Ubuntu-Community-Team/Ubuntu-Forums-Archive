---
title: "Please help me to understand something"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by HJB on 2006-06-17
Hi. Im very confused
I did a new installation of xubuntu
I have a 200gig sata drive and two other ide drives
I reformatted the 200gig drive (where 5.04 was) and partitioned it to:
Part#1 / (I made this one bootable)
Part#2 /boot
Part#3 /home
Part#5 swap
Part#6 /archives

everything went smooth.
Right at the end grub said it could see XP and wanted to know where to install (which MBR), so I picked /dev/sda
Still good
It then rebooted and complained that I couldn't find the drive (or something)
Grub set itself to
> title           Ubuntu, kernel 2.6.15-23-386
root            (hd2,1)
kernel          /vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd          /initrd.img-2.6.15-23-386
savedefault
boot


Why is this?
Anycase, it didn't work so I changed it to hd(0,0) which still didnt work and when I changed it to hd(0,1) all went well

Now if you look at this 
> sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97659134    48829536   83  Linux
/dev/sda2        97659135    97851914       96390   83  Linux
/dev/sda3        97851915   293170184    97659135   83  Linux
/dev/sda4       293170185   390716864    48773340    5  Extended
/dev/sda5       293170248   297170369     2000061   82  Linux swap / Solaris
/dev/sda6       297170433   390716864    46773216   83  Linux

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    61432559    30716248+  17  Hidden HPFS/NTFS
/dev/hda2   *    61432560   159091694    48829567+  83  Linux
/dev/hda3       159091695   174722939     7815622+  82  Linux swap / Solaris
/dev/hda4       174722940   234436544    29856802+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders, total 60074784 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    60050969    30025453+  1c  Hidden W95 FAT32 (LBA)

Look here also

> cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda


It doesn't make sense. Should GRUB not have set itself to hd(2,0)
I chnaged it to hd(2,0) but it didn't work?

Did it install  grub to somewhere else than sda?
How can I check where GRUB was installed?

Please help me to understnd this!
ALSO, how do I know which drive corresponds to which hd(x,y)
Is hda equals to hd(0). Does the bios setup play a role here?
What happens when a sata drive is installed??

This is one thing (amongst many): ) I dont understand about linux

Please help, I want to understand this
Bye
H:confused:

---

