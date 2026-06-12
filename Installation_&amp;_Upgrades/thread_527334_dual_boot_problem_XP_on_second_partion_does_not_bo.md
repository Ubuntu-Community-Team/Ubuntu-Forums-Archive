---
title: "dual boot problem: XP on second partion does not boot"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by onthegojohn1234 on 2007-08-16
[LIST]
[*]_Here is the short version of my problem:_
[/LIST]
Just installed Ubuntu on an unused partition of my primary hard drive. It is actually the first partition, but my Windows XP Pro is installed on the second partition, and I was not using the first partition, so I decided to try out linux.

So now my WinXP is not showing up in the GRUB menu, and I can't boot the Windows OS.

[LIST]
[*]_Some additional info:_
[/LIST]
I've tried editting the menu.lst, adding:
title Windows
root (hd0,1)
makeactive
chainloader +1

Then when i choose Windows XP from the GRUB menu, the screen goes blank with the words "Starting up ..." at the top, and stays like that forever.


Using the GRUB command console, i type the same commands and the same thing happens. If i type (since there is actually a swap partition as well, so i thought i'd give it a try):
rootnoverify (hd0,2)
chainloader +1
It comes back with:
Error 13: Invalid or unsupported executable format

if i type:
makeactive
i get:
Error 12: Invalid device requested

[LIST]
[*]_More action on my part:_
[/LIST]
At first I tried to use the Recovery Console from my WinXP disk, but i couldn't get past the Administrator password.  I was able to blank out the administrator password using the Emergency Boot CD (EBCD from Mikhail Kupchik). So now I am in the recovery console, I type FIXMBR and it tells me that it could cause all my partitions to be unreadable. I got scared and didn't commit.

Remember, by windows partition is the second partition, Ubuntu is on the first partition. I can read the windows partition from Ubuntu, so I will double check all my data backups before I do the FIXMBR.

Will FIXMBR screw my whole hardrive? Will it even fix my issue?

[LIST]
[*]_Some further history of OS installations for this machine:_
[/LIST]
So it started long ago, i had XP installed on partition 1, and used partition 2 for data. Then XP got messed up somehow, and i installed XP on partition 2, and left partition 1 alone for the most part, used it now and then for data storage. This worked well for about a year and half, maybe 2 years. Then I installed Ubuntu on partition 1, during the install of which i separated partition 1 into a main partition (about 9GB) and a swap partition (about 1GB), and i left partition 2 untouched. 

That brought me to my current situation.  Any help/ideas/suggestions would be greatly appreciated.  Like i said, i can access my data from Ubuntu on partition 1, so i want to understand all options and proceed carefully before i screw things up even more.

In short, I'm looking for a solution that would leave my current XP installation intact (and bootable) on partition 2, and a bootable Ubuntu on partition 1.

---

### Post by merlinus on 2007-08-16
Post results of:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by onthegojohn1234 on 2007-08-16
**sudo fdisk -l**

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1405    11285631   83  Linux
/dev/hda2            1406       14592   105924577+   f  W95 Ext'd (LBA)
/dev/hda5            1531       14592   104920483+   7  HPFS/NTFS
/dev/hda6            1406        1530     1003999+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS

**cat /boot/grub/menu.lst**
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
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0aa12da9-7acb-4b64-8226-4078e36fbdfc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0aa12da9-7acb-4b64-8226-4078e36fbdfc ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0aa12da9-7acb-4b64-8226-4078e36fbdfc ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0aa12da9-7acb-4b64-8226-4078e36fbdfc ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0aa12da9-7acb-4b64-8226-4078e36fbdfc ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

That is the original menu.lst.  Like i said, i added numerous variations to the end to add windows XP, I removed them when they didn't work.

---

### Post by merlinus on 2007-08-16
If you look at the output of sudo fdisk -l you will see that xp is on hda5, which in terms of entries in /boot/grub/menu.lst would be (hd0,4).

Also, IIRC windows will not run if it resides on a logical partition.

-merlin

---

### Post by onthegojohn1234 on 2007-08-16
Thank you very much for your help.

So, I added the following 3 lines to menu.lst:
title		Windows XP
rootnoverify	(hd0,4)
chainloader +1

It didn't work, as i kind of expected (i think i already tried that).   Am I correct that this is because "IIRC windows will not run if it resides on a logical partition."?

Primary question:
How do i get it to work?

Secondary question:
what does IIRC mean?

thanks again.

---

### Post by dabl on 2007-08-16
Win XP requires that (a) it be on a primary partition and (b) with the "active" or "bootable" flag set, which means it is the ONLY partition on that hard drive that is set bootable.  :)

