---
title: "add to grub"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by j_dog on 2008-06-11
how would I add a third os to grub. I have Ubuntu and XP on seperate drives. I would like to tinker with Kubuntu that is on a third drive. I have my menu.lst in front of me. I am not sure what to add.

---

### Post by Pumalite on 2008-06-11
Post:
sudo fdisk lu

---

### Post by j_dog on 2008-06-11
john@john-desktop:~$ sudo fdisk lu
[sudo] password for john:

Unable to open lu
john@john-desktop:~$ sudo fdisk 

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
john@john-desktop:~$

---

### Post by Pumalite on 2008-06-11
Sorry; my fault:
sudo fdisk -lu

---

### Post by j_dog on 2008-06-11
john@john-desktop:~$ sudo fdisk -lu
[sudo] password for john:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009af0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   468648179   234324058+  83  Linux
/dev/sda2       468648180   488392064     9871942+   5  Extended
/dev/sda5       468648243   488392064     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ad91ad9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b204b1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   230275709   115137823+  83  Linux
/dev/sdc2       230275710   240107489     4915890    5  Extended
/dev/sdc5       230275773   240107489     4915858+  82  Linux swap / Solaris
john@john-desktop:~$

---

### Post by Pumalite on 2008-06-11
Post:
cat /boot/grub/menu.lst

---

### Post by j_dog on 2008-06-11
john@john-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default         0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=splash vga=789

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
# memtest86=false

## ## End Default Options ##

title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro splash vga=789
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

john@john-desktop:~$ ________________

---

### Post by Pumalite on 2008-06-11
sudo mkdir /media/sdc1
sudo mount -t ext3 /dev/sdc1 /media/sdc1
cat /media/sdc1/boot/grub/menu.lst
Copy the appropriate portion to your present menu.lst

---

### Post by j_dog on 2008-06-11
You lost me with that last step. "Copy the appropriate portion to your present menu.lst"

Oh... wait, I got it . Let me try it

---

### Post by logos34 on 2008-06-11
Or just add this stanza:

> title Kubuntu 
root (hd2,0)
kernel /vmlinuz 
initrd /initrd.img

By using the **symlink** format you just set and forget it.  No need to change it after the next kernel update (-19 is lurking out there as we speak)

---

### Post by j_dog on 2008-06-11
> **Pumalite said:**
> sudo mkdir /media/sdc1
sudo mount -t ext3 /dev/sdc1 /media/sdc1
cat /media/sdc1/boot/grub/menu.lst
Copy the appropriate portion to your present menu.lst

O.K. it shows up in the boot menu. But whe I choose it I get error 15.
not found

---

### Post by Pumalite on 2008-06-11
Post:
cat /media/sdc1/boot/grub/menu.lst.
I'll edit your original menu.lst for you.

---

### Post by j_dog on 2008-06-11
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default		0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=splash vga=789 quiet

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
# memtest86=false

## ## End Default Options ##

title		Linux Mint, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro splash vga=789 quiet
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=dca26b75-cc44-4965-9100-67b4b70f4bbc ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=dca26b75-cc44-4965-9100-67b4b70f4bbc ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

---

### Post by Pumalite on 2008-06-11
You have Linux in sda1 and sdc1. When you first posted your menu.lst I thought it was from sda1. Are you telling me that you have the same menu.lst in sda1 as in sdc1? Or are you changing the boot order of your hard drives? You talked of incorporating Kubuntu from your 'third' drive. Follow logos34 advice and see what happens.

---

### Post by j_dog on 2008-06-11
Linux is on sda1 and sdc1. I have been working with the menu.lst from Sda1.
there is a menu.lst on sdc1. I unplugged the first 2 drives when I installed Kubuntu. I did not want to take a chance of messing up my main OS.

Oh by the way,  I thank you very much for all help you have given me. I greatly appreciate the time and effort you put into this.

---

### Post by Pumalite on 2008-06-11
You are welcome. I'm still curious to see what your Kubuntu menu.lst looks like.

---

