---
title: "[SOLVED] more grub headaches"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by cjv8888 on 2008-06-14
I just installed Ubuntu on a second harddisk.
First harddisk contains Win XP.
Both are IDE in the master position.
In the BIOS , I can select to boot from HD0 or HD1.
HDO will boot directly Windows.
HD1 will bring up the grub.
Initially, I got error 17, cannot mount drive.
I edited the grub from HD(1,0) to HD(0,0) then I can boot into ubuntu but when I try to boot into other OS ie Win XP, it will bring me straight back into the grub.
What should I do?

Thanks in advance.

---

### Post by Pumalite on 2008-06-14
One should be Master and the other slave. You should install Ubuntu with both drives connected (set to 'Auto Select') and let Grub install to MBR. You'll have dual boot.

---

### Post by cjv8888 on 2008-06-14
My cables were not the new autoselect cables.
So what should I do now?
Is there a way to change the grub settings?

---

### Post by meierfra. on 2008-06-14
Try this, open a terminal (Applications->Accessories->Terminal) and type



```
gksudo gedit /boot/grub/menu.lst
```
(l is a lowercase L)

This will open the file "menu.lst". Change the Windows item to

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Save the file and reboot.

If this did not work, post the output  

```
sudo fdisk -l
```
(again l is a lowercase L)

and the content of "menu.lst"

---

### Post by cjv8888 on 2008-06-14
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e752e74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sda3            2933        4865    15526822+   f  W95 Ext'd (LBA)
/dev/sda5            2933        3986     8466223+   b  W95 FAT32
/dev/sda6            3987        4865     7060536    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a8fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4728    37977628+  83  Linux
/dev/sdb2            4729        9729    40170532+   5  Extended
/dev/sdb5            4729        9469    38082051   83  Linux
/dev/sdb6            9470        9729     2088418+  82  Linux swap / Solaris

This is the fdisk

I will try changing the XP on the menu.lst and post back

---

### Post by cjv8888 on 2008-06-14
changing the hd(0,0) to hd(1,0) result in the the system hanging at starting and a flashing cursor.
Here is the grub menu

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
# kopt=root=UUID=b251333d-0389-4445-9905-ce9741935a9e ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b251333d-0389-4445-9905-ce9741935a9e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b251333d-0389-4445-9905-ce9741935a9e ro single
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
chainloader	+1

---

### Post by meierfra. on 2008-06-14
You forgot the map lines:

title Microsoft Windows XP Home Edition
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1

---

### Post by cjv8888 on 2008-06-14
OH , the map lines !!
yes, I just added them and booted into Windows ok.

Thanks a million, mate.
What are they for ,btw so I will understand a bit more about them?

---

### Post by meierfra. on 2008-06-15
The XP boot loader  loses orientation if it is not  on the first hard drive (the drive you are booting from)    The two map lines  virtually swap the two hard drives.  After that Xp thinks it is on the first hard drive, and is able to boot.

---

