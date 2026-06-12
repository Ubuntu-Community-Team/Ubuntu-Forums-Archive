---
title: "init probleme"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by sslizz on 2007-05-17
hi
yesterday,after i reboot ubuntu it  gives me:
[[img]http://img410.imageshack.us/img410/8199/dsc00094kf3.th.jpg[/img]](http://img410.imageshack.us/my.php?image=dsc00094kf3.jpg)
but if i chose the "i686" option in grub it gives me:
[[img]http://img515.imageshack.us/img515/4571/dsc00095ln1.th.jpg[/img]](http://img515.imageshack.us/my.php?image=dsc00095ln1.jpg)
so now after copying th init from the lives cd to the hdd it gives:
[[img]http://img216.imageshack.us/img216/3764/dsc00099rp3.th.jpg[/img]](http://img216.imageshack.us/my.php?image=dsc00099rp3.jpg)

my mon menu.lst
```
Code:
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=108e2ea5-3f80-4591-a08f-f1a718317cdf ro

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
# defoptions=quiet splash rootflags=data=writeback

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
# altoptions=(recovery mode) single rootflags=data=writeback

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

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=108e2ea5-3f80-4591-a08f-f1a718317cdf ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=108e2ea5-3f80-4591-a08f-f1a718317cdf ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, kernel 2.6.12-10-686-smp
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-10-686-smp root=UUID=108e2ea5-3f80-4591-a08f-f1a718317cdf ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-686-smp
quiet
savedefault

title        Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-10-686-smp root=UUID=108e2ea5-3f80-4591-a08f-f1a718317cdf ro single 
initrd        /boot/initrd.img-2.6.12-10-686-smp

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professionnel
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```
my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=108e2ea5-3f80-4591-a08f-f1a718317cdf /               ext3    defaults,errors=remount-ro 0 1
# /dev/sda1
# /dev/sda3
UUID=dda002a6-b8a1-4c95-98b5-c44887072559 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Generated by Automatix
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions
```
ls -l /dev/disk/by-uuid
```
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-06-07 21:50 108e2ea5-3f80-4591-a08f-f1a718317cdf -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-06-07 21:50 1E44A9FF44A9D9B3 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-07 21:50 dda002a6-b8a1-4c95-98b5-c44887072559 -> ../../sda3
```
fdisk -l
```
Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        1206     9687163+   7  HPFS/NTFS
/dev/sda2            1207        2457    10048657+  83  Linux
/dev/sda3            2458        2482      200812+  82  Linux swap / Solaris
```
i tried  to boot whit dev/sda2 or using irqpoll dosn't change nothing.help me pleas.
sorry for my bad english.

---

### Post by sslizz on 2007-05-17
heeeeeeelp

---

### Post by IgnorantGuru on 2007-05-17
Maybe this thread will be of help...
[http://ubuntuforums.org/showthread.php?t=292533](http://ubuntuforums.org/showthread.php?t=292533)

---

