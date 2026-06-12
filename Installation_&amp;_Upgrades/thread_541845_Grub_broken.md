---
title: "Grub broken"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by df9517 on 2007-09-03
Hello,

After installation of Gutsy alpha tribe 4 my Grub was broken.FInally I gave up and reinstalled everything. Sadly, this strange problem remains. I will give you all information, please help me to find the cause:

Main info:
PC booting at HD1=sdb
sda is only a storage hdd
sdb1 = hd(1.0) mounted / and includes the /boot  (Kubuntu feisty 64 bit)
sdb2 = hd(1.1) mounted /home
sdb3 = (hd(1.2) swap

What is happening now is:
PC booting on HDD1.
PC gives me file not found.
Then I edit the boot script from 1.0 to 0.0 and then it starts.

This is unbelievable for me.

He comes outputs: sudo fdisk -l

daniel@Desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217       29786   229488525   83  Linux
/dev/sdb3           29787       30401     4939987+  82  Linux swap / Solaris
daniel@Desktop:~$

---

### Post by df9517 on 2007-09-03
/boot/grub/menu.list

from sdb1

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=3f25c683-20ee-4c89-a6cf-3c4152e1c598 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3f25c683-20ee-4c89-a6cf-3c4152e1c598 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3f25c683-20ee-4c89-a6cf-3c4152e1c598 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by df9517 on 2007-09-03
/boot/grub/device.map at sdb1

(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by Pumalite on 2007-09-03
What do you have in sda1 (hd0,0)?

---

### Post by Pumalite on 2007-09-03
Best thing you can do: re-install Grub with this:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by df9517 on 2007-09-03
Its a ext3 partition in sda. Some backups an definately no /boot or so, Still the computer boots up whan I change it to HD0,0    :/

Tried the grub thing so many times.

sudo grub
root (hd1,0)
setup (hd1)

same result as above

sudo grub
root (hd1.0)
setup (hd0)

same result as above


Use GRUB many times before, not first time for sure.

All this was created when I installed a Gutsy 5 alpha on a new partition on sdb. The partition ts now removed and shouldn`t have anything do do with it.

This is so strange really.

---

### Post by Pumalite on 2007-09-03
Well it looks like backing up all your data and re-install.

---

### Post by df9517 on 2007-09-03
Sorry. This is already just installed from scratch.

I am thinking about if removing sda temporarily would help?

---

### Post by Pumalite on 2007-09-03
I would first invert the order of hard drives boot in BIOS.

---

### Post by df9517 on 2007-09-04
I changed my menu.lst to 0.0 instead. Now it works but it is very strange.

I can accept this for now.

---

### Post by Pumalite on 2007-09-04
> **df9517 said:**
> I changed my menu.lst to 0.0 instead. Now it works but it is very strange.

I can accept this for now.

Post your menu.lst so the rest of the forum can understand what was the solution to your problem, please.

---

### Post by df9517 on 2007-09-05
What do you mean? menu.lst was posted already from beginning in message 2 or 3.u

---

### Post by Anteaus on 2007-09-05
Doesn't help  present situation I know, but I would never allow grub to install into the MBR if I had a choice, especially not on a multiboot system. 

Issue is that since grub relies on information in one specific partition, this creates a '[house of cards](http://www.lalamy.demon.co.uk/ronanpnt.htm)' -a dangerous SPOF for the whole computer. 

Better to install the bootloader to the boot partition, and if multiboot is needed, use a simple boot-chooser utility (e.g. Ranish) which operates independently of any partitions. 

Lilo in the MBR is slightly less risky, as it's very much easier to repair than the hypercomplex grub if it should break. Even so, better to have system-resilience by keeping partitions independent of each other. 

Just my ten cents' worth, based on RH/Mandrake experience.

---

