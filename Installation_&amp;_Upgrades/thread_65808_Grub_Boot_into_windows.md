---
title: "Grub: Boot into windows"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by redice on 2005-09-15
Hi all,

I just installed ubuntu on its own hd (secondary master) and had windows installed on another harddrive (primary master) after the install I boot into ubuntu without a problem :-)
When i tried booting into winxp i get a screen showing the following

Booting 'Windows NT/2000/XP (loader)'

Root (hd1,2)
Filesystem type is fat, partition type 0xc
save default
make active
chain loader +1

and it just hangs there . I cant get into the winxp at all now. Any suggestions guys

Redice

---

### Post by Lord Illidan on 2005-09-15
It would help if you can give us your grub.conf...

Go /boot from Ubuntu and see if there is a file you can read.
Give it to us here.. copy and paste.

---

### Post by redice on 2005-09-15
hi,

dont have a file called grub.cong :-S under /boot i have the following

config-2.6.10-5-386 (file)
initrd.img-2.6.10-5-386 (file)
memtest86+.bin (file)
system.map-2.6.10-5-386 (file)
vmlinuz-2.6.10-5.386(file)
grub(folder)

under /boot/grub i have

device.map (file)
e2fs_stage1_5 (file)
fat_stage1_5 (file)
jfs_stage1_5 (file)
menu.lst (file)
minix_stage1_5 (file)
reiserfs_stage1_5 (file)
stage1 (file)
stage2 (file)
xfs_stage1_5 (file)


What file should i open and input here?

Redice

---

### Post by Lord Illidan on 2005-09-15
Your menu.lst.. under boot/grub

10x for bearing with me.. I am on my Windows pc at work at the moment, and I forget the Ubuntu way of things sometimes.

---

### Post by redice on 2005-09-15
No probs mate... atleast ur taking the time to help me :-)

here goes

------------------------------
============

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb3
title		Windows NT/2000/XP (loader)
root		(hd1,2)
savedefault
makeactive
chainloader	+1

--------------------------------------------
==================

I pasted the whole thing hope thats ok

Redice

---

### Post by hashimoto on 2005-09-15
First, read my sig...

I think you need to change this (at the end):

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb3
title Windows NT/2000/XP (loader)
root (hd1,2)
savedefault
makeactive
chainloader +1

to this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb3
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

Your XP is in primary master so the reference should be (hd0,0) 
(or (hd0,1), I'm in windows now and I can't remenber. I think the first one is correct). 
To fix, open a terminal and do: 
sudo cp /boot/grub/menu.lst /boot/grub/backup.menu.lst

This makes a backup copy of the original menu.lst Then:

sudo gedit /boot/grub/menu.lst 

edit and save, then reboot. That should do it.

---

### Post by redice on 2005-09-15
LOL every one should take your sig seriously. Lucky for me im not a complete newbie......
dude that didnt work got the following error:-

root (hd0,1)

Error 22: No such partition
press any key to continue

Iv now changed it back to what it was....
Any other ideas??

Lord Illidan how bout you?? Any suggestions :-)

Redice

---

### Post by hashimoto on 2005-09-15
The sig is for a reason. ;)

Actually, are you sure your Xp is on the primary master? All properly configured (switches and so)? Because reading the menu.lst it seems that Ubuntu detected XP on the secondary disc (hdb). If it is on thge primary, it should be hda

---

### Post by redice on 2005-09-15
well if its on hdb what should i change (hd1,2) to read
well that hard drive has multiple partitions.
Cant recall what partition windows was installed on to.

Redice

---

### Post by myha on 2005-09-15
Have u tried fdisk -l to see partitions?

---

### Post by danJS on 2005-09-15
Hi,
New to Ubuntu and searching for my own problems with grub (sigh!) but think I can make a suggestion here.

The way I used to do this have windows own bootloader on its own drive (you can use a windows boot disk to restore it). If you then install grub on the linux drive and make that the primary drive, you can use the map command in the grub.conf to switch the position of the harddrives around so windows sees its drive as primary when booted.

```

title=Windows
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

```

NB: You may need to change the drive numbers here, didnt look at your config in detail.

A second advantage of this method is if you for some reason take out the linux drive windows will boot as normal off its own drive.

---

### Post by redice on 2005-09-15
Well heres the output from fdisk -l


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 2 4865 39070080 f W95 Ext'd (LBA)
/dev/hda5 2 2434 19543041 b W95 FAT32
/dev/hda6 2435 4355 15430401 b W95 FAT32
/dev/hda7 4356 4865 4096543+ b W95 FAT32

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 2 2030 16297942+ f W95 Ext'd (LBA)
/dev/hdb2 2031 2336 2457945 7 HPFS/NTFS
/dev/hdb3 * 2337 4852 20209770 c W95 FAT32 (LBA)
/dev/hdb5 2 2030 16297911 7 HPFS/NTFS

Disk /dev/hdc: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 2386 19165513+ 83 Linux
/dev/hdc2 2387 2491 843412+ 5 Extended
/dev/hdc5 2387 2491 843381 82 Linux swap / Solaris


The windows is on either hdb5 or hdb3 as one was an install that got corrupt but i still needed files from it

---

### Post by hashimoto on 2005-09-15
Well, Xp won't boot unless it thinks it is on the first primary disc. So you got to trick it thinking so. I installed XP normally on a first primary. Then I changed that disk to first secondary and used the following entry on the grub menu.lst:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

However, the mbr was on the first partition of that disc. In your case I _think_ it is on partition 3, so DanJS's suggestion could be used.

Maybe something like (now guessing):

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader (hd1,2)+1

As far as you don't mess up the linux information on the menu.lst  you'll be able to boot back to linux and fix the problem. But I'm now guessing the chainloader part, so the sig again.... 

Somebody wiser could step in here, please.

---

### Post by redice on 2005-09-15
one again mate it didnt work :-(

Redice

---

### Post by hashimoto on 2005-09-15
Here's mine (the real one). My xp is on the secondary slave and this works.

title 		windows XP
map 		(hd0) (hd1)
map 		(hd1) (hd0)
root 		(hd1,0)
makeactive
chainloader +1

Reading some other posts gives me the idea that xp's mbr has to be on the first partition of the first disk in order to work. You have so many partitions that I can't really figure out what you have there. I got to give up. Sorry I couldn't be of help and I really hope someone steps in here.

---

### Post by jackmacokc on 2005-09-15
[QUOTE=hashimoto]
Reading some other posts gives me the idea that xp's mbr has to be on the first partition of the first disk in order to work. You have so many partitions that I can't really figure out what you have there. I got to give up. Sorry I couldn't be of help and I really hope someone steps in here.[/QUOTE]

This isnt so. I run Winxp as the primary partition on a second (SATA) disk. Hoary on the first disk for me.

---

