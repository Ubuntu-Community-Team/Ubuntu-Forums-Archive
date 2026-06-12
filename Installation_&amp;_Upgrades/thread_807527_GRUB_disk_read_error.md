---
title: "GRUB disk read error"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by niglch on 2008-05-25
Ever since I upgraded Ubuntu 8.04, I have not been able to access Windows. When I select it in Grub, I get a message after "starting up..." saying
[FONT="Courier New"]A disk read error occurred
Press Alt+Ctrl+Del to restart[/FONT]
However, I have no problem accessing my windows partition from Ubuntu. Also, when I try to access the recovery partition for windows, GRUB simply hangs at "starting up..." so I can't even restore the MBR (my computer did not come with a recovery CD). Any help would be appreciated.

---

### Post by iaculallad on 2008-05-25
> **niglch said:**
> Ever since I upgraded Ubuntu 8.04, I have not been able to access Windows. When I select it in Grub, I get a message after "starting up..." saying
[FONT="Courier New"]A disk read error occurred
Press Alt+Ctrl+Del to restart[/FONT]
However, I have no problem accessing my windows partition from Ubuntu. Also, when I try to access the recovery partition for windows, GRUB simply hangs at "starting up..." so I can't even restore the MBR (my computer did not come with a recovery CD). Any help would be appreciated.

Post us your /boot/grub/menu.lst

Code:

> cat /boot/grub/menu.lst

and the result of fdisk -l (Small letter L)

Code:

> sudo fdisk -l

---

### Post by Pumalite on 2008-05-25
Post:
cat /boot/grub/menu.lst

---

### Post by niglch on 2008-05-26
Here's the menu.lst output:
```
nick@nick-desktop:~$ cat /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color white/blue

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
# kopt=root=UUID=9c40f2eb-b955-4ea3-abc2-632c338ec3b7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c40f2eb-b955-4ea3-abc2-632c338ec3b7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c40f2eb-b955-4ea3-abc2-632c338ec3b7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Recovery Partition
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
And here's the output from fdisk:
```
nick@nick-desktop:~$ sudo fdisk -l
[sudo] password for nick: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000a5ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19225   154424781   83  Linux
/dev/sda2           19226       19457     1863540    5  Extended
/dev/sda5           19226       19457     1863508+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
240 heads, 63 sectors/track, 5174 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xbce1bce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         697     5269288+   b  W95 FAT32
/dev/sdb2   *         698        5174    33846120    7  HPFS/NTFS

```

---

### Post by Pumalite on 2008-05-26
Try changing the boot order of your drives in BIOS. Then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by meierfra. on 2008-05-26
Before you try Pumalite suggestion, remove the four "map ...." lines in menu.lst and see whether that solves your problem. The map lines are  definitely wrong.

---

