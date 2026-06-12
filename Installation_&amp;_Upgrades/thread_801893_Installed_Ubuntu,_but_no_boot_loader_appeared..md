---
title: "Installed Ubuntu, but no boot loader appeared."
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by awchen on 2008-05-21
It seems a lot of people have had this problem.  I have browsed through the forum and have tried some of the advice given, nothing has worked.  I have also viewed the links provided on successfully installing a dual boot for Vista and Ubuntu, but that did not work.

I originally was running Vista on my system, I partitioned 2 part of my hd for the swap and the files for Ubuntu.  On reboot a boot loader did not appear, and I would like to still have access to Vista and all the remaining files on my hd.

The output "sudo fdisk -l"  displays the following.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08753408

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2432     9767520   82  Linux swap / Solaris


The output "cat /boot/grub/menu.lst" displays the following. 

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
# kopt=root=UUID=3625ca71-d958-4c48-9f0e-a86301cf6132 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3625ca71-d958-4c48-9f0e-a86301cf6132 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3625ca71-d958-4c48-9f0e-a86301cf6132 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Why does grub not have Windows Vista as an option?  I am concerned that I may not have access to the main partition where my windows and other files are located.  Thanks in advance for any help. 

-Alvin

---

### Post by iaculallad on 2008-05-21
In the terminal, issue this command to re-create the GRUB.

sudo update-grub

---

### Post by awchen on 2008-05-21
The boot loader still doesn't show Vista.  Is there anything else I can try?

---

### Post by iaculallad on 2008-05-21
Try [this]("http://ubuntuforums.org/showthread.php?t=224351"), hope it will work on your case.

---

### Post by awchen on 2008-05-21
Hm, still no good.  Anymore suggestions?

---

### Post by iaculallad on 2008-05-21
Are you sure you did not touch the the Vista partition when you tried partitioning your HDD? It seems that NTFS drive did not show on your previous post:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08753408

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1216 9767488+ 83 Linux
/dev/sda2 1217 2432 9767520 82 Linux swap / Solaris

Post your fdisk -l again: make sure that its not truncated.

---

### Post by awchen on 2008-05-21
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08753408

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2432     9767520   82  Linux swap / Solaris


This is not truncated.  I was concerned that no other drives appeared as well.  Does this mean I may have incorrectly partitioned my harddrive?

---

### Post by iaculallad on 2008-05-21
There's a big possibility that you did mistakenly partitioned your HDD. The reason why we can't see any NTFS drive as listed using the command fdisk -l. Goodbye Vista :-) ?

Once logged in your Ubuntu goto Places->Computer: Can you see your Vista partition in there?

---

### Post by awchen on 2008-05-21
Haha, alright, I didn't like Vista much anyways.  However, does this mean that I no longer have access to any of the files I once had?

---

### Post by iaculallad on 2008-05-21
Looks like it. Just hope that you backed-up your important data's prior to partitioning your HDD.

---

### Post by awchen on 2008-05-21
I did. I appreciate your help. Cute kid btw. :)

---

### Post by iaculallad on 2008-05-21
> **awchen said:**
> I did. I appreciate your help. Cute kid btw. :)

Thank you, that's my son :-) Go Ubuntu

---

