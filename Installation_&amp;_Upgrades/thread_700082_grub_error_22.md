---
title: "grub error 22"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by edieguez on 2008-02-18
Something changed on my machine and now grub refuses to boot. When I boot my machine I get the following:

Grub Loader stage1.5
Grub is now loading, please wait...
Error 22

When I boot the Kubuntu 7.10 live CD and choose the 'Boot from the first hard drive option' I get the grub menu correctly, but booting off the hard drive gives the error mentioned above. I've tried booting using the live CD and then the following commends:

sudo grub
find /boot/grub/stage1
root (hd0,5)
setup (hd0)

but I still get the error. I am out of ideas and this is driving me crazy.

---

### Post by amohanty on 2008-02-18
For extended docs:
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

Basically grub cannot find your partition. Every so often grub disagrees with the BIOS and uses its own damn partition info which screws it all up. 

Can you post your partition information outlining what is installed where?
And the contents (non-commented contents only please) of /boot/grub/menu.lst?
And the contents of your /etc/fstab? 

AM

---

### Post by edieguez on 2008-02-18
OUTPUT OF FDISK


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3b3f3b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12111    97281576   83  Linux
/dev/sda2           12112       24320    98068792+   f  W95 Ext'd (LBA)
/dev/sda5           12112       12761     5221093+  82  Linux swap / Solaris
/dev/sda6           12762       24320    92847636   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
96 heads, 63 sectors/track, 80753 cylinders
Units = cylinders of 6048 * 512 = 3096576 bytes
Disk identifier: 0xe6cf6a9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       80754   244198552+   7  HPFS/NTFS



CONTENTS OF MENU.LST


title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dad53304-6fc6-4499-a624-9c2fe5122f9e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dad53304-6fc6-4499-a624-9c2fe5122f9e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=dad53304-6fc6-4499-a624-9c2fe5122f9e ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=dad53304-6fc6-4499-a624-9c2fe5122f9e ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader     +1


CONTENTS OF FSTAB


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6 -- converted during upgrade to edgy
UUID=dad53304-6fc6-4499-a624-9c2fe5122f9e / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
#UUID=c254e954-f0bd-453f-892c-c84e6a72cd7b /media/sda1 ext3 defaults,errors=remount-ro 0 1
UUID=c254e954-f0bd-453f-892c-c84e6a72cd7b /home ext3 nodev,nosuid,errors=remount-ro 0 2
# /dev/sdab -- converted during upgrade to edgy
UUID=80A860A4A8609B04 /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=136df77b-4688-43a7-8c7e-91d01ddd84fc none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by amohanty on 2008-02-18
Try this:
boot normally, 
press esc to get to grub menu ( this will be before the loading stage 1.5)
selec the kernel you want to boot from, if you press enter - you _should_ get the same error
now press 'e' - now you can edit the bootup options

type in:
root (hd0,0)

and boot, see if it works.

HTH
AM

---

### Post by edieguez on 2008-02-18
It started to work suddenly after repeatedly trying to reinstall grub. I have no idea which step fixed the problem but I won't complain! Thanks for your help.

---

