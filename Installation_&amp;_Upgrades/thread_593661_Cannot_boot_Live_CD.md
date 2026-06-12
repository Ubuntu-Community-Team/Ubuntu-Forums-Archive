---
title: "Cannot boot Live CD"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by tajreed on 2007-10-27
Here is the scoop:

1. Upgraded from Feisty to Gutsy via the recommended upgrade method. New Gutsy will not boot the 2.6.22-14 kernel. Must use the -12 kernel.
2. Tried to reinstall Gutsy via Live Cd- no go, slips to Busybox.
3. Tried Live CD on another box with Gutsy installed via continuous updates from the Alpha state. Live CD works perfectly. This box uses the -14 kernel.
4. Used the Live CD on a Vista laptop. It works.

?. What is wrong with my Gutsy install on the box that was upgraded from Feisty using the recommended upgrade method. Why can't I use the Live Cd and the -14 kernel?

---

### Post by Pumalite on 2007-10-27
Lets start with your specs.

---

### Post by tajreed on 2007-10-27
AMD 3.0
Nvidia 6200
1G Ram
2hd's
20 G Boot
40 G Data

etc/fstab shows drive id's as hda1 and hda2
etc/fstab in my upgraded machine shows sda1 and sda2.

Is this the prob?

---

### Post by Pumalite on 2007-10-27
Can you post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by tajreed on 2007-10-27
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b7023

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    37431449    18715693+  83  Linux
/dev/hda2        37431450    38475674      522112+   5  Extended
/dev/hda5        37431513    38475674      522081   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b5be962

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    80292869    40146403+  83  Linux
duke@duke-desktop:~$ cat /boot/grub/menu.lst
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
default         2

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
# kopt=root=UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d ro quiet splash
initrd          /boot/initrd.img-2.6.22-12-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d ro single
initrd          /boot/initrd.img-2.6.22-12-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
duke@duke-desktop:~$ 

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b7023

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    37431449    18715693+  83  Linux
/dev/hda2        37431450    38475674      522112+   5  Extended
/dev/hda5        37431513    38475674      522081   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b5be962

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    80292869    40146403+  83  Linux

---

### Post by Pumalite on 2007-10-27
You have an installed system and Grub pointing in the right direction.
What is this doing in your menu.lst:
duke@duke-desktop:~$

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b7023

Device Boot Start End Blocks Id System
/dev/hda1 * 63 37431449 18715693+ 83 Linux
/dev/hda2 37431450 38475674 522112+ 5 Extended
/dev/hda5 37431513 38475674 522081 82 Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b5be962

Device Boot Start End Blocks Id System
/dev/hdb1 63 80292869 40146403+ 83 Linux

Let's check your UUID's
At the Terminal:
cat /etc/fstab
blkid

---

### Post by tajreed on 2007-10-27
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=8989deae-7851-46ba-a441-85229187a2a7 /media/hdb1     ext3    defaults        0       2
# /dev/hda5
UUID=899391ca-d140-4bd3-8e77-fcec18f2b5d1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Pumalite on 2007-10-27
The whole idea is to compare blkid to fstab.

---

### Post by tajreed on 2007-10-27
They appear to be the same.

/dev/hda1: UUID="2a97c002-b017-4d0c-be1e-89f54df9ee1d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="899391ca-d140-4bd3-8e77-fcec18f2b5d1" TYPE="swap" 
/dev/hdb1: UUID="8989deae-7851-46ba-a441-85229187a2a7" SEC_TYPE="ext2" TYPE="ext3"

I take it that hda and sda differences are not significant?

And thanks for your time and effort. I have gotten nowhere yet with this problem.

---

### Post by Pumalite on 2007-10-27
Let's see:
/dev/hda1: UUID="2a97c002-b017-4d0c-be1e-89f54df9ee1d" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="899391ca-d140-4bd3-8e77-fcec18f2b5d1" TYPE="swap"
/dev/hdb1: UUID="8989deae-7851-46ba-a441-85229187a2a7" SEC_TYPE="ext2" TYPE="ext3"

# /dev/hda1
UUID=2a97c002-b017-4d0c-be1e-89f54df9ee1d / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb1
UUID=8989deae-7851-46ba-a441-85229187a2a7 /media/hdb1 ext3 defaults 0 2
# /dev/hda5
UUID=899391ca-d140-4bd3-8e77-fcec18f2b5d1 none swap sw 0 0

They are fine.
Let' s start with the basics: download new iso, do md5sum on iso before burn, bur at 4x, make sure CD is 1rst in boot order in BIOS. I would recommend an Alternate CD.

---

### Post by tajreed on 2007-10-27
Tried the Alt CD. Burned at low speed. Install still failed at:
35.094066-build/buildd/linuxsource2.6.22-2.6.22/drivers/usb/........

---

### Post by Pumalite on 2007-10-28
Did you do md5sum on iso?. Clean the lens in your burner, try the CD's in a different computer.

---

### Post by tajreed on 2007-10-28
I have tried the Live CD's on two diff computers and the work as expected. One was a laptop.

---

### Post by Pumalite on 2007-10-28
Clean your burner or change it then.

---

### Post by tajreed on 2007-10-28
I wish that were the fix but I'm afraid that it is not. I've burned the Live CD's and Alternate CD on this burner and have then tested the CD's on other machines. They work.

What is the deal with hda vs sda? My good install of Gutsy which uses the -14 kernel shows sda as the drive designators in fstab. Whereas the troubled install where I must use the -12 kernel shows hda in fstab. Is that a problem?

---

### Post by Pumalite on 2007-10-28
That's funny because since Feisty all hds are seeing as sds. The thing that counts is that UUID's between blkd and fstab correspond. I'll tell you this: I installed Beta in 2 machines (Clean install) and updated them all the way to Final Release without a hitch and they are working fine. I installed two Final Gutsy's in 2 other machines without a hitch. I don't know your present situation. I'm a Linux only user. Dual booting with Windows is another story, and laptops even worse, with their hidden 'diagnostics' and 'recovery' partitions. My laptops, I DBan them and then Gparted them and then install.

---

### Post by tajreed on 2007-10-28
Same for me on one machine where I started with an alpha gutsy. Updated all the way to final. Uses the -14 kernel and id's the hd as sda.

Upgraded my other machine-a Feisty machine using the official upgrade method. Cannot boot to -14 kernel, I have to use the -12 kernel and the hd's id'ed as hda. Something went wrong when I upgraded the Feisty machine.

---

### Post by Pumalite on 2007-10-28
Upgrades are messy. Better to save /home and data and do a clean install.

---

### Post by tajreed on 2007-10-28
Probably right. But now can't do a clean install. Live CD won't boot-back to the same dilemina.

---

### Post by Pumalite on 2007-10-28
Try booting Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
It mount all your drives/partitions automatically on boot.
You can use this to save:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

