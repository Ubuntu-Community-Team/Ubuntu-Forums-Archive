---
title: "Dual booting vista"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by LostLake on 2007-11-22
I just purchased a new ThinkPad with windows vista. I tried to install ubuntu 7.10 and everything is fine until I boot vista from GRUB. Ubuntu works great but when I boot vista I am taken to the lenovo recovery software. Where did I go wrong?

---

### Post by dward526 on 2007-11-22
For some reason, GRUB found your recovery partition but not the main vista partition.  What usually happens is you end up with two entries for Vista in GRUB (1 for Vista, 1 for recovery).  Attempt to reinstall GRUB and see if it picks up the other partition.

You will be able to tell if this works because you will see 2 Vista on GRUB - I suggest renaming one recovery once you sort it out.

Good luck, and let us know how it turns out.

---

### Post by rsambuca on 2007-11-22
Post the output of ```
cat /boot/grub/menu.lst
```and ```
sudo fdisk -l
```.  We should be able to quickly sort it out.

---

### Post by LostLake on 2007-11-22
:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=cd5d29b8-8c91-4858-9d76-0d12185fed2d ro

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd5d29b8-8c91-4858-9d76-0d12185fed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd5d29b8-8c91-4858-9d76-0d12185fed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by LostLake on 2007-11-22
sudo fdisk -l
[sudo] password for seth:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf21ac63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         925     7427072   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             925       10047    73274414+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10048       19069    72462600   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           19069       19457     3122280    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           19069       19457     3122248+  82  Linux swap / Solaris

---

### Post by rsambuca on 2007-11-22
From looking at your menu.lst, you can see two Vista entries.  The first one is your recovery partition, and the second one is the regular Vista.  Just choose the second "Windows Vista/Longhorn (loader)" on the Grub menu.  If you want, you can either delete the first one, or change the titles so you know the difference.

---

### Post by robbydek on 2007-11-22
When I repartitioned, with Ubuntu's partition software, my Windows Vista partition, I had to repair it with a Windows XP CD.  I can't find the online thread anymore, but basically you:
1) boot into repair mode (system repair) from the Windows XP CD.  Type anything in when it prompts you for a password (will do it 3 times)
2) reboot and choose the option to boot into safe mode it will load drivers and eventually restart (should take no more than a few minutes)
3) boot in Vista its fixed
(paraphrased from eatingorange's April 2007 post)
Here is the link if you want to visit that posting:
[http://ubuntuforums.org/showthread.php?p=2527751]("http://ubuntuforums.org/showthread.php?p=2527751")

---

### Post by LostLake on 2007-11-22
The second windows partition was the right one. How do I change the name if the partition in grub? Thanks for the advice.

---

### Post by rsambuca on 2007-11-22
You can edit the menu.lst file using the text editor program called 'gedit'.  In order to access this file with read and write privileges, you are required to use 'gksudo' first.```
gksudo gedit /boot/grub/menu.lst
```

You will want to edit the last line that starts:

 title Windows Vista/Longhorn (loader)

You can change the part after the word 'title' to whatever you want to appear on your grub menu screen.

Also, if you wish, you can just delete the entire entry for the recovery partition, since you probably don't want it in there anyways.  To do this, you would just delete the entire section including the lines

title...
root...
savedefault
makeactive
chainloader +1

---

