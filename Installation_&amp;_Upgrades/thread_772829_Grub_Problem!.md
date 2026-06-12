---
title: "Grub Problem!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by suba82 on 2008-04-28
Hi everyone! I have some problems with grub.
2 days ago I have changed grub with gfxboot but I had some problems with xp partition.
No boot for xp.
So I restored grub but I have the same problem.  When I chose Ubuntu partition everything is ok, when I chose the other one xp doesnt boot up, it reloads the grub without error.
This is my Fstab
```
filippo@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=f6c01541-6b6d-4f70-8515-99036b4e028a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=3885-7DC9  /media/sda1     vfat    utf8,umask=007,gid=46 0       0
# /dev/sda2
UUID=cc3ae1b0-f2ce-420f-a14f-c9a8a5344ff0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
filippo@ubuntu:~$ 
```
This is my menu.lst
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
# kopt=root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-15-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro single
#initrd		/boot/initrd.img-2.6.24-15-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-14-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro single
#initrd		/boot/initrd.img-2.6.24-14-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-12-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=f6c01541-6b6d-4f70-8515-99036b4e028a ro single
#initrd		/boot/initrd.img-2.6.24-12-generic

#title		Ubuntu hardy (development branch), memtest86+
#root		(hd0,3)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
another thing from Ubuntu I can see windows xp partition, I can open it read and write without problems but the mount point has this name : %3 so when I see the disk with nautilus I see this strange thing.
 [[IMG]http://img187.imagevenue.com/loc181/th_09474_index_122_181lo.jpg[/IMG]](http://img187.imagevenue.com/img.php?image=09474_index_122_181lo.jpg)

This is fdisk
```
filippo@ubuntu:~$ sudo fdisk -l
[sudo] password for filippo: 

Disco /dev/sda: 40.0 GB, 40007761920 byte
255 heads, 63 sectors/track, 4864 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11dc11db

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+   c  W95 FAT32 (LBA)
/dev/sda2            2491        2552      498015   82  Linux swap / Solaris
/dev/sda4            2553        4864    18571140   83  Linux
```

I tried to recover grub too without success
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,3)

grub> root (hd0,3)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,3)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
```

Last thing:
when I choose xp I can see this for a while

```
Booting Microsoft Windows Xp Home
root (hd0,0)
Filesystem type is fat, partition type 0xc
savedefault
makeactive
cainloader +1
Grub loading stage 2...
```
And then instead of bootin windows xp it reloads grub.
Sorry for my english .
Any help appreciated!

---

### Post by tormod on 2008-04-28
It can seem like you at some point have installed the grub MBR loader to the boot sector of your XP partition (hd0,0). So you might need to repair the XP boot sector using the XP installation CD. That will probably write an XP MBR loader to MBR (hd0) again, so you'll need to install grub to (hd0) afterwards.

---

### Post by suba82 on 2008-04-28
Thank you very much for your help tormod, probably you are right cause I did lot of things installing gfxboot with some errors.
Is this a good way to restore the xp boot sector?
[http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:](http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:)

I know this is a linux forum but I use xp just to flash my htc phone and other things and I cant understand lot of microsoft things.
Thank you very much!!! :)

---

### Post by tormod on 2008-04-29
Yes, exactly, just use the **fixboot** command in the XP recovery console.

---

