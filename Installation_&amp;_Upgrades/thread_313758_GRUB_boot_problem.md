---
title: "GRUB boot problem"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by trinitry on 2006-12-06
hi everybody, i am new in Ubunto OS and i have my first issue. I installed Ubuntu in a partition that used to be WinME. I can boot in Ububtu but not in the winXP. My /boot/grub/menu.lst is:
title		Microsoft Windows XP Professional
rootnoverify	(hd0,5)
savedefault
makeactive
chainloader	+1
any help is more than welcome thanks.

---

### Post by eriefisher on 2006-12-06
What is the output of:

sudo fdisk -l

This will tell you exactly where xp is and you can tell grub.

---

### Post by trinitry on 2006-12-06
the output of that command is:

trinitry@trinitry-ubunto:~$ sudo fdisk -lu
Password:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    19872404     9936171   83  Linux
/dev/hda2        20482875   160810649    70163887+   f  W95 Ext'd (LBA)
/dev/hda3   *    19872405    20482874      305235   82  Linux swap / Solaris/dev/hda5        20482938    48162869    13839966   83  Linux
/dev/hda6        48162933   160810649    56323858+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   398283479   199133707+   f  W95 Ext'd (LBA)
/dev/sda5           16128   204828749   102406311    7  HPFS/NTFS
/dev/sda6       204828813   398283479    96727333+   7  HPFS/NTFS

what i should do?

---

### Post by bulldog on 2006-12-06
Well I think you have to alter your boot.ini in the windows partition,normally windows is on your first partition.
You managed it to be on your fifth so it won't boot.

Take a look here,

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)
[http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP](http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP)

---

### Post by lha on 2006-12-06
You installed WinME first, then XP, didn't you? As far as I know, Windows has an akward way to dual-boot. When you installed XP, it put boot.ini, ntldr, and ntdetect.com on hda1. (Yes, on WinME's partition!)  Those files are needed to get XP up and running. Now that you have installed Ubuntu on hda1, XP has lost its boot loader. Usually, boot problems with Windows can be solved with the recovery tools on Windows' install cd, but I don't believe those will help here. Since Windows lost its boot partition, I see no easy options to get it running. I hope someone can come up with a good (or even a decent) solution... :(

---

### Post by Herman on 2006-12-06
Hello trinitry,
lha is right, Windows does have an awkward way to dual boot, and probably you don't have those files in Windows XP that you will need. You can take a look from Ubuntu, look at the second link bulldog gave to see how to check if those files are installed or not.

If you haven't got them don't give up. You should try to get the use of another computer that has Windows XP in it and follow the instructions Microsoft link which you will find in the links bulldog has given. This tells you how to make a Windows XP boot floppy with boot.ini, NTdetect.com and NTLDR on the floppy disk. It is important to follow the instructions about formatting the floppy from the DOS prompt, as other ways of formatting the floppy disk didn't result in a bootable floppy disk when I was testing this.

You will most likely have to edit the boot.ini in the floppy disk from Ubuntu with the correct partition number as explained in the link also.

Then that floppy disk should be able to boot your Windows for you. Once Windows is booted you should try copying the boot.ini, NTdetect.com and NTLDR from the floppy disk to your Windows XP and see if that will work or not.   I hope that work but I have never tried that before myself, so I don't know. I am pretty sure that at least that kind of floppy disk will boot Windows. I am not sure about boting Windows i a logical partition though, either. I will be interested to read how you get along.

Regards, Herman :D

---

