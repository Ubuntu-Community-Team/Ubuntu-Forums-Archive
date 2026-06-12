---
title: "Help, more grub problems"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by mkquist on 2006-08-21
Hi, Installed, successfully Ubuntu on my main machine (newer), dual boot w/XP.  Tried to do same w/second older machine.  Two 250g Hard drives.  Had it running by having XP on hda and Ubuntu on hdb.  Messed up installing though and misstyped the username.  Went through a bit to figure it out.  Before I did I tried to add a user spelled the way I wanted.  Tried to change ownership to the new user.  That didn't work.  So chowned the old user back to its own home folder, but things never quite worked right.  So - reinstalled Ubuntu and now...  Grub errors 15,17 or 18.
  Tried reinstalling w/root as first partition (was second partition) Hdb - grub error.  Tried to install on hda second partition, grub error.  I don't know what to do... ran once. ](*,)   Really want to get it back, but right.  Any thoughts?  BTW Super Grub disc didn't fix this...

Thanx in advance.
 
boot/grub/menu.lst:
 
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
# kopt=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb2.
title		Ubuntu, memtest86+ (on /dev/hdb2)
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

fstab:
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hdb2       /media/hdb2     ext3    defaults        0       2
/dev/hdb3       /media/hdb3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

fdisk -l:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612        5222    20972857+  83  Linux
/dev/hda3            5223        5483     2096482+  82  Linux swap / Solaris
/dev/hda4            5484       30401   200153835   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         131     1052226   82  Linux swap / Solaris
/dev/hdb2             132        5353    41945715   83  Linux
/dev/hdb3            5354       30401   201198060    7  HPFS/NTFS

---

### Post by peabody on 2006-08-21
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

According to this error 15 means it can't find the kernel image, error 17 means it can't recognize the filesystem (suspicious that one, seems like it's looking at the ntfs partition) and 18 says the bios can't see the partition.

what are the contents /boot/grub/device.map?

According to your fstab, your root is /dev/hda2, swap is /dev/hda3.  You should probably be booting with the first grub entry.  What error are you getting with that one?

---

### Post by mkquist on 2006-08-21
After many attempted installs over the last two days, I've found that Windows is now corrupted. Soooo, I tried just installing Ubuntu and another error, i think 15. This after wiping out Windows.  So now I'm reinstalling Windows, and I'll try Acronis boot manager and see if that works.  Guess grub just dont like this old machine. :-k

---

### Post by sacater on 2006-08-21
i had this problem,, i had xp installed on hda and ubuntu on hdb2, i tinkered with ubuntu and lost it, anyway, after that grub gave me error 15, i think u have to have ubuntu installed for it to run and vv,

---