---

### Post by merlinus on 2007-08-16
Install xp on the first partition of your hdd, and make sure it is a primary.

Then create an extended partition, and install ubuntu into a logical partition within that.

IIRC = If I remember correctly

-merlin

---

### Post by onthegojohn1234 on 2007-08-16
Prior to installing Ubuntu on the first partition, my WinXP on the second partition booted worked just fine.  How is that?  Was it only working because an old, not working version of winXP was installed on the first partition?  If i were to install winXP on that first partition again, will my old winXP then be bootable?

---

### Post by onthegojohn1234 on 2007-08-16
If i install xp on the first partition, will my xp that is already installed on the second partition be bootable?

---

### Post by merlinus on 2007-08-16
Doubt it.  If I were you, I would backup data and start from scratch.

This will save you lots of agita in the future.

-merlin

---

### Post by dabl on 2007-08-16
Yep -- what merlinus said.  :)

---

### Post by onthegojohn1234 on 2007-08-16
what about this solution, which is from my same question posted on craigslist linux forum:

you wiped out the mbr in partition 1

when you have partition 1 (C: drive)and 2 (D: drive)and install xp in D the boot files are placed on C

so what you have now is two problems. you have a drive letter problem (windows was installed in D: but that drive is now considered C: by windows)
to solve this you need to boot to dos (msdos like from a win98 cd -- you may need to google boot disks, but it must be real dos not freedos)

run fdisk /mbr

this will erase the disk signature and the first time you boot into XP you will see a message like this: windows has finished installing your hardware and needs to reboot -- it has written a new signature to the disk and put the new drive letters into the registry.

this won't make xp bootable. to do that, boot your xp cd and go to recovery console

run fixboot

now it should boot xp

then you may want to reinstall grub to the MBR so that you can get the linux/xp dual boot going.

good luck

---

### Post by merlinus on 2007-08-16
No harm, at this point, in trying.  I for one would be interested to see what happens.

-merlin

---

### Post by onthegojohn1234 on 2007-08-20
Didn't work.

I got a Windows 98 bootable CD image from AllBootDisks.com.  Booted up, then typed:

fdisk /mbr

It asked me if F: was the right drive to fix, i said yes.

Rebooted the computer, it said "No operating system found", instead of: 
"windows has finished installing your hardware and needs to reboot"

So, i booted up my WinXP CD, and ran fixboot.  It said it ran successfully.  I reboot and now it says 'NTLDR' missing.

blah

---

### Post by trl on 2007-10-15
I realize it is too late for you, onthegojohn1234, but maybe this will help someone in the 
same situation.   

I had some time and a spare machine, and so I recreated the scenario.   

setup:  two partitions (two cases here two primary partitions or one primary, one logical)  

installed xp into first partition then into the second partition.  

Both windows installs recognize the drives as C: and D:  The files ntldr and ntdetect.com and boot.ini are located on the C: drive (the first partition)  I noticed here that the D: windows install had its own pagefile on D: but not ntldr, ntdetect.com, boot.ini

Then I deleted the first partition and installed Ubuntu to the empty space (auto partitioning)  

This got me an unbootable XP.  

Solution:  

As someone has said previously windows will not boot from a logical drive.  In that case what I did was resize the Ubuntu partition to make a little space and created a small primary windows partition there -- like this: EXT3(primary) NTFS(primary) Extended[swap NTFS(unbootableXP)]

Now that there is a windows primary partition do this:  

Boot the XP cd and choose recovery console 

run fixboot   (NOT fixmbr which will overwrite GRUB) (this writes the windows boot file to the MBR of the primary partition -- note: if there is no windows primary partition this will damage your Ubuntu install)  

run bootcfg /rebuild  (this writes the boot.ini file)  

Copy ntldr and ntdetect.com from the i386 folder on the cd to the windows primary partition.  

Edit menu.lst in Ubuntu to get GRUB to pass boot to windows (look at your partition numbers)  

This worked for me.  The Xp installation still identified as being on the D: drive

-tom

---

