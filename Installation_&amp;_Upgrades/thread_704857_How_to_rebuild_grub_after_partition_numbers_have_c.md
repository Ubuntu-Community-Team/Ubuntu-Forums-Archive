---
title: "How to rebuild grub after partition numbers have changed?"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by mogie on 2008-02-22
After I deleted a primiray partition between my XP partition and my Ubuntu-partitions, my GRUB went wrong of course..

There's an Grub Error 17 - saying it cant find the partition it is looking for etc..

Anyways, I want to automatically reinstall GRUB again, by it detecting the partitions on its own (like when I installed ubuntu for the first time) and correct the partition number since I can't do this by hand.. (I not that clever in the grub > cmd window yeat..)

I'm able to boot Ubuntu with a so called "Super Grub Resque Disk" - very handy - and read the menu.list, where I change root line from (hd2,6)-->(hd2,5) and then boots.

Hopes there's an easy solution to this. In case the menu.lst and fstab would be any use, here they are :)


Thanks for all support!

menu.lst
```

default		1

timeout		5


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fed032de-4f43-4463-b928-1ac55e66fa35 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Windows XP SP2 (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc7
UUID=fed032de-4f43-4463-b928-1ac55e66fa35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=18A8718DA87169E0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=137A0E1FDD27A2E9 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=AF393E99DA789169 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=02B8A1647802CE90 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=137999FC791BC6F9 /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc2
UUID=9AAC2BF4AC2BCA19 /media/sdc2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc4
UUID=E6E88A5AE88A28BF /media/sdc4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc5
UUID=52549051549039A5 /media/sdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc6
UUID=E4D438AED43884B8 /media/sdc6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc8
UUID=38b82365-9bf8-4c7d-90a8-94f4fd83b0aa none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by logos34 on 2008-02-22
Edit menu.lst as root and then reinstall grub to the mbr of your boot disk.

gksudo gedit /boot/grub/menu.lst

change 'groot' and 'root' lines.

To reinstall grub:

> sudo grub

> root (hd2,5)
> setup (hd0)
> quit

---

### Post by mogie on 2008-02-22
Weeehee! :D

Thank u so much! That worked a bunch ;)

---

