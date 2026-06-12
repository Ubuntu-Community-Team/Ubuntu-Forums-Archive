---
title: "Lost system, can't reinstall"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2006-12-13
I was fiddling about trying to fix a graphics cad issue when I suddenly lost X and could no longer boot into a graphical environment. After attempting to fix it in vain, I decided to reinstall Ubuntu (I was planning on doing it soon anyway). The isntallation went without errors but on reboot I got a GRUB screen offering different modes of startup. When I choose my kernel I get an error number 15 file not found in reference to a kernel image at /boot....
Same story with recovery mode. Thank heavens for Live CDs, but I've no idea what to do next.
What does this kind of message mean and how can I boot to my newly isntalled system?

---

### Post by wpshooter on 2006-12-13
If you only have and want Ubuntu on this machine then:

Get the **KILLDISK** program and** WIPE** the hard drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

And then reinstall your Ubuntu.

Good luck.

---

### Post by pickarooney on 2006-12-14
Microsoft Certified Partner.. hmmm
I'd like to know what exactly is wrong and how to fix it normally, though.
I just wiped the HD again and installed Kubuntu. After reboot it's the same story, GRUB loader and error 15 file not found each time.

I think there might be a link between this and the fact that GRUB claims to have found another Linux installation. There's the remains of a Breezy installation on a secondary hard drive and this appears in the list of available OSes. I don't know how to get at the boot file to remove this broken, old installation.

---

### Post by pickarooney on 2006-12-14
OK, managed to mount my hard drives (this is a HUGE oversight on the live CD surely, no graphical interface for mounting your HD?) and view the menu.lst file

I think the problem might be related to an old, broken installation of Ubunu Breezy the boot loader picked up on a secondary hard drive and lists as an option at boot time.
menu.lst looks like this:
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
# kopt=root=UUID=5bec61b0-4e6c-4df2-a10b-896bee3cc2ac ro
# kopt_2_6=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-10-386 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, memtest86+ (on /dev/hda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

All the stuff after ### END DEBIAN AUTOMAGIC KERNELS LIST is irrelevant to my installation.

---

### Post by seshomaru samma on 2006-12-14
What's you fdisk?
```
sudo fdisk -l
```

---

### Post by pickarooney on 2006-12-14
I followed [this](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1413211) guide to the letter and still no luck. I can't even boot into GRUB now, let alone Linux.

**sudo fdisk -l** gives this:
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         127     1020096   83  Linux
/dev/sda2           23948       24321     3004155    5  Extended
/dev/sda3             128        5226    40957717+  83  Linux
/dev/sda4            5227       23947   150376432+  83  Linux
/dev/sda5           23948       24321     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9729    78148161    5  Extended
/dev/hda5             702         732      248976   82  Linux swap / Solaris
/dev/hda6             733        9729    72268371   83  Linux
/dev/hda7               1         701     5630688   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19193   154167741   83  Linux
/dev/hdb2           19194       24792    44973967+   5  Extended
/dev/hdb5           19194       24792    44973936   83  Linux

Disk /dev/sdf: 65 MB, 65536000 bytes
5 heads, 32 sectors/track, 800 cylinders
Units = cylinders of 160 * 512 = 81920 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         800       63983    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1000, 4, 32) logical=(799, 4, 30)

```

the relevant part of /boot/grub/menu.lst is now:
```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

I tried the kernel line with and without /boot, to the same, negative effect.

**fstab** is like so:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=23cd75dd-8522-4cc8-8026-43d34facd54f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=38771644-df5d-4863-95ef-4abcf0a9c696 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=6aca9cac-5354-4183-bf88-68e9e62bed9a /home           ext3    defaults        0       2
# /dev/hdb5
UUID=faf11a4c-4365-4982-98c9-fcf80bc73ca5 /media/backup   ext3    defaults        0       2
# /dev/hda6
UUID=f3466d96-c519-11d7-9a37-a027fa319c88 /media/oldhome  ext3    defaults        0       2
# /dev/hda7
UUID=bb8c5418-a024-4cc0-a287-4b1b083042af /media/oldsystem ext3    defaults        0       2
# /dev/hdb1
UUID=f084d777-e5ba-49df-b71b-729b2c0d2475 /media/supersize ext3    defaults        0       2
# /dev/sda5
UUID=7db0edf9-d00d-4b15-a5c3-c738a9091488 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

SDA is the SATA HD where I've just installed Kubuntu. HDB is a data disk and HDA is a third HD with an old Linux installation and my backed up home directory from before the reinstall.
I don't know what **initrd** is but I suppose it should have the same path as the kernel, whether that's with or without the /boot or not I can't figure. /boot is a separate partition on SDA1 by the way. Maybe there should be a **boot=/dev/sda** somehwere in menus.lst?

**/boot** contains:  abi-2.6.17-10-generic     grub                          lost+found      System.map-2.6.17-10-generic
config-2.6.17-10-generic  initrd.img-2.6.17-10-generic  memtest86+.bin  vmlinuz-2.6.17-10-generic

**/boot/grub** contains: efault     e2fs_stage1_5  installed-version  menu.lst      minix_stage1_5     stage1  xfs_stage1_5
device.map  fat_stage1_5   jfs_stage1_5       menu.lst.old  reiserfs_stage1_5  stage2

Perhaps I should (re-)run grub-install, but with what parameters?

---

### Post by pickarooney on 2006-12-14
getting closer to it...
GRUB is on the wrong hard drive I *think*:
```

grub> find /etc/fstab
find /etc/fstab
 (hd0,6)
 (hd2,2)
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,6)
grub> root (hd2,2)
root (hd2,2)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub>

```

How to know if (1,6) or (2,2) is the SATA drive? and how to move GRUB to the right place?

---

### Post by wpshooter on 2006-12-14
> **pickarooney said:**
> getting closer to it...
GRUB is on the wrong hard drive I *think*:
```

grub> find /etc/fstab
find /etc/fstab
 (hd0,6)
 (hd2,2)
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,6)
grub> root (hd2,2)
root (hd2,2)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub>

```

How to know if (1,6) or (2,2) is the SATA drive? and how to move GRUB to the right place?

Have you tried WIPING your hard drives with the KILLDISK program like I suggested ?

I believe it will allow you to wipe ALL the drives on your system and you can stop fooling around with this stuff and get the O/S properly installed on your computer.

---

### Post by pickarooney on 2006-12-15
> **wpshooter said:**
> Have you tried WIPING your hard drives with the KILLDISK program like I suggested ?

I believe it will allow you to wipe ALL the drives on your system and you can stop fooling around with this stuff and get the O/S properly installed on your computer.

NO, I don't want to wipe 300 GB of data, I just want to fix the bootloader, thanks.

---

