---
title: "Dual boot, 2 SATA hard drives, Vista + Ubuntu = noob?"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by indianajones123 on 2007-08-14
Hi everyone, a few weeks ago I successfully installed Vista and Feisty on one hard drive in a laptop, dual booted, etc.

I just tried to do the same with my desktop, but now Vista won't load.  Grub recognizes it, but it just won't boot.  Ubuntu on the second (which I'm running now) works fine.  I have two SATA drives.  The first has Vista with two partitions, C: for the OS, and D: for data.  The second has Feisty on it.  I'm pretty sure I know where I screwed up...

When getting to the part with Grub, instead of leaving it alone, I thought "oh, I had to edit this on my laptop, so i should do it here".  I clicked Advanced and changed (hd0) to (hd0,0).

Now, I'm pretty sure I thought it was a good idea because my Vista OS is on the first hard drive, first partition.  Regardless of my train of thought, is there anyway I can boot my Vista again?  After reading a lot, it sounds like I overwrote my MBR or something.  At the very least I can access my D: partition with Ubuntu so I can move my data over, but I'd **really** like to avoid reinstalling Windows.

Thanks!

---

### Post by logos34 on 2007-08-14
> **indianajones123 said:**
> Hi everyone, a few weeks ago I successfully installed Vista and Feisty on one hard drive in a laptop, dual booted, etc.

I just tried to do the same with my desktop, but now Vista won't load.  Grub recognizes it, but it just won't boot.  Ubuntu on the second (which I'm running now) works fine.  I have two SATA drives.  The first has Vista with two partitions, C: for the OS, and D: for data.  The second has Feisty on it.  I'm pretty sure I know where I screwed up...

When getting to the part with Grub, instead of leaving it alone, I thought "oh, I had to edit this on my laptop, so i should do it here".  I clicked Advanced and changed (hd0) to (hd0,0).

Now, I'm pretty sure I thought it was a good idea because my Vista OS is on the first hard drive, first partition.  Regardless of my train of thought, is there anyway I can boot my Vista again?  After reading a lot, it sounds like I overwrote my MBR or something.  At the very least I can access my D: partition with Ubuntu so I can move my data over, but I'd **really** like to avoid reinstalling Windows.

Thanks!

Post the ouput of 

**sudo fdisk -l** (lowercase L)

**cat /boot/grub/menu.lst**

Assuming the windows disk is set first in the hard disk boot order, and Vista (C: ) is the first partition (sda1 may be a utility/recovery partition for all I know), then with '(hd0,0)' you put grub on the very first part of the vista partition rather than the MBR (where it would have gone with grub-install command 'hd0').  You could try using SuperGrub CD to remove it and reinstall it to the mbr.

---

### Post by indianajones123 on 2007-08-14
Thanks for the response, here are the outputs.  And also, the first partition isn't a recovery partition.. I build the PC and installed a fresh copy of Vista.  The C: is 100gb for the OS/games/programs/etc and the D: is about 200gb for my docs/music/movies/etc.

sudo fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sda2           13055       38914   207711232    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4980    40001818+  83  Linux
/dev/sdb2            4981        5478     4000185   82  Linux swap / Solaris
/dev/sdb3            5479       20023   116832712+   b  W95 FAT32

Grub menu.lst:

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
timeout         10

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
# kopt=root=UUID=b05e5f02-ae18-4ae1-bf4f-ba7a27f3e83d ro

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b05e5f02-ae18-4ae1-bf4f-ba7a27f3e83d ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b05e5f02-ae18-4ae1-bf4f-ba7a27f3e83d ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b05e5f02-ae18-4ae1-bf4f-ba7a27f3e83d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b05e5f02-ae18-4ae1-bf4f-ba7a27f3e83d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista
root            (hd0,0)
savedefault
chainloader     +1

---

### Post by logos34 on 2007-08-14
I'd get the SuperGrub cd.  

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

First see if you can use it to boot vista.  Then use it to erase grub from sda1 and reinstall it to the mbr.  (I know you can use it to erase the mbr).  Not sure if that will do the trick but give it a try.  Otherwise you might consider getting [EasyBCD and using vista boot loader to boot linux. ]("http://neosmart.net/wiki/display/EBCD/Linu").  Linux occasionally has trouble [URL="https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28dual%29%7C%28boot%29"]dual booting vista.
[/URL]

Or you could try installing grub to the ubuntu disk's mbr, restore vista bootloader to sda, then use the bios to choose your boot drive.

---

### Post by confused57 on 2007-08-14
You might want to try the bootrec.exe utility on the Vista install DVD:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

bootrec /FixBoot  might restore your Vista bootloader, especially if you installed grub to (hd0,0).

---

### Post by MQMike on 2007-08-15
Vista’s CD should be able to fix the MBR  (hd0) and the partition (hd0,0).

Then, simply re-install GRUB over that same MBR, (hd0).

When you installed GRUB to (hd0,0), that may have messed up Vista, and so that must be fixed first.
Reinstalling GRUB to (hd0) then should be easy.  Your menu.lst looks ok, but that issue is moot right now because first you need to fix (hd0,0) and (hd0).

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)
(gives some tips, principles of Vista’s capabilities)

Re-installing GRUB:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)


This should be quite doable – depends on the utilities on the Vista CD for fixing these things, which I understand are pretty good.

BTW, you can use the Ubuntu Live CD to get at this issue, to get a terminal and to get the grub> prompt, etc. -- see the How-To's.

---

