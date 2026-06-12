---
title: "GRUB Error 17"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Synthdark on 2008-04-16
My laptop is a Inspiron 600m. The HDD crashed and I replaced it today with a 160GB EIDE drive.

Ubuntu 7.10 was installed and working fine on the old drive.

I have installed Win XP on the first partition and it's working fine. Then I went to install Ubuntu on the second partition (3rd part is a swap). Install went fine.

I can run mount /dev/sda2 and access the files through the live CD.

Upon boot I get GRUB Error 17.  I can boot Windows with Super GRUB but thats it.

Should an IDE drive be represented as a sda?
Anyone have any ideas?

sudo fdisk -lu
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x269d269c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   287997254   143998596    7  HPFS/NTFS
/dev/sda2       287997255   308672909    10337827+  83  Linux
/dev/sda3       308672910   312576704     1951897+  82  Linux swap / Solaris

```


grub> geometry (hd0)
```

grub> geometry (hd0)
drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82

```


/dev/sda2/boot/grub/menu.lst
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=17c14f75-ef82-450a-8d65-9af6d8d3cae2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=17c14f75-ef82-450a-8d65-9af6d8d3cae2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
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
makeactive
chainloader	+1

```


/dev/sda2/boot/grub/device.map
```

(hd0)	/dev/sda

```

---

### Post by Partyboi2 on 2008-04-16
you could try adding noverify to his part of grub menu.lst
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root[COLOR=Blue]noverify[/COLOR]        (hd0,0)
savedefault
makeactive
chainloader    +1[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#17") is some more info on grub error17

---

### Post by dstew on 2008-04-16
If you got the grub error number only, with no explanation, that means it is a stage1.5 error, and grub is mis-installed. You cannot fix it by editing the menu.lst file. To re-install grub, see [this HowTo]("http://ubuntuforums.org/showthread.php?t=224351").

---

