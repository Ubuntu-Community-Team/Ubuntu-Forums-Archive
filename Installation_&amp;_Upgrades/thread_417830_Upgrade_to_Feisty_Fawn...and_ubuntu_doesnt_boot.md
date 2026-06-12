---
title: "Upgrade to Feisty Fawn...and ubuntu doesnt boot"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Ram Ravichandran on 2007-04-21
Hi,
I decided to upgrade my ubuntu from edgy to feisty since the software manager was nice enough to let me know that a new distribution was available! The upgrade process went smoothly allnight long. I have a dual boot, switched to windows and then tried to boot into ubuntu this morning, but the bar on splash screen moves a little bit and then stops. I booted into command line and saw the following:

Loading Ubuntu, please wait...

check root = bootarg cat /proc/cmdline
or missing modules, devices: cat/proc/modules ls /dev
ALERT! /dev/hda3 does not exist   Dropping to shell!

BusyBox v1.1.3 Built-in shell (ash)

/bin/sh can't access tty; job control mode off.

and then puts me into an intiramfs prompt.

I guess that in the upgrade process, the device map pointing to the right boot partition (/dev/hda2) and the home partition (/dev/hda3) got mixed up.

Any ideas on how I can go about fixing this? Is downgrading back to edgy possible? I'd really like to get back to my ubuntu environment rather than windows.

Any suggestions would be appreciated!
Thanks,
Ram

---

### Post by autocrosser on 2007-04-21
The kernel that Feisty uses now polls for SATA instead of IDE/ATA. Boot off of a live CD & modify your /etc/fstab to reflect sda instead of hda (also check your /boot/grub/menu.list)--I would guess that there are several threads like this....Look for UUID to setup your system the new way.

---

### Post by forlaf on 2007-04-22
Good luck, Ram. I had the same thing happen, and I gather it's been happening to allot of people with two hard drives. I was able to boot the kernel 2.6.17-10 version by putting it as the first entry in the /boot/grub/menu.lst file. I was then able to upgrade to Feisty with that kernal. It works, but I haven't been able yet to upgrade the kernal to 2.6.20-15.
David.

---

### Post by Ram Ravichandran on 2007-04-22
Something interesting...
i mounted my harddrive(hda3) using a live cd, and the /boot folder was empty!
i mounted the boot partition (hda1) and it contained all my boot files!!

Any ideas why or how to proceed from here?

---

### Post by forlaf on 2007-04-22
I'm not certain about the where your boot files are, but I wanted to say that I followed Autocrosser's reference to sda as opposed to hda. I found the last entry on [[COLOR="MediumTurquoise"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=417446&highlight=UUID") thread particularly useful. I believe I now have a fully functioning installation of Feisty.
David.

---

### Post by ecionci on 2007-04-22
check out my post above "reboot interrupted with this" I explain how I fixed this  (with a little help
from my friends).

---

### Post by Ram Ravichandran on 2007-04-22
Thanks all for your replies...I've gone ahead and changed my fstab to
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3	/               ext3    defaults,errors=remount-ro 0       1
/dev/sda2	/boot           ext3    defaults        0       2
/dev/sda1	/media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4	none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and also changed grub's menu.lst
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I still get the same message when I boot into ubuntu. should i change root to an 'sdx' form?

---

### Post by autocrosser on 2007-04-22
I'm running two drives & my /boot/grub/menu.lst looks like:

## ## End Default Options ##

splashimage=(hd1,0)/boot/grub/splashimages/soft-tux.xpm.gz

title        Feisty, kernel 2.6.20-15-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=d4c465e8-62a9-47cd-89fc-11035d656290 ro ht=on splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Feisty, kernel 2.6.20-15-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=d4c465e8-62a9-47cd-89fc-11035d656290 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Feisty, kernel 2.6.20-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-14-generic root=UUID=d4c465e8-62a9-47cd-89fc-11035d656290 ro ht=on splash
initrd        /boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title        Feisty, kernel 2.6.20-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-14-generic root=UUID=d4c465e8-62a9-47cd-89fc-11035d656290 ro single
initrd        /boot/initrd.img-2.6.20-14-generic

title        Feisty, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Edgy, kernel 2.6.17-11-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 ht=on ro splash 
initrd        /boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Edgy, kernel 2.6.17-11-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 ro single 
initrd        /boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Edgy, kernel 2.6.17-10-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 ht=on ro splash 
initrd        /boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Edgy, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 ro single 
initrd        /boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Edgy, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin  
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

You can see that Edgy & WinXP are on hd0,0 & hd0,1, while Feisty is on hd0,1. Everything is refered to by UUID.

---

### Post by mikexgough on 2007-04-22
just having a look here, I have 2 machines and went for the upgrade option through the update manager, one went through no probs (this has 2 hard drives - one for data onlt the other for Ubuntu only) the other machine dual boots M$ windozw 2k & ubuntu and has 1 hard drive - this is the one that now wont boot and was running edgy fine on 2.17 kernel, I have tried to boot the 2.17 and thats no go either..........so this is not isolated to dual Hard drive pc's
I will try some of the suggestions on here and if sucessfull repost my findings

---

### Post by theseeker213 on 2007-04-22
The Feisty Fawn upgrade also completely killed my machine. It had an error while updating samba (almost halfway through), now it does not boot up and I get

1) Errors from init about /etc/event.d/tty1 through tty5, control-alt-delete,logd,sulogin about "Unknown stanza"
2) udevd complaining that PHYSDEV* rules are deprecated
3) udevd error "specified group 'nvram' unknown'
4) udevd could not find "60-libpisock.rules"
5) udevd deprecated a direct reference to sysfs directories in 65-persistent-storage.rules

