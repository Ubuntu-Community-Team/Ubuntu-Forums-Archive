---
title: "[SOLVED] GRUB not loading on new machine"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by wickstopher on 2008-01-26
Hello, there!  I recently built a new machine, and have installed both Windows XP and Ubuntu (Linux Mint Daryna).  For some reason, however, GRUB will not load when booting up the machine (i.e. it boots straight into Windows XP).  If I want to boot my linux installation, I have to do so via Super Grub Disk.  I have attempted to "Fix Boot of GNU/Linux" via the Super Grub Disk (it said that it succeeded), but to no avail.  Here's a quick rundown of my situation:

I have two hard drives installed in the machine.  One 500GB EIDE drive (slave, with my optical drive being the master), ext3 formatted and containing my /home partition, which I migrated over from my last machine, which was dual-booting the exact same two operating systems in an almost identical configuration.  I've never had any problem dual-booting before.  Also, a 250GB SATA hard drive, with 3 partitions.  The first partition is my XP install, the second partition is my Ubuntu install, and the third partition is swap.

When I first attempted to install XP, it wanted to write information to my /home drive.  It wanted me to reformat a partition of that drive into NTFS, and it wouldn't let me install unless I did that.  I didn't want to do that, so I disconnected that drive, and XP installed fine.  Then, I reconnected the /home partition drive, installed Ubuntu to the SATA drive, designating the EIDE drive as my /home partition, and everything works fine.  Except for some reason, as mentioned above, GRUB won't load when I start up the machine.  Anybody out there have any ideas?

---

### Post by logos34 on 2008-01-27
I think grub is on the MBR of the IDE drive.

Use Super Grub Disk to reinstall grub to the MBR of the SATA. Or use the [ubuntu live cd]("http://ubuntuforums.org/showthread.php?t=224351").  But you may have to change the 'root' and 'groot' lines in menu.lst to (hd**0**,1).

---

### Post by c0met on 2008-01-27
I'd try following the instructions at the below web page. It should fix things for you (it did for me when I was in a similar situation).

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by wickstopher on 2008-01-27
Okay, I finally got grub to load when I start my computer.  Thanks, guys.  My problem now is this: I got it to boot my linux partitions, but for some reason it won't boot Windows XP.    When I attempt to boot Windows XP from grub, I get the following message (it also prints the lines of the menu.lst entry for XP):

> Filesystem type unknown, partition type 0x7

Here is a copy of my menu.lst:

```
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
timeout		10

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# memtest86=true

## ## End Default Options ##

title		Linux Mint, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I know I'm probably just missing something stupid, so if someone out there has the ability to point out my stupidity, I'd be greatly appreciative!  Thanks!

---

### Post by confused57 on 2008-01-27
Try removing the map lines, you don't need them, since you're booting to the SATA drive.

---

### Post by wickstopher on 2008-01-27
Brilliant, that worked.  Thanks very much!

---

