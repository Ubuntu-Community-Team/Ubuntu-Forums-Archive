---
title: "Grub Issues, XP on raid0 and 7.10 on seperate drive"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by netviper8 on 2007-10-13
Hello Everyone,

This is my first post here. I've been searching around for a solution to my issue for several hours and haven't found exactly what I need yet. I'm running an Asus M2N-SLI motherboard,  with two 250gb sata drives in a raid0. I have Windows XP installed on the raid0. I also have a 160gb sata drive that I had been using as storage.

Last night I re-partitioned the 160gb drive and installed 7.10 on it. I believe it saw the raid array as two separate drives, and installed the grub bootloader on the first of the two. Upon reboot I was faced with a grub Error 21.

Realizing what had happened, I loaded my XP boot cd and ran a fixmbr. I rebooted and got Error 21 again.

Fearing that I'd lost all my data, I loaded the ubuntu cd, installed dmraid, and mounted my raid array to verify that my data was still there (it is).

My boot order is floppy, cd, raid0, and finally the 160gb drive. I've tried disabling the 160gb drive in BIOS and I still got the grub error which means it is indeed on one of the two drives in the array.

Now my main concern is removing grub from the drive it's on, and I can't seem to find a way to do that.

Here's what drives ubuntu shows:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdf0fdf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000063b0

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb59b68d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6079    48829536   83  Linux
/dev/sdc2            6080        7052     7815622+  82  Linux swap / Solaris
```

I guess it is also possible that grub is just misconfigured, so here's what it looks like right now:

```
root@ubuntu:/ubuntu/boot/grub# cat menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=717e96de-0d80-4096-bbce-3f6ca0161651 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
groot=(hd2,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=717e96de-0d80-4096-bbce-3f6ca0161651 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=717e96de-0d80-4096-bbce-3f6ca0161651 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1
```

Any suggestions?

As far as skill level, I work in Linux support for a major hosting company (mainly Redhat products) and am RHCE certified. I've just never run into this issue before :(

EDIT: This thread has some useful information: [http://ubuntuforums.org/showthread.php?t=159202](http://ubuntuforums.org/showthread.php?t=159202)
I would just need to get grub off of the raid array, onto the 160gb drive, and then change the boot order.

---

### Post by netviper8 on 2007-10-14
Still working on it, haven't figured it out yet :confused:

---

### Post by netviper8 on 2007-10-14
Hoping this might be helpful:

```
ubuntu@ubuntu:/ubuntu/boot/grub$ cat device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
```

*Bump for great justice*

---

### Post by netviper8 on 2007-10-14
Well after searching all over some more, I ended up just making an NTFS partition on my 160gb drive, backing everything up, and then reinstalling windows :)

So all is good I suppose.

---

