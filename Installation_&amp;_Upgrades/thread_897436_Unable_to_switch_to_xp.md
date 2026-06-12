---
title: "Unable to switch to xp"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by vampur on 2008-08-22
Hi freinds 

I tried a lot to switch to the xp the older os of mine and also i could not access the drive in which the xp was installed ,, 
is dere any way so dat i can reslove da xp  n it's data .. 

dat's my grub output

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=65adad4e-99ef-4552-9140-478faad5eff7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=65adad4e-99ef-4552-9140-478faad5eff7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by forger on 2008-08-22
you could try fixing it with [supergrubdisk]("www.supergrubdisk.org")

---

### Post by vampur on 2008-08-22
????????????

sudo mount -o force -t ntfs /dev/sda1 /media/WindowsXP
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


any help 
please

---

### Post by sandysandy on 2008-08-22
post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

have u tried super grub disk!

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by vampur on 2008-08-22
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c112c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sda2        30716280   156296384    62790052+   f  W95 Ext'd (LBA)
/dev/sda5        30716343    92148839    30716248+   b  W95 FAT32
/dev/sda6        92148903   112631714    10241406    b  W95 FAT32
/dev/sda7       112631778   136054484    11711353+   b  W95 FAT32
/dev/sda8       136054548   155332484     9638968+  83  Linux
/dev/sda9       155332548   156296384      481918+  82  Linux swap / Solari


any way i can reslove and i haven't tried supergsub 

is dere any way i can get my data of xp which is winxp pro sp3

---

### Post by vampur on 2008-08-22
which version i download for sgrup?????

---

### Post by sandysandy on 2008-08-22
download super grub disk ([COLOR="Blue"]SGD[/COLOR]) from following link and burn as iso image

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

see this link also.

[http://users.bigpond.net.au/hermanzo...bdiskpage.html](http://users.bigpond.net.au/hermanzo...bdiskpage.html)

pop SGD into Cd drive and reboot computer. it will boot into SGD, use the help option. it will guide u step by step.

see if u can boot into XP from SGD

regards

---

### Post by SkonesMickLoud on 2008-08-22
From within Ubuntu, start up a terminal and enter:

```
sudo gedit /boot/grub/menu.lst
```

Enter your sudo password.

Add "makeactive" to the XP entry in menu.lst.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
[COLOR="Red"]makeactive[/COLOR]
chainloader	+1
```

Save.

Reboot and see if you can get XP to load.

---

### Post by vampur on 2008-08-22
it just says now 
bash: /boot/grub/menu.lst: Permission denied

---

### Post by sandysandy on 2008-08-22
try this code

[COLOR="Blue"]gksudo gedit /boot/grub/menu.lst[/COLOR]

it will ask u for password. use ur normal password.

regards

---

### Post by vampur on 2008-08-22
i treid that active one but still dosen't work dear

---

### Post by sandysandy on 2008-08-22
> **vampur said:**
> i treid that active one but still dosen't work dear

do u have the requisite privileges on your account to use [COLOR="Red"]sudo.
[/COLOR]
regards

---

