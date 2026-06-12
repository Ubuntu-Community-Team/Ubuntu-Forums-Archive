---
title: "Ubuntu won't load"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by ThumbBumpkins on 2007-12-15
Hey all, I just installed Ubuntu on my system for the first time after a several month break, and I downloaded, burned and ran Ubuntu 7.10 without a hitch. However, after the installation, GRUB failed to appear and instead Windows XP booted up directly. After some tinkering I have managed to get GRUB to load. However, when I select Ubuntu, I get error 22 (I think): Partition does not exist. Windows loads completely correctly.

Even more mysterious, when I try to open /boot/grub/menu.lst in either gedit or kate, it is completely blank.

Both Windows and Ubuntu are installed on the same SATA drive.

/dev/sda1 = NTFS, my Windows partition
/dev/sda2 = ext3, Linux root partition
/dev/sda3 = swap for Linux

Any help at all would be very much appreciated, I'm eager to jump back into Ubuntu.

My Ubuntu install is brand new, so I could repartition/reformat/reinstall as necessary. However, I would really, really like to avoid reinstalling windows or deleting that partition.

---

### Post by Pumalite on 2007-12-15
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Blank menu.lst smells to me like a bad install.

---

### Post by ThumbBumpkins on 2007-12-15
I have reinstalled several times off two different discs with a variety of partition configurations, as well as just uninstalling and reinstalling grub in various wats, and the problem persists. I thought maybe having Windows on my first partition was the problem, but I have no idea. Any other thoughts?

---

### Post by Pumalite on 2007-12-15
Laptop or desktop? Specs would help. If you can boot a Live CD, post:
sudo fdisk -lu

---

### Post by ThumbBumpkins on 2007-12-16
It's a desktop, one that ran linux without a problem for months before. I have not changed the hardware even slightly since then.


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97659134    48829536    7  HPFS/NTFS
/dev/sda2        97659135   156826529    29583697+  83  Linux
/dev/sda3       156826530   160826714     2000092+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2be24c15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   398267414   199133676    7  HPFS/NTFS

---

### Post by Pumalite on 2007-12-16
From Live CD at the Terminal:
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
From that partition: 
cat /boot/grub/menu.lst

---

### Post by ThumbBumpkins on 2007-12-16
How do I change which partition I am in? Sorry, I am not a terribly experienced Linux user.

---

### Post by ThumbBumpkins on 2007-12-16
Nevermind, I figured it out.

root@ubuntu:/# sudo cat /boot/grub/menu.lst
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
# kopt=root=UUID=eb17fb84-1452-42f6-b946-e2330cc23952 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eb17fb84-1452-42f6-b946-e2330cc23952 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eb17fb84-1452-42f6-b946-e2330cc23952 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by Pumalite on 2007-12-16
Try reinstalling Grub with this 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

