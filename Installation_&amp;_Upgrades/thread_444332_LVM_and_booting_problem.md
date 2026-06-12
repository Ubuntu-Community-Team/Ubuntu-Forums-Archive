---
title: "LVM and booting problem"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ©TriMoon® on 2007-05-15
Hi all,

Im having major problems instaling Kubuntu from the amd64-DVD the way i want it...
Im unable to boot my fresh installed system!

Let me start with the error im stuck at and after explain my setup.
When i boot i see vt8 and vt1 outputs below, and thats it...
I can't seem to get the system up :(

**My setup is:**
[list][*]CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
[*]Memory: 1GB RAM
[*]Video card: ATI Radeon 1650 pro
[*]Disks: 1xIDE, 1xSATA
[*]Partition table(s): See fdisk output and LVM setup below, /dev/sda1 is an ext3 partition mounted on /boot
[*]Bios boot: IDE-HD
[*]System is dual booting Kubuntu / Windows XP using GRUB.
[*]Install option choosen was: Setup server with all 3 extras (LAMP etc)
[/list]
I was able to set this all up and install kubuntu without any problems or errors, although the tea-breaks between LV setups is kinda BIG.

Anyone any ideas how to proceed tobe able to boot this system from HD?
---------------------------------------------------------------------------------------------------------------------------------
[vt8] output:```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) <promt is here>
```

[vt1] output:```
Loading, please wait...
kinit: name_to_dev_t(/dev/mapper/Linux-swap) = dm-1(254,1)
kinit: trying to resume from /dev/mapper/Linux-swap
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init


<following lines are at bottom of screen>
Kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000
```

Fdisk output:```
~ # fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks  Id  System
/dev/sda1               1           3       24066  83  Linux
/dev/sda2   *           4        6409    51456195   7  HPFS/NTFS
/dev/sda3            6410       19457   104808060  8e  Linux LVM

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks  Id  System
/dev/hda1               1       16709   134215011   7  HPFS/NTFS
~ #
```

LVM setup:
All LV's are ext3 and mounted on the obvious named mountpoints, except swap ofcourse which is a swap :D```
                    Current LVM Configuration:
Unallocated physical volumes:
  * none

Volume groups:
  * Linux                                               (107319MB)
    - Uses physical volume:          /dev/sda3          (107319MB)
    - Provides logical volume:       bin                (1073MB)
    - Provides logical volume:       home               (85895MB)
    - Provides logical volume:       lib                (4294MB)
    - Provides logical volume:       root               (104MB)
    - Provides logical volume:       sbin               (1073MB)
    - Provides logical volume:       swap               (8589MB)
    - Provides logical volume:       tmp                (524MB)
    - Provides logical volume:       usr                (4294MB)
    - Provides logical volume:       var                (419MB)
    - Provides logical volume:       var.log            (524MB)
    - Provides logical volume:       var.spool          (524MB)

```

---

### Post by mlind on 2007-05-15
I reckon you need/should have /boot outside of the LVM, as a normal (bootable) primary partition. At least this way I've always used to install Ubuntu. Other partitions are managed by LVM. How does your /boot/grub/menu.lst look like?

---

### Post by ©TriMoon® on 2007-05-17
> **mlind said:**
> I reckon you need/should have /boot outside of the LVM, as a normal (bootable) primary partition. At least this way I've always used to install Ubuntu. Other partitions are managed by LVM. How does your /boot/grub/menu.lst look like?

About the /boot
> **My setup is:**
[list][*]Partition table(s): See fdisk output and LVM setup below, /dev/sda1 is an ext3 partition mounted on /boot
[/list]

For the contents of the menu.lst ill get back and edit that into this reply when i boot into that machine again...

*edit*
```
root@ubuntu:/mnt/boot/grub# cat menu.lst
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
# kopt=root=/dev/mapper/Linux-root ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-server
root            (hd1,0)
kernel          /vmlinuz-2.6.20-15-server root=/dev/mapper/Linux-root ro quiet splash
initrd          /initrd.img-2.6.20-15-server
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-server (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.20-15-server root=/dev/mapper/Linux-root ro single
initrd          /initrd.img-2.6.20-15-server

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

root@ubuntu:/mnt/boot/grub#  

```

---

### Post by ©TriMoon® on 2007-05-20
Please see [this thread]("http://kubuntuforums.net/forums/index.php?topic=3083234.0") for a cross-post discussion on the Kubuntu-forums.
It seems the ubuntu installer cant handle multiple partitioned setups!

---

