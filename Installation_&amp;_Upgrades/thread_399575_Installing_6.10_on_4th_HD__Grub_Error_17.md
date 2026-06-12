---
title: "Installing 6.10 on 4th HD / Grub Error 17"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by canehdian on 2007-04-02
Hello all.

I am encountering an issue when trying to get Ubuntu to launch/run. I am hoping (for now) to run a Dual Boot of Ubuntu and XP Sp2

After installing Ubuntu, what appeared to be successfully, I received a Grub Error 17 where it just froze. Normally I would have panicked, seeing I just partitioned part of a drive to install Ubuntu, but thankfully I had prepared a Super GRUB disk. Booting off the floppy I forced SGD to correct the MBR and back into Windows I went - all was there and good.

So I restarted and booted back onto the Ubuntu install CD and everything looked like it was correct on the partition ( I mounted the drive manually to see the files). Ok so then I tried to re-install Ubuntu - in case the first install was totally complete. Again it installed with no errors until I reboot - bringing the dreaded GRUB 17 error back. In went the floppy with SGD and a fix of the MBR brought windoze back. Ok I thought maybe I could do the same thing with SGD and force a Ubuntu boot - no luck. OK maybe correcting the GRUB install with SGD will work - nope - straight into windoze with no GRUB prompts to be seen.

What can I do to fix this?!


****System Specs - 3 IDE drives (120GB - 30GB Windoze/80GB NTFS partitions / 20 GB for CD/DVD temp/swaps / 80 GB single partition) and 1 SATA ( 58GB EX3 for Ubuntu and 2 GB linux-swap partition / 180GB NTFS partiton) - 1 DVD ROM - 1 DVDRW - 1 CDRW - 1.5 GB RAM - ATI(AMD) X800XL AIW + other stuff 


****Logs ---> I had to mount the drives from the install CD to get this data!

My output from the devicemap was:

(hd0) /dev/hda
(hd1) /dev/hde
(hd2) /dev/hdf
(hd3) /dev/sda <--- assuming this is my SATA drive where Ubuntu is installed?

******

fdisk -l output:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 5818 46733053+ 83 Linux
/dev/sda2 6079 30402 195371033 f W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.               <--- I have a weird 5.88MB unallocated partition created here?!
/dev/sda3 5819 6078 2088450 82 Linux swap / Solaris
/dev/sda5 6079 30402 195371032+ 7 HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4334 34812823+ 7 HPFS/NTFS
/dev/hda2 4335 14592 82397385 f W95 Ext'd (LBA)
/dev/hda5 4335 4648 2522173+ 7 HPFS/NTFS
/dev/hda6 4649 14592 79875148+ 7 HPFS/NTFS

Disk /dev/hde: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hde1 1 9964 80035798+ 7 HPFS/NTFS

Disk /dev/hdf: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdf1 * 1 2498 20065153+ 7 HPFS/NTFS

************************************************** ********************************

******************************* menulst:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-26-amd64-generic
root (hd3,0)
kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root (hd3,0)
kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro single
initrd /boot/initrd.img-2.6.15-26-amd64-generic
boot

title Ubuntu, memtest86+
root (hd3,0)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

************************************************** ************************************



Thanks in advance for all your help!!

---

### Post by bulldog on 2007-04-02
Set the Sata disk as the default boot device.
Install GRUB on this device,so when you boot your Sata hdd you will see GRUB,and you'll have a choice to boot ubuntu or windows.
You have to modify your windows entry in the menu.lst to fool windows,so it thinks it's on the first boot device.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
You get with the find command something like (hd3,0) so use with the setup command (hd3) instead of (hd0)
Make the Sata hdd your default boot device and it should work.

To make windows boot,open the menu.lst```
gksudo gedit /boot/grub/menu.lst
```
Make it like this,```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1
```

---

