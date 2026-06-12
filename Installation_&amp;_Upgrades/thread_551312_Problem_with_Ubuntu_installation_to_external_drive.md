---
title: "Problem with Ubuntu installation to external drive"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by jbsabre on 2007-09-15
So I have a somewhat unusual (idiotic on my part) problem with my Ubuntu load to my external hard drive.  I had already installed Kubuntu (dual boot with XP) to my desktop computer.  I wanted to install Ubuntu to my external drive for use with my laptop.  I had problems loading the live disc with my laptop because apparently Ubuntu has issues with Radion Xseries graphics drivers, so I decided to do the install from my desktop to the external drive.  I followed the directions on this forum, but unfortunately (due to my inability to do anything right) I completely missed the part where I shouldn't load the grub to my desktop hard drive.

Now when I boot up my desktop, where it would previously auto-load to windows unless I picked Kubuntu from the boot menu, I get a grub error if my external drive is not plugged in.  If the external drive is plugged in it puts Windows XP and Kubuntu in the 'Other OS' category.  I would like to know how to remove the Ubuntu portion altogether and go back to the dual boot for XP and Kubuntu on my desktop.  I should be able to figure out how to make my desktop recognize the external without a problem. 

sda is my windows xp/ kubuntu dual boot drive.

sdf is the external drive.

please let me know if I missed anything.


menu.lst:
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf7d4865-16f6-4508-86a0-ec16c81bf6d1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf7d4865-16f6-4508-86a0-ec16c81bf6d1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu, memtest86+ (on /dev/sda4)
root		(hd0,3)
kernel		/boot/memtest86+.bin  
savedefault
boot




fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdf1
UUID=cf7d4865-16f6-4508-86a0-ec16c81bf6d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=64D372C45B4FA17A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4B6E-6BC0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e0f4e656-c92f-4757-b3f3-09fb31f70ece /media/sda4     ext3    defaults        0       2
# /dev/sda6
UUID=4601-825B  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdf6
UUID=8DD6-0EEE  /media/sdf6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=5a8ff90f-7633-4b8d-841d-e738a3b47480 none            swap    sw              0       0
# /dev/sdf5
UUID=22eb080d-b2ed-40a4-8cca-668f19e6c859 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



fdisk -l:

Disk /dev/sdc: 128 MB, 128450560 bytes
8 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         979      125296    6  FAT16

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        1952    15679408+  83  Linux
/dev/sdf2            1953        9729    62468752+   f  W95 Ext'd (LBA)
/dev/sdf5            1953        2214     2104483+  82  Linux swap / Solaris
/dev/sdf6            2215        9729    60364206    b  W95 FAT32

Disk /dev/sdg: 32 MB, 32768000 bytes
2 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by logos34 on 2007-09-15
Boot into kubuntu install.  Reinstall grub to both drives.

[B]sudo grub 
find /boot/grub/stage1[/B]

It should return two locations:
**(hd0,3)**-->kubuntu
**(hd2,0)**-->ubuntu

[B]root (hd0,3)
setup (hd0)[/B]-->writes grub to desktop/internal drive mbr
**quit**

Now write grub to the mbr of the external usb drive:

[B]sudo grub 
root (hd2,0)
setup (hd2)
quit[/B]

Add an entry to the bottom of your kubuntu menu.lst for ubuntu installation on the usb drive:
[B]
gksudo gedit /boot/grub/menu.lst[/B]

> title Ubuntu, kernel 2.6.20-15-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=cf7d4865-16f6-4508-86a0-ec16c81bf6d1 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

You can allow the system to automount external partition in kubuntu (at 'media/disk', etc) or add an entry to kubuntu fstab:

**gksudo gedit /etc/fstab**

> # /dev/sdf1
UUID=cf7d4865-16f6-4508-86a0-ec16c81bf6d1 /media/sdf1 ext3 defaults 0 0

Create mount point:

**sudo mkdir /media/sdf1**

*or use anything you like in place of 'sdf1', like 'external,' 'ubuntu', etc.

Using [volume labels for USB]("http://ubuntuforums.org/showthread.php?t=139535") is another option (e2label or tune2fs).

Now you should be able to boot your desktop without the usb hard disk attached, and boot into ubuntu when connected to the laptop by changing the Bios boot order so the USB is first.

---

