---
title: "can't get windows to boot after installing ubuntu"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by tmelliott88 on 2007-08-23
I just installed ubuntu and love it. it seems to work great and everything. The only problem i have is I do not know how to boot up windows again. When it tells you to press the "esc"button on the start-up to run a different OS, windows is not a choice and i don't know how i can boot windows. A friend told me that I had to restore the master boot records for windows but i have no clue  how to do it. any help would be greatly appreciated. Thanks.

---

### Post by Pumalite on 2007-08-23
From Terminal post:
sudo fdisk -l (smal L)
cat /boot/grub/menu.lst

---

### Post by tmelliott88 on 2007-08-23
when i type in that stuff the list that comes up does not include windows, just Ubuntu, kernel 2.6.20-16-generic, Ubuntu, kernel 2.6.20-16-generic (recovery mode), Ubuntu, kernel 2.6.20-15-generic, Ubuntu, kernel 2.6.20-15-generic (recovery mode), and Ubuntu, memtest86+

---

### Post by Pumalite on 2007-08-23
Post everything, so I can help you edit it. Without the facts I cannot help you. (copy and paste)

---

### Post by tmelliott88 on 2007-08-23
tim@tim-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6817    54757521   83  Linux
/dev/sda2            6818        7113     2377620    5  Extended
/dev/sda5            6818        7113     2377588+  82  Linux swap / Solaris
tim@tim-laptop:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory
tim@tim-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=64dcad76-53a9-4edc-8f05-68d21459c100 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=64dcad76-53a9-4edc-8f05-68d21459c100 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=64dcad76-53a9-4edc-8f05-68d21459c100 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=64dcad76-53a9-4edc-8f05-68d21459c100 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=64dcad76-53a9-4edc-8f05-68d21459c100 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2007-08-23
Windows does not exist in your system. You probably erased it when you installed. Sorry. On the other hand; be happy; you got rid of it.

---

### Post by merlinus on 2007-08-23
Sad to say, unless you have two hdds, your install of ubuntu wiped out windows.

Did you select "Use Entire Disk" at the partitioning menu?

Hopefully you backed up important data.

-merlin

---

### Post by tmelliott88 on 2007-08-23
i don't think  i did, i think i only used like 5 gb for ubuntu

---

### Post by Pumalite on 2007-08-23
The reality is: windblows is no more.

---

### Post by merlinus on 2007-08-23
Clearly something went wrong...

Let us know if you want assistance with reinstalling xp, if need be.

-merlin

---

### Post by merlinus on 2007-08-23
> **Pumalite said:**
> The reality is: windblows is no more.

The wind blows most all the time here at 7000' of elevation in northern New Mexico.

:lolflag:

-merlin

---

### Post by Pumalite on 2007-08-23
Glad to see you in the forums. Enjoy New Mexico!. I've been there and I love it.

---

