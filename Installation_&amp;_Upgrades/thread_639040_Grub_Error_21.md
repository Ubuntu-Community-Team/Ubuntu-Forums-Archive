---
title: "Grub Error 21"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by JeffoOfMetal on 2007-12-12
I tried installing Xubuntu on a 4GB flash drive. I ran the Xubuntu live CD on a Windows computer and then went through the steps to install and chose the flash drive as the install destination. The install went on, but it took a while. Then, I tried to reboot the computer, and it couldn't boot back into Windows XP. I got Grub error 21.

I tried rebooting while the jump drive was in and I could successfully boot into Windows and then remove the flash drive after I did, with XP still going. 

I'm guessing the problem has to do with the Xubuntu install somehow moving the Windows boot file onto the flash drive.

I looked at the flash drive's contents and saw the normal Xubuntu filesystem, with a folder called "boot" and with a handful of files in it.

Can someone help?

---

### Post by MeathooK427 on 2007-12-12
It sounds to me like grub's menu.lst file is messed up. Can you post the contents for us?

...should be in /boot/grub/

Also in terminal type: sudo fdisk -l

Paste the output of that cmd as well

Thanks

---

### Post by JeffoOfMetal on 2007-12-12
this is from fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31080   234964768+   7  HPFS/NTFS
/dev/sda2           31082       32301     9223200    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         463     3719016   83  Linux
/dev/sdb2             464         491      224910    5  Extended
/dev/sdb5             464         491      224878+  82  Linux swap / Solaris

==========================================

and the contents of /boot/grub:

* default (type of file: default document)
* device.map
* e2fs_stage1_5
* fat_stage1_5
* installed-version
* jfs_stage1_5
* menu.lst
* minix_stage1_5
* reiserfs_stage1_5
* stage1
* stage2
* xfs_stage1_5

all are documents.

---

### Post by MeathooK427 on 2007-12-12
Thanks for the fdisk output, however the menu.lst file is what I need, it's in the /boot/grub folder.

Full path is /boot/grub/menu.lst

Thanks

---

### Post by JeffoOfMetal on 2007-12-12
```
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
# kopt=root=UUID=077aca1a-b8c2-4fdc-a2c9-b691d768ac8b ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=077aca1a-b8c2-4fdc-a2c9-b691d768ac8b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=077aca1a-b8c2-4fdc-a2c9-b691d768ac8b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by confused57 on 2007-12-12
What happened is that grub was installed to your internal hard drive's mbr, you can restore Windows IPL with an XP installation cd, Win98SE oem boot floppy, or Super Grub Disk:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
This will enable you to boot into Windows without the flash drive inserted.

If your flash drive has a mbr and your bios is capable of booting first to USB, you can install grub to the flash drive's mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
you would do something like:
root (hd1,0)
setup (hd1)

Then try booting first to the flash drive...if you get a grub boot menu, highlight the Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.

If your bios isn't capable of booting first to USB, go ahead and restore your Windows mbr, then try using SGD to boot into Ubuntu(you don't need to make any changes to the root designation, if you use this method).

Here's a description of grub error 21:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by JeffoOfMetal on 2007-12-12
thank you so, so much! :)

I'm sure I'll be able to use the XP install cd.

Thank you

---

### Post by confused57 on 2007-12-12
> **JeffoOfMetal said:**
> thank you so, so much! :)

I'm sure I'll be able to use the XP install cd.

Thank you

Glad to help, hope it works...

---

### Post by JeffoOfMetal on 2007-12-13
Success!

That was easy!

I was looking for solutions earlier and they were all so complicated.

Thank you!

:)

---

