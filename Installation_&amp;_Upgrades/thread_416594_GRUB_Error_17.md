---
title: "GRUB Error 17"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Rat2000 on 2007-04-21
Hi, this is my first Ubuntu install. The installation went well but now when my system boots I get a "GRUB Error 17". I've seen other posts talk about this but I haven't found a solution that works for me.

Result from "sudo fdisk -l":
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48642   390709248    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       10158       19075    71633835   83  Linux
/dev/sdc2               1       10157    81586071    7  HPFS/NTFS
/dev/sdc3           19076       19452     3028252+   5  Extended
/dev/sdc5           19076       19452     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         502     4030432    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 14)
```

My Grub menu.lst:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ffd7d6d6-60df-4855-b254-b34c9f1628cc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ffd7d6d6-60df-4855-b254-b34c9f1628cc ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ffd7d6d6-60df-4855-b254-b34c9f1628cc ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
rootnoverify (hd1,0)
map	(hd0) (hd1)
map	(hd1) (hd0)
savedefault
makeactive
chainloader	+1

```

Thanks for any help!

---

### Post by bulldog on 2007-04-21
From which hdd are you booting?
Is GRUB on this hdd?

It's all a pointing matter,GRUB can see your hdd configuration different as you are seeing it.
Try```
cat /boot/grub/device.map
``` in a terminal to see how your device are listed.
Tell me which hdd is set to boot and if GRUB is located on this disk as well.

---

### Post by Rat2000 on 2007-04-21
cat on device.map returns the following:
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd

```

Ubuntu is installed in hd2 in a partition next to Windows XP so I guess that would be hd2,1 for Ubuntu (I used the guided partition resize to make the new partition on what was a Windows XP only disk).

---

### Post by bulldog on 2007-04-21
Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       10158       19075    71633835   83  Linux
/dev/sdc2               1       10157    81586071    7  HPFS/NTFS
/dev/sdc3           19076       19452     3028252+   5  Extended
/dev/sdc5           19076       19452     3028221   82  Linux swap / Solaris

If I look at the fdisk output,your ubuntu partition should be (hd2,0) the first partition on the sdc disk.
This is correct in menu.lst.
You can have a look at the UUID's if they are correct in menu.lst and fstab.
To find the UUID ```
ls /dev/disk/by-uuid -lh[compare the UUID you found with the one for sdc1 in menu.lst and fstab.
Correct them if needed,and if you did modify them[code]sudo update-grub
``` should be enough to let you boot into ubuntu.

---

