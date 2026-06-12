---
title: "FakeRAID Hardy Dual Boot install WIN2k"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by PMWaddell on 2008-08-11
Loved and used Ubuntu on my laptop and finally made the plunge to setup my desktop.  As other users in the house need Windows I needed Dual Boot.

Followed the instructions at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) with great success.  Ubuntu is up and running, networked just fine, sound, video, etc.

The only catch is that due to the FakeRAID and existing Win2K install, the Grub install (and setup was a little vague) has left my Win2K inaccessible.  


Originally had a 8Gb Boot Partition, a 40Gb Data, 3Gb swap and 2 other partitions on an extended partition.

Removed the extended partition and recreated it using fdisk as 32Mb Boot, 512 Gb swap and the rest as Root.  But all on the extended.  This left my Windows Partitions mostly untouched.

Now Ubuntu loads up fine.  Windows loading from grub shows the f8 prompt for startup options, followed by the Windows 2000 Splash screen but before the progress bar can reach the end I get a Blue Screen error.  I will post the exact death screen later along with the fdisk output and fstab if needed.

Ok the question is, is this MBR, LVB, boot.ini, NTLDR, NTDetect.com, or some option miss-set in menu.lst or fstab?

I know it is getting to NTDetect but really this could be any number of things.

Thanks in advance.

===

Status Update one.

Noticed that the primary partition did not have the correct system id/type, corrected.  Now I can boot windows but it does not see the data drive or the swap drive.

Partly solved.

===

Status Update Three

Just needed to reassign the drive letters in windows and everything is back.

Problem solved.

===

Added Details

dmraid -r
/dev/sdb: sil, "sil_aeaibjdfcbae", stripe, ok, 160083456 sectors, data@ 0
/dev/sda: sil, "sil_aeaibjdfcbae", stripe, ok, 160083456 sectors, data@ 0


 dmraid -ay
RAID set "sil_aeaibjdfcbae" already active
RAID set "sil_aeaibjdfcbae1" already active
RAID set "sil_aeaibjdfcbae2" already active
RAID set "sil_aeaibjdfcbae3" already active
RAID set "sil_aeaibjdfcbae5" already active
RAID set "sil_aeaibjdfcbae6" already active
RAID set "sil_aeaibjdfcbae7" already active

 fdisk -l /dev/mapper/sil_aeaibjdfcbae

Disk /dev/mapper/sil_aeaibjdfcbae: 163.9 GB, 163925458944 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba417740

                       Device Boot      Start         End      Blocks   Id  System
/dev/mapper/sil_aeaibjdfcbae1   *           1        1044     8385898+   7  HPFS/NTFS
/dev/mapper/sil_aeaibjdfcbae2            1045        6266    41945715    7  HPFS/NTFS
/dev/mapper/sil_aeaibjdfcbae3            6267        6658     3148740    7  HPFS/NTFS
/dev/mapper/sil_aeaibjdfcbae4            6659       19929   106599307+   5  Extended
/dev/mapper/sil_aeaibjdfcbae5            6659        6663       40131   83  Linux
/dev/mapper/sil_aeaibjdfcbae6            6664        6726      506016   82  Linux swap / Solaris
/dev/mapper/sil_aeaibjdfcbae7            6727       19929   106053066   83  Linux


cat menu.lst
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
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password --md5 #####################################

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
# kopt=root=/dev/mapper/sil_aeaibjdfcbae7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

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

title		Ubuntu 8.04, kernel 2.6.24-19-386
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-386 root=/dev/mapper/sil_aeaibjdfcbae7 ro quiet splash
initrd		/initrd.img-2.6.24-19-386

title		Ubuntu 8.04, kernel 2.6.24-19-386 (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-386 root=/dev/mapper/sil_aeaibjdfcbae7 ro single
initrd		/initrd.img-2.6.24-19-386

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows 2000
rootnoverify	(hd0,0)
chainloader	+1
boot

---

### Post by fozzybear7703 on 2008-08-18
i am having the thing happing,after having a painful install on raid 0 with no ideas :(

---

