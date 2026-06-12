---
title: "System won't boot after install"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by sx460 on 2005-08-29
Hello guys, I have 3 hard drives in my computer:

80GB IDE
80GB SATA
200GB SATA

Windows is installed on my 200GB drive. I also thought it would be nice to install Linux on that drive since it has so much extra room. I repartitioned my 200GB drive during the Ubuntu install and the install went smooth. Grub notice the Windows XP partition and install and added it to the Grub menu during install. Once install was done the computer rebooted and from them on could not enter either Windows or Linux because the boot loaded never displayed. It errored saying no bootable disk or OS found type error even though both Linux and Ubuntu are on the 200GB drive.

I've got my machine running again, have to reinstall Windows on the 200GB over the other Windows partition.

Any idea why this might have happend? This happened with 4.10 and was hoping it wouldn't happen with 5.04.

My machine specs are:

Ubuntu 5.04 32-bit
Athlon 64 3200+
1GB DDR400 Dual Channel
Soltek K8TPro-939

Thanks!

---

### Post by weekend warrior on 2005-08-30
Maybe I can get you started *hopefully* in the right direction. It sounds like a GRUB problem. Search the forums for "Grub problems XP". Try these threads...

[click me](http://ubuntuforums.org/showthread.php?t=56563&highlight=grub+problems+xp) 
[click me](http://ubuntuforums.org/showthread.php?t=59892&highlight=grub+problems+xp) 
[click me](http://ubuntuforums.org/showthread.php?t=49383&highlight=grub+problems+xp) 


This will tell you plenty about GRUB
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)


HTH

---

### Post by sx460 on 2005-09-01
Thanks for the information. Very much appreciated! I'll be taking the suggestion to install Grub to a floppy and then trying and then adding the boot loaded to the Windows partition later. Sounds like a good solution. Thanks!

---

### Post by FLeiXiuS on 2005-09-01
When you partitioned your disk did you give the partition containing /boot the bootable parameter?

---

### Post by sx460 on 2005-09-01
[QUOTE=FLeiXiuS]When you partitioned your disk did you give the partition containing /boot the bootable parameter?[/QUOTE]

I'm not sure if I did or not. I remember how I partitioned though... I used the paritioner inside the install of Ubuntu. I choose a drive which had a lot of free space (turned out to be the same drive I have Windows installed on), then resized the existing paritions so that I had free space for Ubuntu. Then went back to the install and told Ubuntu to use the free space on the drive and to parition it automatically (using the free space just freed by repartitioning the disk).

The drive is a 200GB SATA drive. The 2 partitions it had before repartitioning during Install were: 50GB for Windows, 150GB for data/backup, both NTFS partitions.

Any thoughts?

---

### Post by FLeiXiuS on 2005-09-02
Boot up the ubuntu system disk.  Go into recovery mode and see if the partition has the bootable parameter.

$ sudo fdisk -l

---

### Post by mcduck on 2005-09-02
Also you could go to BIOS and check what mode your HDD is using, there might be some options like 'LDA' or 'Large', try different settings. I had the very same problem, and setting HDD to 'Large' solved it..

---

