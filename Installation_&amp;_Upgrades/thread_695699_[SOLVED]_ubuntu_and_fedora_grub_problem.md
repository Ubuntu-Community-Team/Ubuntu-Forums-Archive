---
title: "[SOLVED] ubuntu and fedora grub problem"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by mohbana on 2008-02-13
hi guys i installed fedora after installing ubuntu, now i am stuck.  I had to manually edit the the grub on feedora aswell as ubuntu's grub.  Whats happening now is that it boats up ubuntu up, but it fails to load, its gets stuck after ***found 4 cpus***.  this is really strange, i have no idea whats going on, i am pretty sure this all happened after installing fedora because i changed the partion layout a little bit during install.  So i am assuming its something to do with that.  thanks for the help.  Fedora also overwrite the mbr grub.

the ubuntu grub

```
su -c 'cat /media/disk/boot/grub/menu.lst'
Password: 
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         2

# windows = 4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 ro
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 ro
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Fedora (2.6.23.14-107.fc8) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.23.14-107.fc8 ro root=LABEL=/1 rhgb quiet 
initrd          /boot/initrd-2.6.23.14-107.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Fedora (2.6.23.9-85.fc8) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.23.9-85.fc8 ro root=LABEL=/1 rhgb quiet 
initrd          /boot/initrd-2.6.23.9-85.fc8.img
savedefault
boot

```


fedora's grub

```
su -c 'cat /boot/grub/grub.conf'
Password: 
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.23.15-137.fc8)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.23.15-137.fc8 ro root=LABEL=/ rhgb quiet acpi=off
        initrd /boot/initrd-2.6.23.15-137.fc8.img
title Fedora (2.6.23.8-63.fc8)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.23.8-63.fc8 ro root=LABEL=/ rhgb quiet acpi=off
        initrd /boot/initrd-2.6.23.8-63.fc8.img
#title Ubuntu
#       rootnoverify (hd0,4)
#       chainloader +1
title Ubuntu
        configfile (hd0,4)/boot/grub/menu.lst
title Windows Vista
        rootnoverify (hd0,0)
        chainloader +1

```


all the partion tables.  sda5 is where ubuntu is installed, sda2 and sda3 are for fedora.

```
su -c '/sbin/fdisk -l'
Password: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6429e8e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32540   261368832    7  HPFS/NTFS
/dev/sda2           32541       34324    14329980   83  Linux
/dev/sda3           34325       35599    10241437+  83  Linux
/dev/sda4           36875       38913    16378267+   5  Extended
/dev/sda5           37385       38913    12281661   83  Linux
/dev/sda6           36875       37001     1020064+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000fc91f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

```

```
/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 160 2008-02-13 15:13 .
drwxr-xr-x 6 root root 120 2008-02-13 15:13 ..
lrwxrwxrwx 1 root root  10 2008-02-13 15:13 246880A368807578 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-13 15:13 3b56c34e-d857-443c-bba1-baf134865421 -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-02-13 15:13 6c59de33-1884-499b-9173-3ee88fd07970 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-02-13 15:13 80AC2108AC20F9F4 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-02-13 15:13 a0138ec0-ba7b-485d-b38d-477adb7b2803 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-02-13 15:13 f0e7fe54-a3e7-49df-96e6-cc267b430c31 -> ../../sda5

```

if you need any extra info then please tell what it is and i am quiet new to linux so please take it easy.

thanks alot

---

### Post by taurus on 2008-02-13
Since you are using GRUB from Fedora to boot your machine, you need to edit /boot/grub/grub.conf and replace two lines

```

title Ubuntu
        configfile (hd0,4)/boot/grub/menu.lst

```

with these to boot Ubuntu.

```

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 ro
initrd          /boot/initrd.img-2.6.22-14-rt

```
Save it and reboot.  Now, see if you can boot Ubuntu from the GRUB menu.

---

### Post by mohbana on 2008-02-13
thanks for the reply, i tried what you said but it doesn't work, *it still gets stuck when trying to load ubuntu but it gets past the grub bit*, i'll be back with some pics.

grub pic
[http://img514.imageshack.us/img514/775/pict0001xl5.jpg](http://img514.imageshack.us/img514/775/pict0001xl5.jpg)

"crash" pics
[http://img248.imageshack.us/img248/4673/pict0002ru9.jpg](http://img248.imageshack.us/img248/4673/pict0002ru9.jpg)
[http://img409.imageshack.us/my.php?image=pict0003wq6.jpg](http://img409.imageshack.us/my.php?image=pict0003wq6.jpg)

I'd like to point out that i changed the partion table quiet alot but i didn't touch the ubuntu (sda5) partion at all.

I changed the /etc/fstab to reflect this.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f0e7fe54-a3e7-49df-96e6-cc267b430c31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=246880A368807578 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
#UUID=112cbc61-ef9b-4afa-920f-e81ba72c1c2b /media/sda2     ext3    defaults        0       2
# /dev/sda3
#UUID=4bbd72e7-0c65-471d-a6b7-5712664657d2 /media/sda3     ext3    defaults        0       2
# /dev/sdb1
UUID=80AC2108AC20F9F4 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=3b56c34e-d857-443c-bba1-baf134865421 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```


My last resort would be to reinstall ubuntu, but i need to know a few things.

1.  How can i get access to the boot log to find out whats stopping ubuntu from loading, it just gets stuck at one position move.  On top of that i can't type anything in the console.
2.  Do i have an option as to where i can install grub if i install of the live cd?

thanks for your time.

---

### Post by taurus on 2008-02-13
Maybe this is what you want.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mohbana on 2008-02-13
i know nothing about linux but isn't this to do with ubuntu as i am getting past the grub menu and i can actually load ubuntu?

---

### Post by mohbana on 2008-02-13
What a long day, but i fixed.  It turned out to be something really strange.  Here is the low down.

1. I got feed up so i installed ubuntu again, this time i installed ubuntu's grub on ubuntu's "/", so the grub looks like this.

```
title Ubuntu
        configfile (hd0,4)/boot/grub/menu.lst
```

2.  i had to boot into the livecd with safe graphics mode and **"nosplash acpi=off"**, but i had no network connection even though i use a NIC, this problem was still present even after i rebooted and start ubuntu anynumber of times, i was absolutely puzzled.  the mouse and usb keyboard that were connected to the usb ports on the monitor were also extremely slowwwww.
3.  i then tried removed** "acpi=off"** and put **"irqpoll"** instead and the network card works :).

overall ubuntu is really buggy in terms of installation especially for new hardware, fedora does a good job at it, the live cd boots fine it installs fine aswell.  no configuration on my part what so eva, ubuntu needs to sort out this 8800 nvndia card issues asap.  But it doesn't have a community as user freindly as ubuntu.


thanks for your help

---

