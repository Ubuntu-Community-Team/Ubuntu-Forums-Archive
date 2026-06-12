---
title: "cannot boot vista after installing ubuntu 8.10"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by horming on 2008-11-14
I installed vista and then ubuntu 8.10.
Now Grub won't able to boot my vista.
When I select to boot vista ... it outputs "Starting up ..." and never came back.

Here is my fdisk -l + menu.lst

=========================================================
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09340933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36c552c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5005    40202631    7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22652265

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdc1   *           1       10012    80416768    7  HPFS/NTFS**
/dev/sdc2           10013       10136      996030   82  Linux swap / Solaris
**/dev/sdc3           10137       20023    79417327+  83  Linux**

Disk /dev/sdd: 4219 MB, 4219993600 bytes
4 heads, 32 sectors/track, 64391 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       64392     4121071+   b  W95 FAT32

=========================================================
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
# kopt=root=UUID=ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
[B]title		Windows Vista/Longhorn (loader)
rootnoverify	(hd2,0)
savedefault
makeactive
chainloader	+1[/B]
=========================================================

I need help to boot my vista back.
Help help help

---

### Post by caljohnsmith on 2008-11-14
So is Windows on sdc1 (the same drive as Ubuntu), or on a different drive? How about opening your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your current Vista entry with:
```
title      Windows Vista (hd0)
root       (hd0,0)
chainloader +1

title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows Vista (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
Reboot, try all the above combos, and if none of them work, let me know exactly what happens when you try each of them. Also, if none of them work, please also post:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
And we can work from there.

---

### Post by horming on 2008-11-14
I copy various of vista load entry to the menu.lst.
But I ran the "code" you reply as well before testing each combination.

About the result from the vista load entry combination:
1. OK
2. NTLDR is missing
3. (same as above)
4. Error 21: select disk does not exist

Thanks !

In the future if I want to reinstall ubuntu again freshly, from my fdisk -l dump, from GRUB, which root should I use?

Thanks again !

---

### Post by caljohnsmith on 2008-11-14
> **horming said:**
> I copy various of vista load entry to the menu.lst.
But I ran the "code" you reply as well before testing each combination.

About the result from the vista load entry combination:
1. OK
2. NTLDR is missing
3. (same as above)
4. Error 21: select disk does not exist

Thanks !

In the future if I want to reinstall ubuntu again freshly, from my fdisk -l dump, from GRUB, which root should I use?

Thanks again !
Glad to hear you got Vista to boot OK. If you need to reinstall Ubuntu, just put it in sdc3 which is your current Ubuntu main install. Cheers and have fun with your OSes. :)

---

