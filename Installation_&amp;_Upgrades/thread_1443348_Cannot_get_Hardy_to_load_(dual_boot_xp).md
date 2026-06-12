---
title: "Cannot get Hardy to load (dual boot xp)"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by SiouxerBrewer on 2010-03-31
I am running a dual boot system (XP and ubuntu).  I was able to run xp and feisty fawn without a problem but for some reason hardy won't load.  I get the "Error 22: No Such Partition" when trying to boot into Ubuntu.  I am able to boot into xp ok after reading this thread [http://http://ubuntuforums.org/archive/index.php/t-658350.html]("http://http://ubuntuforums.org/archive/index.php/t-658350.html")  I am however unable to get past starting into ubuntu.  Here are the results of sudo fdisk -lu```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000889bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   781417664   390708801    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7b5b7b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sdb2        51199155    92164904    20482875   83  Linux
/dev/sdb3        92164905    97289639     2562367+  82  Linux swap / Solaris
/dev/sdb4        97289640   156296384    29503372+   7  HPFS/NTFS

```
Here is my menu list:
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
# kopt=root=UUID=b0d21944-c171-4744-82a9-e332f7692caf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=quiet splash pci=nomsi

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=b0d21944-c171-4744-82a9-e332f7692caf ro quiet splash pci=nomsi
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=b0d21944-c171-4744-82a9-e332f7692caf ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
makeactive
savedefault
chainloader	+1

```
I have followed the steps of recovering GRUB after reinstalling windows [http://https://help.ubuntu.com/community/WindowsDualBoot]("http://https://help.ubuntu.com/community/WindowsDualBoot") and that is not working.  Thank you for your consideration.

---

### Post by SiouxerBrewer on 2010-03-31
Turns out it was a setting in my Bios, I had to change the HDD boot order just in case anybody else is having this problem (dual boot with two HDD).  I would have thought that mapping GRUB would have solved this problem but the bios setting was also needed.

---

