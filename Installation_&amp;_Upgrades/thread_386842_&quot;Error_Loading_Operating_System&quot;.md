---
title: "&quot;Error Loading Operating System&quot;"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by AstralRunner on 2007-03-17
I've tried installing Ubuntu 6.10 using both the Live CD and the Alternate CD, with the exact same results. I have some experience with PCs, but none with any form of GNU/Linux.

I'm trying to create a duel-boot machine with WindowsXP and Ubuntu. I have 3 hard-drives, two NTSF with WindowsXP installed on one, and another on which I wish to install Ubuntu. So I set the boot order in BIOS as, "Floppy, CD, soon-to-be-Linux-drive, WinXP drive."

I then boot from the install CD, and erase the third hard-drive. I create a 512 MB swap partition, and leave the rest as ext3. In the installer, I set the ext3 partition as the root mount, and the second hard-drive and the WinXP hard-drive as /media drives. When asked if I want to install GRUB into the MBR of the first hard-drive, I say Yes. It finishes installing, the computer restarts, BIOS loads, and the I just get a blank screen with, "Error Loading Operating System" and a blinking cursor at the top.

If I set the WinXP drive earlier in the boot order, it starts up as normal.

Any help with this would be greatly appreciated!

---

### Post by bulldog on 2007-03-17
The question in this is,on which disk is GRUB installed.
Just changing the boot order in the BIOS isn't enough to convince ubuntu that the drive you're installing on,is the first hdd.

If you have the time,try to boot from each hdd and see if you meet GRUB some where.
Another possibility is to boot from the live cd and open a terminal and type```
 cat /boot/grub/device.map
``` to see how ubuntu is ordering your hdd's.

It's important to know if you have SATA and IDE disks or just one of them.

---

### Post by AstralRunner on 2007-03-17
I've since made some progress. I erased my GNU/Linux drive and installed from the Alternate CD. When it asked about GRUB, I said "No" and set the install path manually. I specified /dev/sdb1 , which is the / partition of the Ubuntu drive. After restarting, I was presented with a list of operating systems!

However, when I selected the regular Ubuntu option, it then gave me, "Error 17: Cannot mount selected partition." When I selected WinXP, it booted up properly. Even Ubuntu is telling me I should just stick with Windows...

So, I guess I'm getting closer.

---

### Post by bulldog on 2007-03-17
If windows was booting like it should,you have GRUB on the windows disk.
To be sure,just boot the live cd and put the output of the following commands on this forum.
I or someone else can tell you what's going wrong.

```
sudo fdisk-l
```
For the next commands you need to mount your ubuntu partition,
```
sudo mkdir /mnt/rescue
sudo mount /dev/sdb1 /mnt/rescue
cat /mnt/rescue/boot/grub/device.map
cat /mnt/rescue/boot/grub/menu.lst
cat /mnt/rescue/etc/fstab
```

---

### Post by AstralRunner on 2007-03-17
ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9557    76766571   83  Linux
/dev/sdb2            9558        9964     3269227+   5  Extended
/dev/sdb5            9558        9964     3269196   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 1014 MB, 1014497280 bytes
17 heads, 32 sectors/track, 3642 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3643      990703+   6  FAT16


root@ubuntu:~# mkdir /mnt/rescue
root@ubuntu:~# mount /dev/sdb1 /mnt/rescue


root@ubuntu:~# cat /mnt/rescue/boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd



root@ubuntu:~# cat /mnt/rescue/boot/grub/menu.lst
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
timeout         20

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
# kopt=root=UUID=baca203a-f6eb-4fb2-80f4-4cec5f57c8a7 ro
# kopt_2_6=root=/dev/sdb1 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

root@ubuntu:~# cat /mnt/rescue/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=baca203a-f6eb-4fb2-80f4-4cec5f57c8a7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9136a83b-1ee7-44ad-a3ea-56eafd42862f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0






Note: sdc is the WinXP drive.

---

### Post by skirsman on 2007-03-24
I've the same ERROR

But I'm very new and I've no idea what to do.....

I've 2 SATA disc, I'm sure the installation was made in the booting disc, but after the computer start up i receive the same error......

Please help, I wanna leave WXP

SK

---

### Post by tbresson on 2008-02-15
I fixed my problem.

I loaded the LIVE CD and followed the directions on installing GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

In my case:
sudo grub
find /boot/grub/stage1
root (hd4,0)
setup (hd0)
quit

---

