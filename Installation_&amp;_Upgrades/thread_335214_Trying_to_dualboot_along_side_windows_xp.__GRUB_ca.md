---
title: "Trying to dualboot along side windows xp.  GRUB can't find my ubuntu partition"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by dis astranagant on 2007-01-10
I installed Ubuntu successfully (apparently), but it would appear that the config file generated for GRUB is wrong, and I haven't the foggiest idea how to go about fixing it so that I can boot something other than windows.  All 3 options set up for ubuntu spit out "Error 22: No such partition".

---

### Post by rsambuca on 2007-01-10
Do you have one hard drive or two?  How many partitions?  We need some info!  What happened during the installation?  What version, etc.

---

### Post by dis astranagant on 2007-01-10
2 drives currently.  One is just a data dump and grub calls it hd0.  The other has 3 partitions, 1 big ntfs one with windows on it, 1 smaller one (ext3) with the AMD64 version of 6.10 on it, and the third is a 2 GB swap partitition.  The installation went off without a hitch, beyond having to turn off a bunch of acpi stuff to get the installer to run and it locking up when I was told to remove the cd and hit enter after the install finished.

It looks like the ext3 partition and the swap partition are only visible in gparted.  trying to root (hd1,1...n) fails, while root (hd1,0) finds the windows partition. @_@

---

### Post by louieb on 2007-01-10
How weird. Usually its XP  GRUB cant find. But to get the GRUB configuration file fixed (/boot/grub/menu.lst) need info.
Boot to the live CD.
Open Applications>Accessories>Terminal.
and run ```
sudo fdisk -l
```that a lower case l as in Little.
Copy and paste the output here.

After the output is posted I will go through how to mount and edit the GRUB configuration file.
Or since you can boot windows get [ext2ifs]("http://www.fs-driver.org/") and install it in windows. Go ahead and read the dock and set it up to access your Linux partitions. Then find the file /boot/grub/menu.lst and post the content here.
 
So get those two things. 
Output of fdisk -l
and the content of /boot/grub/menu.lst
and we will get the dual boot problem fixed.

---

### Post by dis astranagant on 2007-01-10
Alright.  I'll get that in ~10-12 hours when I next have the chance.  As soon as I get my face out of an article I'm reading I'll see if remaking the ubuntu partitions and reinstalling did me any good.

---

### Post by dis astranagant on 2007-01-10
here's fdisk -l
```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26576   213471688+   7  HPFS/NTFS
/dev/sdb2           26577       30146    28676025   83  Linux
/dev/sdb3           30147       30401     2048287+  82  Linux swap / Solaris

```

and here's menu.lst

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
# kopt=root=UUID=27c5734c-fc98-49b8-8b35-4f1d9d616272 ro
# kopt_2_6=root=/dev/sdb2 ro

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
# defoptions=quiet splash irqpoll pci=noacpi nolapic acpi=off

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro quiet splash irqpoll pci=noacpi nolapic acpi=off
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I'm not sure how the windows xp boot option is working, as it is pointing at my data dump @_@

---

### Post by louieb on 2007-01-10
Sorry but I am absolutely stumped. The output of fdisk and the menu.lst configuration file match up perfectly. Both say Linux is on the 2nd partition of the 2nd hard drive. 
Out of curiosity which XP entry works. My guess is the first one doesn't work and the second on does.    The difference between the two is the hard drive GRUB is looking for XP on. The second entry is using the map option to trick XP into thinking its on the first hard drive. 

Maybe the boot order in BIOS is set to boot to sda2 first. It just doesn't make much sense. But lets try one thing before I give up. Below is an config file entry that tries to boot Ubuntu from the 2nd partition of the first hard drive. Add this and see what happens. I am curious to know.
```

title    Test Ubuntu, Swap drives
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash irqpoll pci=noacpi nolapic acpi=off
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

---

### Post by bulldog on 2007-01-10
From which drive are you booting?
Have you seen the GRUB menu?
Is it possible GRUB is on the other disk,so try to boot from the other hdd and see what happens.
Or give us the output of```
cat /boot/grub/device.map
```

---

### Post by rsambuca on 2007-01-10
I had a similar problem a while back.  For me, it was because the order of the drives in the BIOS was different than what grub was using.  I just switched the Boot order of the drives in the Bios and everything worked perfectly.  You can give it a try as it is a quick test, anyway.

---

### Post by dis astranagant on 2007-01-10
The first Windows XP option is actually the one that works, which is why I made the comment about wondering how that is possible.  I'm gonna see if grub sees more than one partition on hd0, which could answer all problems.  As for which drive has grub, both of them do, as I accidentally put it on the data dump the first time I ran the ubuntu installer.

Device.map reads as:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

---

### Post by bulldog on 2007-01-10
> **dis astranagant said:**
> The first Windows XP option is actually the one that works, which is why I made the comment about wondering how that is possible.  I'm gonna see if grub sees more than one partition on hd0, which could answer all problems.  As for which drive has grub, both of them do, as I accidentally put it on the data dump the first time I ran the ubuntu installer.

Device.map reads as:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

The important thing is,from which drive do you boot?
Your menu.lst points to hd1,1 so you have to boot from sda to let it work,in that case your second XP entry should work also.
If you boot from sdb your first XP entry work and ubuntu does not.

---

### Post by dis astranagant on 2007-01-10
I'm trying to boot from sdb.  sda is just a big ntfs data dump.  Changing the ubuntu menu items to point to hd0 fixed the issue.  I kinda wonder why it installed this "generic" version  of the kernel though.  I intended to install the amd64 version to go with my athlon 64 X2 3800+ processor.  My previous install was definitely the amd64 version...

---

### Post by bulldog on 2007-01-10
If you changed the menu.lst to hd0 your definitely booting from the same hdd as where ubuntu is installed.
So the mapping of XP is rather useless.
Have no experience with the 64bit OS so can't tell anything about which kernel it installs.

---

