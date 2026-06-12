---
title: "partition issues"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by corticalaxon on 2007-12-11
Hello, I'm a complete newbie and from past threads haven't exactly found my answer.
I'm trying to install ubuntu 7.10 and i'm at the partitions stage...i set up a partition in my 500 gb external, but whenever i click forward, it always says it doesn't have a root file system defined, and so i go into "edit partition" and i put in ext3 (later i tried fat32 because i think my external is by nature fat32), and still the same thing comes up...what should I do? Also, what does mount point mean? Thanks in advance...

Edit: i found out how to get rid of the no root file system, now i just am wondering...none of the file systems work. I put in / for the mount point and have tried a number of different file systems (after having created one partition and another swap partition), and during the installation process it always says the installation to SCSI3 partition 5 (the portion on my 500 gb external) of ___ file system failed. What do I do? Please help me...

---

### Post by forestpixie on 2007-12-12
it needs to be ext3 and as you've deduced / as a mount point

---

### Post by v.alari on 2007-12-12
Been there a couple days ago, you will also need a Swap partition at least 256mb big, I chose to make mine 4GB and considering the size you have to work with consider something similar.

NOTE: I found that I wanted to make more partition later on but cant because I have 4 primaries already, if you may encounter this scenario, make one extended primary and then use logical partitions inside it. You can still use up to three other primary partitions as well if you want.

---

### Post by forestpixie on 2007-12-12
if you've got 64bit - swap can be that big - but not 32bit - unless you change the kernel I think

with 32bit as it is you can have a total of 4Gb RAM and swap

---

### Post by v.alari on 2007-12-12
Thats true, I am on an AMD64. Also running swap on a separate drive is supposed to be faster but probably more hassle. Just what I read.

---

### Post by corticalaxon on 2007-12-12
Hmm...

I am on a 32 bit P4 dell (from 4 years ago) and the only reason I'm not partitioning on my main 80gb drive is because it has very little space left. I could move some stuff from that drive to the external, but my external is only the essentials edition WD, and so it would probably take forever.

By putting ext3 do you mean using ext3 as file system and then typing in /ext3 for mount point; I'm asking this only because I already tried using ext3 (and for that matter most of the other file systems) as the file system and simply "/" as the mount point, and the "write to file system failed" sign shows up during installation.

I put a 512 mb swap partition, but from what you all have been saying, it seems like I should reduce this because I only have 32bit.

And, for what it's worth, my partition screen consists of 

Main drive
     -Used space  (most of it) 
     -free space (apprently only like 32 mb)
External
     -free space (something like 450000mb or something like that, 
     whatever it was formatted with -50gb)
     - /sdb5 swap (512mb - like I said maybe i should reduce this)
     - /sdb6 ext 3  /   (50000 mb)

Based on reading what others have done, you'd think it would work. I don't even have 4 partitions on either drive. But apparently not yet. Like I said, I could move some media files from the main drive to the external, and then put at least the swap on the main drive (because one of you said it's easier). 

Finally, perhaps it might have something with the fact that when partitioning I chose logical partition instead of the other option (the real partition). I, however, am not sure.

Thanks for all the input, though, I really appreciate it.

Edit: Quite weirdly, when I booted back into windows today my external drive 'disappered,' and no such drive was found even though it is connected and running. I tried dis and reconnecting to no avail. I am really in the mud.

---

### Post by corticalaxon on 2007-12-12
I have a screenshot here of what my partition screen looks like. There seems to be some unnecessary stuff (i.e. that free 254 mb) there. Yet the 500gb shows up, although still not in Windows (probably because the file system is messed up from last night's messing around). Thus, I need to figure out how to get rid of that extra free space 254 mb and have only the free space (450gb), the swap (256), and the install (50gb) under my 500 gb drive in a combination that works. Have failed to do that and to revive recognition of my external drive outside of the partition programs. Please help.

---

### Post by corticalaxon on 2007-12-12
Yeah so, I somehow finally got linux to install fully. It finished. But now, when the  computer restarted, it came to the black GRUB screen, said GRUB loading, please wait, and then it said error 21. (I don't know what that means). It just stood there like that. Didn't do anything. I forced off and rebooted, same thing. I forced off and rebooted several times using dells f12 setup boot list menu, and i chose C (main) drive, same thing (which is strange because I installed linux on the ext3 on the external), but maybe not so strange because GRUB controls that and the linux-external drive and thus might apply to all drives. How do I remedy this situation, though? I can get into neither Windows nor Linux, and the only way I'm typing this right now is by rebooting with the LiveCD. And, still, my 500gb hard drive is not recognized.

Someone help me please...I'm stuck in the ubuntu livecd without access to either os, and therefore to grub...I need to get into windows, that's where all my stuff is.. : (

---

### Post by Sef on 2007-12-12
This is GRUB error 21:

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

GRUB can't read your disk for some reason.   You could try reinstalling GRUB with [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by corticalaxon on 2007-12-12
I shall try to burn the supergrub iso and install it on the LiveCD, but I don't know if that's possible...

I still don't understand why Grub doesn't read it, though. I named it /dev/sdb6 in the ubuntu install, assigned it ext3 and / like everyone says, etc.

Edit, for what it's worth, here's my menu.lst from the LiveCD, I have absolutely no idea how to interpret it, and I can't modify it because it' s a livecd and i don't have permissions


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
# kopt=root=UUID=b6d164a9-f302-44fa-a298-1fd0c891402c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b6d164a9-f302-44fa-a298-1fd0c891402c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b6d164a9-f302-44fa-a298-1fd0c891402c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by corticalaxon on 2007-12-13
I have one last idea for saving my computer...If, through the livecd, I delete the partition on my external harddrive on which I installed ubuntu, will that therefore delete GRUB and therefore I won't get the GRUB error and I won't boot into it by default (provided that, on reboot, i switch the internal harddrive where windows is to the first boot option)? And will that kill my external harddrive (as of yet I still can't access the untouched rest of the 418 gb, only the internal harddrive and the 40 gb linux install partition of my external are visible)?

Edit: Based on what some of you have been saying and on what I've been reading, I did try to recover the windows boot loader through the xp recovery disk, to no avail. I got to the screen where I could modify the boot settings but there was only one (the internal xp drive) recognized anyways, but I set it as default (it said winxp on it), and still I got the GRUB 21 error, which makes sense because GRUB is still present.

---

### Post by froy02 on 2007-12-13
Linux or windows do not boot in logical partitions.  They have to be formatted as primary partitions to use for boot, nts or ext3.

---

### Post by corticalaxon on 2007-12-13
Ah. That would be a problem. I installed it as logical partition on the external. Is there a way I can reverse the install or something (sorry for my ignorance I'm a case in point noob) or perhaps change the partition through Gparted? Thanks.

---

