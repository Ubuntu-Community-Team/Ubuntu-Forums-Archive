---
title: "Cant boot up windows"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by John T on 2007-02-06
I recently installed Ubuntu from the live CD onto my windows xp laptop. After rebooting post-instalation, I could not get back into windows. I tried changing my menu.lst info to no avail. I get a "missing kernel" error or something to that affect. any ideas?
Thanks

---

### Post by logos34 on 2007-02-06
Post the output from these commands:
> sudo fdisk -l 
cat /boot/grub/menu.lst

---

### Post by John T on 2007-02-06
> **logos34 said:**
> Post the output from these commands:

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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda5 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS

title        Microsoft Windows XP
root        (hd0,3)
makeactive
chainloader    +1

(makes no difference if it is rootnoverify)

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        6592    52902045    7  HPFS/NTFS
/dev/sda3   *        9154        9545     3148740   db  CP/M / CTOS / ...
/dev/sda4            6593        9153    20571232+   5  Extended
/dev/sda5            6593        6981     3124611   83  Linux
/dev/sda6            6982        8958    15880221   83  Linux
/dev/sda7            8959        9153     1566306   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by logos34 on 2007-02-06
> # This entry automatically added by the Debian installer for a non-linux OS

title Microsoft Windows XP
**root (hd0,3)**
makeactive
chainloader +1

(makes no difference if it is rootnoverify)

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 7 6592 52902045 7 HPFS/NTFS
/dev/sda3 * 9154 9545 3148740 db CP/M / CTOS / ...
**/dev/sda4 6593 9153 20571232+ 5 Extended**
/dev/sda5 6593 6981 3124611 83 Linux
/dev/sda6 6982 8958 15880221 83 Linux
/dev/sda7 8959 9153 1566306 82 Linux swap / Solaris

Partition table entries are not in disk order

The root line is pointing to the wrong partition (your extended).  Should be sda2 or sda3

try 
> root (hd0,1)
or
> root (hd0,2)

---

### Post by John T on 2007-02-06
it makes no difference if it is (hd 0,1) or (hd 0,2) or (hd 0,3)

---

### Post by logos34 on 2007-02-06
Your windows sys files are sda2, so it should work with hda0,1.  See here's mine (with sys files on hda1:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP Professional x64 Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

xxxxx@xxxx-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1019     8185086    7  HPFS/NTFS
/dev/hda2            1020       10912    79465522+   f  W95 Ext'd (LBA)
/dev/hda3           10913       11039     1020127+  82  Linux swap / Solaris
/dev/hda4           11040       12188     9229342+  83  Linux
/dev/hda5            1020       10912    79465491    7  HPFS/NTFS

---

### Post by logos34 on 2007-02-06
Is windows sda2 mounting in linux and if so can you access your files?

---

### Post by John T on 2007-02-06
It is mounting but no files are visible

---

### Post by logos34 on 2007-02-06
I do know that when you resize windows partition for ubunut install, the first thing windows does when you reboot into it is run checkdisk.  So maybe that's part of the problem, dunno.

---

### Post by logos34 on 2007-02-06
Let me run my systemrescuecd on my pc to see what all it can do.  It's supposed to have file system tools for win like ntfsprogs for NTFS, dostools, etc.

---

### Post by logos34 on 2007-02-07
I would suggest you run a filesystem check of your ntfs partition.  The Gparted that's on the Ubuntu livecd does not have that feature, nor does the Gnome Partition Editor on the desktop.  You need to download the Gparted livecd or SystemRescueCD.  Just right-click on the ntfs parition and select "Check"and apply.  Here's what Herman has to say:
> you can initiate a filesystem check by right-clicking a partition, and selecting 'check' from the right-click menu, then click 'Apply'.
When the operation is finished you should click the '> Details' and then the 'Check and Repair' line, which expands into three subsequent lines.
These are, 'calibrate', 'check filesystem for errors and (if possible) fix them', and 'grow filesystem to fill partition'.
When you click on each of these you get more details of what has been done.
The middle line, 'check filesystem for errors and (if possible) fix them', when clicked, tells you the command GParted LiveCD used for the check, and when you click on the line describing the command, it expands into a full report on the state of your filesystem, which is super cool! 
[http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check](http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check)

See if that does anything.  Hopefully it will at least make your windows files accessible in linux if it doesn't make windows bootable.

---

