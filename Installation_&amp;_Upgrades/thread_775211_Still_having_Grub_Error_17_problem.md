---
title: "Still having Grub Error 17 problem"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2008-04-29
I have been trying to fix the Grub error 17 problem for several hours now.  I have read several fixes posted by other users but nothing seems to work.

Background:  I have had Winders XP Pro installed on the Primary Master IDE drive (sda or C: drive) for a long time.  I had Ubuntu 8.04 beta installed on the IDE Primary Slave drive (which I think is called sdb) for a few weeks and was regularly updating.  There is also a data drive installed on the IDE Secondary Master (which I think is called sdc).  Today, my Ubuntu disk filled up (it was only a 30 gb drive that I was using for testing).  So I replaced the 30 gig drive with a 200Gig drive and re-installed 8.04 LTS from the live cd.  Installation was smooth until reboot when I got the error 17.

One of the problems I am having is that I may not be editing the correct files.  When I boot from the LiveCD, the root file system is the cdrom.  if I open a terminal after booting from the livecd and do a "find / -name menu.lst -print" command, I do not find the menu.lst file.

I then go to "Places>Computer" and I get a list of all of the drives on the computer.  There is one called "Filesystem" which is the cdrom, and the drive that Ubuntu is installed on is called "197.0 GB Media".  If I double click on the "197.0 GB Media" I get all the files from the Unbuntu installation.  I can then navigate to /boot/grub and edit the menu.lst file that is there.  Is taht the correct file that I should edit??

If so, then here is a copy of the menu.lst and an fdisk -l for your review.   A couple of comments about the menu.lst.  I have tried several combinations of the two XP definitions at the bottom  Both commented out, both uncommented, one or the other uncommented, and using several different root identifiers.  Also the last one says /dev/sdc1, but there is not, and never has been an istallation of ANY OS on that drive so I don't understand why it says that.  Lastly, I have tried a couple of different root specifications for the Ubuntu systems but I think I have them set back to what the originals were in this list.  Nothing seems to have made any difference at all. 

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
color cyan/blue white/blue

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
# kopt=root=UUID=31f10765-a75a-4276-a408-755b6f2b3a04 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31f10765-a75a-4276-a408-755b6f2b3a04 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31f10765-a75a-4276-a408-755b6f2b3a04 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
#title		Microsoft Windows XP Professional
#root		(hd2,0)
#savedefault
#makeactive
#map		(hd0) (hd2)
#map		(hd2) (hd0)
#chainloader	+1



 sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30743838720 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x598f0dfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3737    30017421    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8283fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23947   192354246   83  Linux
/dev/sdb2           23948       24321     3004155    5  Extended
/dev/sdb5           23948       24321     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x370be2ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36483   293049666    7  HPFS/NTFS
ubuntu@ubuntu:~$ 




Thanks in advance for you help,

Wayne

---

### Post by martrn on 2008-04-29
You need to reinstall grub

From [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

Command line

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
4.  Type "grub"
5.  Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". Use whatever your computer spits out for the following lines.
6.  Type "root (hd1,0)", or whatever your harddisk + boot partition numbers are for Ubuntu.
7.   Type "setup (hd1,0)", ot whatever your harddisk nr is.
8.   Quit grub by typing "quit".
9.   Reboot and remove the bootable CD.

---

### Post by xeddog on 2008-04-30
Martrn -- 

Tried the commands you gave.  Still have the error 17.  Here is what happened with grub - 

[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> 


Not sure what the two errors mean.

Wayne

---

### Post by Moop on 2008-04-30
Have you tried changing which hdd is set to boot first in the bios? When you changed hdd's it may have changed where grub was located compared to the last install.

---

### Post by xeddog on 2008-04-30
Moop - Checked the bios and the boot sequence did not change.  Still set to boot from the XP drive after the cdrom.  But The order of the drives in the bios apparently DID change.  The bios had the XP drive as first, the 300GB data drive as the second drive, and the 200GB Ubuntu drive as the third drive.   When I set the order correctly IT WORKS!   WOOHOO.

Thanks 

Wayne

---

