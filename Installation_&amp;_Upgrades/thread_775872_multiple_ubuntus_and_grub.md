---
title: "multiple ubuntus and grub"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ve3dvv on 2008-04-30
The problem is every time I add another Ubuntu the boot partition gets overwritten and it only boots the last install.

500GB drive as follows

/dev/sda1   /boot      1GB     boot partition
/dev/sda2   /          100GB   Ubuntu 8.04 64 bit
/dev/sda3   swap       2GB
/dev/sda4   Extended
/dev/sda5   /          100GB   Ubuntu 8.04 32 bit
/dev/sda6   /shared    50GB
/dev/sda7   /          remainder  MythBuntu 8.04

Question: how to fix grub?

Note: at moment it boots directly into Mythbuntu

John,

---

### Post by El King on 2008-04-30
open terminal 
```
sudo gedit /boot/grub/menu.lst
```
and
```
sudo fdisk -l
```
and post back both

---

### Post by Rallg on 2008-04-30
While El King helps you solve your problem, let me give some general advice:

When you install Ubuntu (or most other variants of Linux), you do not have to install a bootloader. If you simply accept the default bootloader installation, it will usually over-write what you had previously. That might or might not be a problem.

A better approach, with multiple Linux installations, is to NOT accept the default bootloader installation after the first install. For example, on my system I use the Ubuntu "advanced" install feature to place Grub on the new Ubuntu partition, rather than on the hard drive's main partition. Then, each Linux partition has its own Grub files, but only one of them is referenced from the MBR. I will have to go back and manually edit the menu.lst for that one, but there is no interference from a new installation. In fact, you can do without installing a duplicate Grub, but I do it so that I can see the new UUID and any changes that might have happened.

---

### Post by ve3dvv on 2008-04-30
Thanks for replying so fast...

================================================================
HERE IS MY FDISK LISTING
==================================================================
~$ sudo fdisk -l
[sudo] password for john6:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e60f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123       11672    92775375   83  Linux
/dev/sda3           11673       11915     1951897+  82  Linux swap /
Solaris
/dev/sda4           11916       60801   392676795    5  Extended
/dev/sda5           11916       24663   102398278+  83  Linux
/dev/sda6           24664       30742    48829536   83  Linux
/dev/sda7           30743       60801   241448886   83  Linux
john6@mythbuntu-32:~$

========== HERE IS /BOOT/GRUB/MENU ================================

root@mythbuntu-32:~# cat /boot/grub/menu.lst
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
# kopt=root=UUID=b5395fa0-a516-4d4a-950b-8b0262df8575 ro

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
kernel		/vmlinuz-2.6.24-16-generic root=UUID=b5395fa0-a516-4d4a-950b-8b0262df8575 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=b5395fa0-a516-4d4a-950b-8b0262df8575 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
root@mythbuntu-32:~#

---

### Post by confused57 on 2008-04-30
It's really not advisable to share a separate /boot partition among different distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

If you're using a separate boot partition to overcome grub error 18, due to bios limitations, it would be better to set up your main distro to use the boot partition.  When you install other distros, install grub to the root partition of the new distro, then add a chainload or configfile entry to your main distro's /boot/grub/menu.lst to boot the new distro:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
On 2nd thought, I'm not sure if this would work if the new distro's kernel is located outside the bios limitation.

You don't need a separate boot partition, except to overcome the bios limitation...if this is the reason you're doing so, I'd recommend installing with a smaller root partition for each of the distros to keep them within the limitation, then create a large ext3 data partition that you can share among the distros.

Added:  You may be able to boot your other distros by adding a symlink entry for each of them:
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

To edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

---

### Post by gnumd on 2008-05-02
Informative.  I am noob so bear with me please.

I have an 8G eeePC.
So it has an SSD internal drive of 8G.
I am using SDHC cards for my installs.

First I installed WINXP to the SSD and then moved it using Acronis to an SDHC card and it works great.
Well it boots great, it actually runs too slow for my taste.  

I then erased the SSD and installed Ubuntu 7.10 to an SDHC but also use the SSD as a separate /home partition.  I also put a boot partition on the SSD.  When I boot I press <esc> when the BIOS is doing its business and choose what device I want to boot from manually.  So if I have in the WINXP SDHC I pick the SDHC and it works.  If I have the Ubuntu SDHC inserted I pick the SDHC and it works with the /HOME storing my user files.  I didn't think until now that the boot partition mattered to the SDHC installs but I think I must be wrong.

It was working flawlessly in the above manner.
Then I decided to experiment with GnewSense and installed it to an external USB HDD.

I must have forgotten to ignore putting on GRUB or something because now I can only boot into the USB HDD into GnewSense.  When I choose the SDHC with Ubuntu 7.10 inserted I can't get into the SDHC's OS.

Interestingly, when I put in the WINXP SDHC it runs fine?

> My question that hopefully will fix my dilemma is:
How do I put in a GRUB boot that will permit me to access the Ubuntu 7.10 on the SDHC and maintain my previous install?  Can I do this and still keep the GnewSense installation (it needs a bit of work to get internet working but ultimately I'd like to go completely FREE/LIBRE).

Thank you!

~gnumd~

---

