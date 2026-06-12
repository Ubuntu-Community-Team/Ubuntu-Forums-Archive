---
title: "Bootloader Issues"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by musey on 2008-06-06
Recently upgraded my pc. Installed Windows XP into one partition using half the hard drive. Today installed Ubuntu 7.10 into a partition using the other half.

After rebooting I got a message at startup saying "Error Loading Operating System". I loaded up the CD and found some commands to reinstall GRUB:

When you get to the desktop open a terminal and enter.

sudo grub

This will get you a "grub>" prompt

find /boot/grub/stage1

This will return a location.Use that location in the next line

root (hd1,1)

Next enter the command to install grub to the mbr but be carefull here,if the find command returned (hd1,?) the setup should be on (hd1) not (hd0)

setup (hd1,1)

Exit the grub shell

quit


After rebooting GRUB appeared and I chose to load XP. However, since then my pc has been loading XP without showing GRUB. So I need some help :-)

I see similar threads asking for the output from a couple of commands so here they are:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cd02ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31871   256003776    7  HPFS/NTFS
/dev/sda2           31872       59623   222917940   83  Linux
/dev/sda3           59624       60801     9462285    5  Extended
/dev/sda5           59624       60801     9462253+  82  Linux swap / Solaris

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd25dd25

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10010    80405293+   7  HPFS/NTFS

(This 80Gb drive is from my old setup when I had XP and Ubuntu on separate drives)

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

(It appears that the grub folder has disappeared since I reinstalled it)

---

### Post by Herman on 2008-06-06
> ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

(It appears that the grub folder has disappeared since I reinstalled it)That's because you're looking for /boot/grub/menu.lst in your Ubuntu Live CD and there isn't one. It's a common mistake, everyone does that at first. If you want to access your /boot/grub/menu.lst in your hard disk, you have to mount a file system in your hard disk first. Then it will be found in your /media folder in your LiveCD, or wherever you mounted it.
cat /media/ubuntu/boot/grub/menu.lst.
For more details, see this link, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").

---

### Post by Herman on 2008-06-06
> I loaded up the CD and found some commands to reinstall GRUB:
When you get to the desktop open a terminal and enter.
sudo grub
This will get you a "grub>" prompt
find /boot/grub/stage1
This will return a location.Use that location in the next line
root (hd1,1)
Next enter the command to install grub to the mbr but be carefull here,if the find command returned (hd1,?) the setup should be on (hd1) not (hd0)
setup (hd1,1)
Exit the grub shell
quit Okay, so you installed GRUB to your Ubuntu partition?

What boot loader do you have in the MBR of your first hard disk (hd0)?
Shouldn't you install GRUB to MBR in (hd0)?
You probably will need some kind of a boot manager like GRUB or GAG Boot Manager installed in the MBR of your first hard disk if you want to be able to dual boot.

Alternatively, you could install GRUB or GAG or another boot manager in the MBR of any non-first hard disk and boot it from your BIOS, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).

to set up GRUB to boot from your first hard disk like most of us do, you would use the same sequence of commands as you already used, and replace 'setup (hd1,1)' with 'setup (hd0)'.

---

### Post by musey on 2008-06-06
Aha! Ok, here we are:

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
# kopt=root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Herman on 2008-06-06
You may also need to switch your hard disk order in your BIOS if you have one SATA and ONE PATA (IDE) hard disk, as there appears to be some confusion as to which one is your first hard disk and which one is second. 
Fdisk says your 500 GB hard drive is first, but GRUB thinks it's (hd1), which would be your second hard drive.

---

### Post by musey on 2008-06-06
We're getting closer. I removed the IDE drive from the system and the command find /boot/grub/stage1 came back with the result "(hd0,1)". I then entered the commands:

root (hd0,1)
setup (hd0)

Now GRUB loads at startup. However when Ubuntu is selected I get the message:

"Error 21: Selected disk does not exist"

Windows loads as normal.

---

### Post by Herman on 2008-06-06
Okay, here's what GRUB Error 21 means, [Grub error 21]("http://users.bigpond.net.au/hermanzone/p15.htm#21").

:)  So, now try editing your /boot/grub/menu.lst as follows, (there are four changes, be sure to scroll down to see them all),
```
## default grub root device
## e.g. groot=(hd0,0)
[COLOR=Red]**# groot=(hd1,1)**[/COLOR]

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR=Red]**root        (hd1,1)**[/COLOR]
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
**[COLOR=Red]root        (hd1,1)[/COLOR]**
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
[COLOR=Red]**root        (hd1,1)**[/COLOR]
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
``````
## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,1)**

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
**root        (hd0,1)**
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
**root        (hd0,1)**
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=bbba26cd-95d1-4996-b5d4-71f6a42548d3 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
**root        (hd0,1)**
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

---

### Post by Herman on 2008-06-06
:) And then, if you want to, you can plug your 80 GB IDE hard drive back in again, but just make sure you set your hard disk boot priority in your BIOS so that your Sata hard disk is the first hard disk and the IDe hard disk will be second, [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").
NOTE: Your 'hard disk boot prioity' is something different to 'hard disk boot sequence', but the exact terminology will be different according to what brand of BIOS you have.

---

### Post by musey on 2008-06-08
Fantastic! Thank you very much.

---

