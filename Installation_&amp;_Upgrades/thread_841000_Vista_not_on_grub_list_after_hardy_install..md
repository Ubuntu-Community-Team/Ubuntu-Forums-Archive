---
title: "Vista not on grub list after hardy install."
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by drews_blunted on 2008-06-25
I just did a fresh install of ubuntu hardy heron and previous installs had detected and showed my windows vista install on my /dev/sde1 This time however it didnt detect it and it is not showing up. I am curious if there is a way to edit my grub to alow me to boot back into my windows install.

Here is a "fdisk -l"


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c356f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50255025

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000053f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9575

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       35724   286952998+  83  Linux
/dev/sdd2           35725       36481     6080602+   5  Extended
/dev/sdd5           35725       36481     6080571   82  Linux swap / Solaris

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001    c  W95 FAT32 (LBA)

^^ My windows Vista HD

Here is my Menu.lst in grub.

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=cbdb7eef-02ea-4775-8d2a-fb523bf90d3d ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cbdb7eef-02ea-4775-8d2a-fb523bf90d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cbdb7eef-02ea-4775-8d2a-fb523bf90d3d ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cbdb7eef-02ea-4775-8d2a-fb523bf90d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cbdb7eef-02ea-4775-8d2a-fb523bf90d3d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Linux Mint, kernel 2.6.22-14-generic (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Linux Mint, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdd1 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Linux Mint, kernel 2.6.20-16-generic (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sdd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Linux Mint, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sdd1 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Linux Mint, kernel memtest86+ (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


Does anyone know what i need to be adding to my Grub to make vista load again! Thanks.

---

### Post by logos34 on 2008-06-26
try 
> 
title        Windows Vista
root        (hd4,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader    +1verify hard disk order in /boot/grub/device.map

> dev/sde1               1       91201   732572001    **c  W95 FAT32 (LBA)**why did you put vista on a fat32?  

Actually, that entry should have a boot (*) flag on it like this:

> dev/sde1               [COLOR=Red]*****[/COLOR] 1       91201   732572001    c  W95 FAT32 (LBA)you can toggle the boot flag with **sudo cfdisk /dev/sde**.  Or use Gparted (right-click on sde1>manage flags>'boot').

but the 'makeactive' command in the vista entry above should make it bootable

---

### Post by drews_blunted on 2008-06-27
i installled fat32 because i thought it would be easyest to read/write from linux.

---

### Post by logos34 on 2008-06-27
that used to be true, but not anymore as Hardy comes with out-of-the-box ntfs read-write support (ntfs-3g), and there's fs-driver for windows to access ext3 linux filesytem should you prefer that route.  So there's really no reason left to use fat32 (which is less secure, defrags more easily and has a file size limit of 4 GB)

Well, did you try the windows entry yet?

---

