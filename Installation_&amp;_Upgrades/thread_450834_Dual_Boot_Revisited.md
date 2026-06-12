---
title: "Dual Boot Revisited"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Mantis2600 on 2007-05-21
Hello all,

When I first installed 6.10, I attempted to get a dual boot with XP up and running.  After much struggle, my Ubuntu install has been running flawlessly for about 3 months.  My XP install will not boot an instead says "NTLDR is missing."  Because linux was working I never got around to fixing it.  Now, because of file sharing needs and gaming, I'd like to get my XP install running.  Any tips are appreciated, as I don't know where to start.

Provided below is an explination of my HDD setup:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2648    21270028+   7  HPFS/NTFS
/dev/sda2            2649       24321   174088372+   f  W95 Ext'd (LBA)
/dev/sda5            2649       24321   174088341    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2550       38914   292091152+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2               1          13      104391   83  Linux
/dev/sdb3             269        2549    18322132+  83  Linux
/dev/sdb4              14         268     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

sda1 is the windows partition, and sdb1 and sda5 are existing NTFS data stores.  


Let me know what I need to show you to make this work...Thanks in advance!

---

### Post by southernman on 2007-05-21
I can't be of great help here... more of a general hint at what you'll need to do - or at least what I think will be required.

You'll need your xp cd. Once you get the pc to boot into the windows installer you can use it to repair / rewrite your mbr. I've read about two such solutions, just not sure which is the one your going to follow:

1 - fixmbr
2 - fixboot

---

### Post by Mantis2600 on 2007-05-21
I'll wait a bit before I try that, only because I'm inclined to believe that those might mess with grub.  If I don't get any other suggestions, I'll give it a whirl.

---

### Post by southernman on 2007-05-21
> **Mantis2600 said:**
> I'll wait a bit before I try that, only because I'm inclined to believe that those might mess with grub.  If I don't get any other suggestions, I'll give it a whirl.
I highly suggest waiting on someone else to help... or searching the forum for fixmbr and fixboot, seperatly.

The post are there, waiting for you to come... ;)

Ok, I'm bored. I'll search the forum for ya.

---

### Post by southernman on 2007-05-21
Ok... here is a outside page, found during my search of the forum for [fixmbr]("http://ubuntuforums.org/search.php?searchid=20620474")

The outside link to [fix or repair mbr]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console")

I think what you really want to run is fixboot... I'll be bach!

---

### Post by southernman on 2007-05-21
Alright, found the ONE thread I was really looking for... [here]("http://ubuntuforums.org/showthread.php?t=445632&highlight=fixboot"). Warning, it's going to seen downright brutal at first but there is a happy ending... so read the whole thread.

If you want to take out the bleeding edge of fixing xp only to have to redo grub... I'd do a full backup of your ubuntu before repairing your xp.

---

### Post by Mantis2600 on 2007-05-21
This is why I've never bothered to fix this problem.  Windows always does something rediculous...

When I try to boot into the recovery console, everything goes wrong...when I select the windows hard drive, the computer restarts.  Everytime, without fail.  So this course of action (fixboot) won't work.

---

### Post by confused57 on 2007-05-21
> **Mantis2600 said:**
> This is why I've never bothered to fix this problem.  Windows always does something rediculous...

When I try to boot into the recovery console, everything goes wrong...when I select the windows hard drive, the computer restarts.  Everytime, without fail.  So this course of action (fixboot) won't work.

You might want to open a terminal and post the output of:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

---

### Post by Mantis2600 on 2007-05-22
> **confused57 said:**
> You might want to open a terminal and post the output of:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```


Sure thing

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=faad672b-ecad-4776-a896-af6c65658a3c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=faad672b-ecad-4776-a896-af6c65658a3c ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=faad672b-ecad-4776-a896-af6c65658a3c ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

---

### Post by confused57 on 2007-05-22
If I'm reading it correctly, it looks like your device.map is reversed...it should be:
```
(hd0)	/dev/sdb
(hd1)	/dev/sda
```

This may or may not be the problem, but it might be worth trying:
```
gksudo gedit /boot/grub/device.map
```

If you want, you can back it up before editing:
```
sudo cp /boot/grub/device.map /boot/grub/device.map_backup
```

---

### Post by Mantis2600 on 2007-05-22
> **confused57 said:**
> If I'm reading it correctly, it looks like your device.map is reversed...it should be:
```
(hd0)	/dev/sdb
(hd1)	/dev/sda
```

This may or may not be the problem, but it might be worth trying:
```
gksudo gedit /boot/grub/device.map
```

If you want, you can back it up before editing:
```
sudo cp /boot/grub/device.map /boot/grub/device.map_backup
```


This appeared to do nothing

---

### Post by confused57 on 2007-05-22
Your menu.lst Window's entry looks OK, you might try "rootnoverify (hd1,0)" instead of just "root (hd1,0).
If your ntldr is indeed missing, here's one possibly way to restore it:
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by Mantis2600 on 2007-05-22
no difference when using the root verify thing, I'll try the NTLDR thing, I'm just concerned it will mess with my linux install...

---

### Post by Mantis2600 on 2007-05-23
bump, anyone?

---

### Post by Mantis2600 on 2007-05-24
one last bump

---

