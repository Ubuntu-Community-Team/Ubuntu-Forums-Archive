---
title: "Dual boot not working (ubuntu NBR Alpha3 + Windows7)"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by yuger on 2010-03-21
[SIZE=2]hi i ve recently installed Ubuntu 10.04 Alpha-3 Netbook remix on my eeepc [/SIZE][SIZE=2]which was running wih windows 7 on it . installation of ubuntu was successful and it worked well , but when i choose "windows 7 (loader) (on /dev/sda1 )" from grub menu it gave me error saying "[/SIZE]
 > [U][COLOR=Black]windows failed to start. A recent hardware or software change might be the cause . to fix the problem:
<repair bla bla bla>

status: 0xc000000f
info: The boot selection failed because a required device is inaccessible[/COLOR][/U][U][COLOR=Black]
[/COLOR][/U]
additional info:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary
/dev/sda2              13        3134   25063424   83  Linux
/dev/sda3            3134        8616    44040192   6  FAT16
/dev/sda4            8616       19458    87081984  7   HPFS/NTFS
Partition 4 does not end on cylinder boundaryany way to get dual boot working ?

---

### Post by Herman on 2010-03-21
Did you resize the Windows7 partition with a partition editing program?
Either the Windows7 disk management utility or the partition editor in the Ubuntu installer can resize a Windows 7 partition without moving the Windows 7 boot sector.
You can also resize a Windows 7 partition safely with GParted, but you must remove the uncheck the box for 'align partition to cylinder boundaries.

Most Windows 7 partitions are supposed to start in sector number 2048, if you run 'sudo fdisk -lu' you'll be able to tell, but 'sudo fdisk -l' only shows which cylinder it starts in.
Probably it should start in about cylinder 32 1/2, unless EeePC installations of Windows 7 are different. Yours starts in cylinder 1 according to your fdisk output.

Does your EeePC has a CD drive?
I guess probably not, but if it does your can easily run 'Startup Repair' from your Windows 7 Installation DVD and fix the boot loader automatically.

---

