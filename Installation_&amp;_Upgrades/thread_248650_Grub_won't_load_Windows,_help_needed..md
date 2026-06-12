---
title: "Grub won't load Windows, help needed."
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by squeegeeboy on 2006-09-01
Howdy all. I found myself in a nerdy mood yesterday so I thought I'd try and see if I could dualboot XP/Ubuntu. I partitioned using Gparted and put Ubuntu on the same drive as my Windows install. The Ubuntu install went fine and I'm using it as we speak, however, since installing Ubuntu, grub is not able to load Windows, when trying to do so I get the following:

Booting 'Windows NT/2000/XP (loader)'

root (hd0,0)
Filesystem type unknown, partition type 0x7
save default
makeactive
chainloader +1

I read a few threads regarding this topic but haven't been able to resolve my issue. Initially I tried to restore the MBR using my XP disc but that didn't seem to work, When I tried to boot windows after restoring the MBR my computer would continuously restart when getting to the point where Windows would normally start booting up. 

Here are the contents of /boot/grub/menu.lst
--------------------------------------------

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


And here are the results of cat /etc/fstab
------------------------------------------


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hde1       /media/hde1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdf1       /media/hdf1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0



And finally, here is what sudo fdisk -l shows.
----------------------------------------------

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2559    20555136    7  HPFS/NTFS
/dev/hda2            2560        3398     6739267+  83  Linux
/dev/hda3            3399        3659     2096482+  82  Linux swap / Solaris
/dev/hda4            3660        4865     9687195   83  Linux

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081   42  SFS

Disk /dev/hde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       14593   117218241   42  SFS

Disk /dev/hdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1        4865    39078081    7  HPFS/NTFS


After reading all of the threads regarding this problem it seems that the problem is not necessarily with my Windows partition but with Grub and the fact that it doesn't recognize my NTFS partition. At this point I'm not entirely sure what to try next, it seemed that restoring the MBR worked for some but it didn't seem to be the solution for me, thoughts?

---

### Post by galileon on 2006-09-01
hello, grub itself cant read ntfs, and it might even be illegal to do so in many places...:(

what you need here is to chainload, but you need to tell grub not to check anything inside the partition.

try to add the following line at the end of your menu.lst

title windoze
rootnoverify (hd0,0)
chainloader +1


got the hint from here btw [http://www.unix.com/archive/index.php/t-12636.html](http://www.unix.com/archive/index.php/t-12636.html)

let us know if it works!

---

### Post by squeegeeboy on 2006-09-01
Okey dokey, here's what I originally got when trying to load windows: 

Booting 'Windows NT/2000/XP (loader)'

root (hd0,0)
Filesystem type unknown, partition type 0x7
save default
makeactive
chainloader +1

After adding "noverify" to root here's what I get now.

Booting 'Windows NT/2000/XP (loader)'

rootnoverify (hd0,0)
save default
makeactive
chainloader +1

So, that seems to have gotten rid of the 'Filesystem type unknown, partition type 0x7' error, however it still didn't start booting windows it just sat there displaying the above information. Any other suggestions?

---

### Post by galileon on 2006-09-01
i think you might not need to have the bits for 
save default
makeactive
(i dont think you need them here), but the one i saw in the link was more like

title windoze
rootnoverify (hd0,0)
chainloader +1

but are you sure your windows partition is still alive? because it seemed to me you did something to it with the dd..have you checked thru a live cd?

btw if you want a windows MBR, find a win98 cd, boot on it, do a fdisk /mbr

i dunno how its done on xp tho

---

### Post by squeegeeboy on 2006-09-01
Mmmkay, took "make active", and "save default" out and that didn't work either. Now it shows:

Booting 'Windows NT/2000/XP (loader)'

rootnoverify (hd0,0)
chainloader +1

As far as windows being active, are you referring to the actual partition that windows is taking up or wondering if all the windows files are still there? I can browse through my windows directory and all that so nothing was lost as far as I can tell. 

I don't have any live cd's around, how might I check to see if the windows partition is still good to go?

---