I am contemplating wiping it and doing a reinstall. This is very frustrating! I wish it could back out of an install once it finds an error, perhaps something similar to Gentoo's sandbox model.

---

### Post by autocrosser on 2007-04-23
The "unknown stanza" problem is a mal-formed line in the /etc/event.d/tty1~5 files (had that problem about 4~5 kernels ago.
 
The "udevd error "specified group 'nvram' unknown' " was also a problem for quite a while..
 
I don't know about the rest of them, I would recomend a search thru the closed Feisty Development forum-----you might find the answers there.

---

### Post by Ram Ravichandran on 2007-04-25
autocrosser,
I've been using kubuntu to make changes to be able to make my feisty work (and trust me, it does seem feisty!)
suprisingly, my changes to the menu.lst file are not stored =(
I changed the grub line directly from the command line to include the root=UUID=...line
and now, the status bar moves a little more but stops on the 'Waiting for root file system' line.

Any ideas on how i can fix this?

---

### Post by autocrosser on 2007-04-26
Double check your UUID number. I think that it is not correct for you drive/partition (each computer will be slighty different--at least I would hope so). I have posted in another thread how to obtain your UUID number, In brief:

To change your /etc/fstab to UUID:
Do a grep UUID of your /dev/whatever-it-is:

<code example>  sudo /sbin/dumpe2fs /dev/sda2 | grep UUID  Will give a result like:

dumpe2fs 1.40-WIP (14-Nov-2006)
Filesystem UUID:          1b31b23b-4db9-42c1-84a8-fd1f21992500

Take the UUID number-- include it in the /etc/fstab & /boot/grub/menu.list

Take your time & double check everything  BEFORE rebooting....

---

### Post by James Keating on 2007-04-30
The problem probably is not the script.

If on booting you get messages such as
init:/etc/event.d/tty1:13: Unknown stanza

The problem is in /etc/event.d/tty1 (and tty2 etc.)
The last two lines in mine were
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should have been
exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.

---

### Post by robcodemax on 2008-06-21
Try this one ** Linux all-generic-ide irqpoll** and you wont be getting that error message

---

### Post by alhead on 2008-06-27
> **robcodemax said:**
> Try this one ** Linux all-generic-ide irqpoll** and you wont be getting that error message

This ended 3 days of unsuccessfully attempting to partition my drive.  Thank you so much.

---

### Post by D!V00NE on 2008-06-28
hi i have a question of this type too.
i hade ubuntu 7.01 now i removed my hdd and placed it on my new pc. ubuntu boots but without interface. i mean it boots with just command line. how can i bring back the interface on new pc. is there a way. and if not if i upgrade to ubuntu 8.04 will the interface comes up or not?

thanks for helping.

---

