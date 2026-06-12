---
title: "Root file problem"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by Trututu on 2007-02-16
Hiho,
I have installed Ubuntu 6.06 LTS. Intallation proceeded with no problems.
After that, I have rebooted the PC, removed CD from CD-ROM. The boot manager appeard.
I have choosed first option (default) "Kernel something something". It was starting and then DANG! It stopped at "Check root file system" and it wasn't OK, so it went to the "Waiting for root file system..." My PC hang out :|
Anyone could help me? LIVE CD is working properly.

By the way, I've got Intel 2x2,8 and Windows XP installed.

---

### Post by taurus on 2007-02-16
Boot from the LiveCD and post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Trututu on 2007-02-18
Here it comes:

> Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2613    20988891    7  HPFS/NTFS
/dev/hde2            2614        7205    36885240    f  W95 Ext'd (LBA)
/dev/hde5            2614        5226    20988891    7  HPFS/NTFS
/dev/hde6            5227        6501    10241406   83  Linux
/dev/hde7            6502        6631     1044193+  82  Linux swap / Solaris

---

### Post by taurus on 2007-02-18
Need to see your menu.lst to see how you mount your root partition in there.

Applications  -> Accessories  -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hde6 /mnt/ubuntu
cat /mnt/ubuntu/boot/grub/menu.lst
```
Post the output of the last command here.

---

### Post by Trututu on 2007-02-18
An error:

> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hde6 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hde6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ cat /mnt/ubuntu/boot/grub/menu.lst


2 last lines from dmesg:

> [17179774.860000] VFS: Can't find ext3 filesystem on dev hde6.
[17179794.580000] VFS: Can't find ext3 filesystem on dev hde6.


Sorry, I think I deleted root partition after error in starting Ubuntu. I'm going to create it now, and I will publish text from that menu.lst

---

### Post by taurus on 2007-02-18
Which filesystem did you format /dev/hde6 to?

---

### Post by Trututu on 2007-02-18
OK, listen forget my earlier posts I made all wrong :P
Let's start again.

This is from sudo fdisk -l :
> 
Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2613    20988891    7  HPFS/NTFS
/dev/hde2            2614        5226    20988922+   f  W95 Ext'd (LBA)
/dev/hde3            7206        7842     5116702+  83  Linux
/dev/hde4            7843        7906      514080   82  Linux swap / Solaris
/dev/hde5            2614        5226    20988891    7  HPFS/NTFS


After that I made:
> sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hde3 /mnt/ubuntu
cat /mnt/ubuntu/boot/grub/menu.lst

And here is the output of it:
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
# kopt=root=/dev/hde3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hde3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hde3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Trututu on 2007-02-19
Oh I forgot to tell that my XP doesn't work - when I press XP HOME EDITION in boot manager it appears something like:

> title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

And here DANG! PC don't want work :/

---

