---
title: "help with dual boot - vista, ubuntu 7.10"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by jimbo650 on 2007-12-16
I  have a dual boot that works but the Ubuntu has taken over 2 of my 3 hard drives. I was using one (sata 80gig) as a backup for my Vista (500 gig sata_. I want to get that drive back to use under Vista and confine the operation of ubuntu to just one 80 gig stat dirve.

I have seen other posts and can not figure out what to do. I am incuding the material others have requested. See below:

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7230c9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b6b147e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9324    74894998+  83  Linux
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3201b04d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7988    64163578+   7  HPFS/NTFS
/dev/sdc2            7989       60801   424220422+   5  Extended
/dev/sdc5            7989       55388   380740468+   7  HPFS/NTFS
/dev/sdc6           55389       60801    43479891   bc  Unknown

Disk /dev/sdf: 998 MB, 998768640 bytes
20 heads, 51 sectors/track, 1912 cylinders
Units = cylinders of 1020 * 512 = 522240 bytes
Disk identifier: 0xe5756a7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1913      975295+   6  FAT16
jim@multimedia:~$                    


cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
jim@multimedia:~$      


cat /boot/grub/menu.lst
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
# kopt=root=UUID=9d8c4574-4738-49ff-990b-c95e9292bae7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9d8c4574-4738-49ff-990b-c95e9292bae7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9d8c4574-4738-49ff-990b-c95e9292bae7 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=17373257-901b-41fc-880b-ad2a2b2915e7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=17373257-901b-41fc-880b-ad2a2b2915e7 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Windows Vista/Longhorn (loader)
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

jim@multimedia:~$

---

### Post by logos34 on 2007-12-16
> **jimbo650 said:**
> I  have a dual boot that works but the Ubuntu has taken over 2 of my 3 hard drives. I was using one (sata 80gig) as a backup for my Vista (500 gig sata_. I want to get that drive back to use under Vista and confine the operation of ubuntu to just one 80 gig stat dirve.

All you have to do is delete all the partitions on sdb.  (unmount sdb1 first).  Then make one big ntfs partition.

sudo gparted

Remember to delete the fstab entry for sdb1 (or change it to whatever new filesystem you made) before you reboot:

gksudo gedit /etc/fstab

I assume you have ntfs-config already.

---

### Post by jimbo650 on 2007-12-17
I am new to Ubuntu, only about a week into this. I do not understand your last sentence:

' I assume you have ntfs-config already."

thanks for your help.

Jim

---

### Post by logos34 on 2007-12-17
ntfs-config will edit /etc/fstab so that you can not only read but write to your windows partitions.  ubuntu 7.10 gutsy comes preinstalled with the ntfs-3g driver that makes this feature possible, but you have to configure your drives to mount with it.  ntfs-config does it for you:

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support internal drives

---

### Post by jimbo650 on 2007-12-18
1 more thing, while I have your help. I do not understand this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Windows Vista/Longhorn (loader)
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

what are the 2 'map' lines? are they doing anything? they just seem to go back and forth!

---

### Post by logos34 on 2007-12-18
> **jimbo650 said:**
> what are the 2 'map' lines? are they doing anything? they just seem to go back and forth!

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)
[http://www.users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://www.users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by louieb on 2007-12-18
> **jimbo650 said:**
> ...what are the 2 'map' lines? are they doing anything? they just seem to go back and forth,,, 
They are there to fake Vista -  to think that its installed on the 1st hard drive.
Might spend a while on Herman's Dual Boot site.

---

### Post by jimbo650 on 2007-12-18
Thanks Y'all :ks

---

