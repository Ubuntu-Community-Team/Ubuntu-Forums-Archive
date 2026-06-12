---
title: "XP boot problems after installin Ubuntu 7.10"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by EuGis42 on 2008-04-05
Hi

I am a beginner when speaking about linux and i just can't understand why this is happening:

I have two disks, one of them has two ntfs partitions, one contains xp, the second one is for media... the second disk is ext3 - this is where i put my fresh ubuntu

when i try to boot xp the splash screen displays as expected, but it never exits from the splash to the OS itself... when running xp in safe mode, everything goes fine, the system boots up normally... any idea of what may be wrong? ( i know this is probably a windows problem, but it occured when i installed ubuntu ...)

Thanx!

---

### Post by Pumalite on 2008-04-05
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by EuGis42 on 2008-04-05
```
Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010001

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/hda2        40965750    80019764    19527007+   f  W95 Ext'd (LBA)
/dev/hda5        40965813    80019764    19526976    7  HPFS/NTFS

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0cd785d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   429835139   214917538+   6  FAT16
/dev/hdb2       429835140   625137344    97651102+  83  Linux
```


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
# kopt=root=UUID=b03add6d-368f-447e-a32e-35330a420573 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b03add6d-368f-447e-a32e-35330a420573 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b03add6d-368f-447e-a32e-35330a420573 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Pumalite on 2008-04-05
It looks OK. Try changing 'root' to 'rootnoverify' in your Windows entry.

---

### Post by EuGis42 on 2008-04-05
Soo.... how/where do i change it? (i am kinda confused right now LOL) ..and I don't wanna mess things up :)

---

### Post by Pumalite on 2008-04-05
Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Let's edit:
gksudo gedit /boot/grub/menu.lst
Here, change this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
To this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
rootnoverify           (hd0,0)
savedefault
makeactive
chainloader     +1

Save, exit, reboot.

---

### Post by EuGis42 on 2008-04-05
unfortunately, this does not work :( xp still "freezes" in the splash screen

---

### Post by Pumalite on 2008-04-05
Something might be wrong with Windows then. Your fdisk matches your menu.lst

---

### Post by EuGis42 on 2008-04-05
Okay .. thanks... only one more question... restoring my xp to an earlier state using the system restore WILL NOT TOTALLY DESTROY ubuntu... right? :)

thx for help :)

---

### Post by Pumalite on 2008-04-05
You can restore XP MBR with Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Or your Installation CD>Recovery>FIXMBR>FIXBOOT.
Later you can reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

