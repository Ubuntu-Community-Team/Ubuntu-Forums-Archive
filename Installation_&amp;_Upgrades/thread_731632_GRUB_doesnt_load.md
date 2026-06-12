---
title: "GRUB doesnt load"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Evilmachine on 2008-03-22
Hi Guys,

i have got the following problem.

I had Ubuntu and Windows Vista on the same Computer.
Everything works finde but i wanted to overwrite Windows Vista with XP, cause Vista was very slow with Gaming and so one.

So i tried to install Windows XP. After the Blue Screen where the necassary files are copied is a reboot. After that neither Grub nor Windows startet. I just got the error Error in Operating System.

So i tried to fix Grub with the Super Grub Disk. I tried similar Options like Linix Automatic, Boot Linux directly, Fix Boot auf Linux (not in that order) but it just stops after trying.

Then i installed Grub to MBR with the Ubuntu Live CD and yes it starts. But when it starts it freezes at the Point "Grub Loading, please wait". 

So what can i do now??

Paste of fdisk -l and menu.lst are coming in a moment.

Paste of fdisk -l
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00df00df

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           3       77507    39062500    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           77521       81377     1943865   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/hda3           81377      158802    39021885   83  Linux
Partition 3 does not end on cylinder boundary.

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb51c8c87

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14595   117234306    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bf554f6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9730    78148608    7  HPFS/NTFS
```

Paste of menu.lst
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
default      0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout      10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,2)/boot/grub/splashimages/ubuntu-grub-fullcolor.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
##password --md5 $1$5PlfK$N0soPUYGazQR1REcMfDXG/#
# examples
#
# title      Windows 95/98/NT/2000
# root      (hd0,0)
# makeactive
# chainloader   +1
#
# title      Linux
# root      (hd0,1)
# kernel   /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2ae1f628-0933-4f46-bf44-714638990c0f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash locale=de_DE vga=789

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true

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

title      Ubuntu 7.10, kernel 2.6.22-14-generic
root      (hd0,2)
kernel      /boot/vmlinuz-2.6.22-14-generic root=UUID=2ae1f628-0933-4f46-bf44-714638990c0f ro splash locale=de_DE vga=789
initrd      /boot/initrd.img-2.6.22-14-generic
quiet

title      Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
lock
root      (hd0,2)
kernel      /boot/vmlinuz-2.6.22-14-generic root=UUID=2ae1f628-0933-4f46-bf44-714638990c0f ro single
initrd      /boot/initrd.img-2.6.22-14-generic

title      Ubuntu 7.10, memtest86+
root      (hd0,2)
kernel      /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title      Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title      Windows Vista/Longhorn (loader)
root      (hd0,0)
savedefault
makeactive
chainloader   +1
```

---

