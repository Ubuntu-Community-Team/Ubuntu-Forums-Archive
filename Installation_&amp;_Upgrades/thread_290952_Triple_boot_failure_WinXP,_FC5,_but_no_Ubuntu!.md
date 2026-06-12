---
title: "Triple boot failure: WinXP, FC5, but no Ubuntu!"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by AVH on 2006-11-01
I have WinXP and FC5 installed on sda,(hd0). They work fine. I tried to install Ubuntu 6.10 on to an IDE drive which is master on the second IDE channel. That makes it hdc, (hd1).

The installation seemed to go fine. I did select to install Grub in the MBR. and accepted the default partioning for the drive.

I rebooted expecting my original FC5 grub setup to be trashed but it was intact and working - no sign of Ubuntu.

Hdc seems to have been partioned for a linux install but I haven't been able to mount it in FC5 to see if anything is on it. I have guessed at manual grub configuration which finds the disk but not the vmlinuz file.

Basically, I don't know if the install failed or if the problem is the grub config.

Here is my grub.conf

#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=2
timeout=30
splashimage=(hd0,1)/grub/splash.xpm.gz
#hiddenmenu
title Fedora Core (2.6.18-1.2200.fc5)
	root (hd0,1)
	kernel /vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.18-1.2200.fc5.img
title Fedora Core (2.6.15-1.2054_FC5)
	root (hd0,1)
	kernel /vmlinuz-2.6.15-1.2054_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.15-1.2054_FC5.img
title Win XP
	rootnoverify (hd0,0)
	chainloader +1
title Ubuntu 6.10 (2.6.17-10-generic)
	root (hd1,0)
	kernel /vmlinuz-2.6.17-10-386-generic root=/dev/hdc1
	initrd /initrd.img-2.6.17-10-386


Here is the output from fdisk -ls

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2385    19157481   83  Linux
/dev/hdc2            2386        2491      851445    5  Extended
/dev/hdc5            2386        2491      851413+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14692   118013458+   7  HPFS/NTFS
/dev/sda2           14693       14705      104422+  83  Linux
/dev/sda3           14706       19457    38170440   8e  Linux LVM

Disk /dev/dm-0: 36.9 GB, 36943429632 bytes
255 heads, 63 sectors/track, 4491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-1 doesn't contain a valid partition table
[root@localhost ~]#

---

### Post by louieb on 2006-11-01
I think your close. You say you can't mount hdc from fedora. Do you have a live CD you can boot from. You really need the kernel name. My guess is that the Ubuntu kernel is in /boot on hdc and not on hda. So you need to point grub to the /boot folder.
You tried:```
title Ubuntu 6.10 (2.6.17-10-generic)
root (hd1,0)
kernel /vmlinuz-2.6.17-10-386-generic root=/dev/hdc1
initrd /initrd.img-2.6.17-10-386
```
Now try this:
```
title Ubuntu 6.10 (2.6.17-10-generic)
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-386-generic root=/dev/hdc1
initrd /boot/initrd.img-2.6.17-10-386
```

---

### Post by confused57 on 2006-11-01
You could use the desktop live cd to mount your Ubuntu drive:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

You could then open /boot/grub/menu.lst, write down the entries to boot Edgy, then add the entries to your Fedora grub menu...should be similar to the entry louieb suggested.

---

### Post by AVH on 2006-11-02
I tried:

> title Ubuntu 6.10 (2.6.17-10-generic) root (hd1,0) kernel /boot/vmlinuz-2.6.17-10-386-generic root=/dev/hdc1 
initrd /boot/initrd.img-2.6.17-10-386
and any variations on the vmlinuz file name I could think of.

Same result: Error 15 : file not found.

The Ubuntu Live won't mount the drive either, its not even listed in 'Computer' as it is in FC5, which also won't mount it. Ubuntu Live, however, does see the disk in fdisk -ls

What next?

---

### Post by blabla on 2006-11-02
look at this

[http://www.smop.co.uk/node/43](http://www.smop.co.uk/node/43)

and print it out to find and boot your ubuntu straight away (it proabably put its grub in the mbr of the second hard disk)

HTH

ingo

---

### Post by louieb on 2006-11-02
Ok one last thing to try. 
[LIST]
[*]Get hold of a Puppy Linux Live CD.
[*]Once you boot to it and get to the desktop you will see an icon labeld "Drives". Click on it (Everything in Puppy is single click).    
[*]You should see a list of all your partitions on all your drives.
[*]Click on "mount" for the partition that holds Ubuntu this will open the file manager and display the folders and files on the partition.   
[*]Click on the boot folder.
[*]Now you shoud see the kernel "vmlinuz-whatever"
[*]If not snoop around It could be in the boot folder of the fedora install but I doubt it. (fedora kernels all end with FC#) Ubuntu end with something else.
[*]You now know where the kernel is and what it is named. 
[*]Point menu.lst to the kernel and initrd file.
[/LIST]
If this dosn't work I give up.

---

### Post by AVH on 2006-11-02
Following the instructions suggested by blabla from [http://www.smop.co.uk/node/43]("http://www.smop.co.uk/node/43") I used 'find /etc/fstab' and 'find /vmlinuz' at the grub command prompt. Both returned '(hd1.0)',AKA hdc1. the 'find' command could not locate any vmlinuz-2.6.... variations that I tried.

The instructions then said I should reinstall grub on the MBR. The example was a single drive setup instead of a two drive setup like mine. Where would I reinstall grub to? (hd0.0)? (hd1.0)?

And Anyway... If vmlinuz is on (hd1,0) why can't I get it to boot with the grub I've got? Is there a way I can find out the exact name of the vmlinuz file from the grub command line?

Meanwhile I'm going to follow up on the suggestions by louieb and confused57.

---

### Post by AVH on 2006-11-03
OK. I found the problem (I think). But, not the solution. Apparently there is  a problem with mixing SATA and IDE drives. I found a thread that mentions this here: [http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata]("http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata") . I started with a SATA boot drive and installed Ubuntu to an IDE drive. The Ubuntu install won't  work if the boot drive remains the SATA drive, but will work if the IDE drive is made the boot drive.

I switched my boot drive to the IDE drive and Ubuntu and WinXp worked fine - no sign of FC5 though. I took the grub info on Ubuntu from the 'menu.lst' file plugged it into the FC5 grub Ubuntu entry (and switched boot to the SATA drive) and got 'Error 17 Cannot mount partition'. I haven't yet tried to get the Ubuntu grub install to boot FC5, but thats next.

Stay Tuned.

---

### Post by ingo on 2006-11-04
This what GRUB itself has to say about error 17:

17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.       

But before we go into file systems, a quick recap (please correct any mistakes!) of your situation:

- hda (IDE, bootable with Ubuntu)
- sda (SATA, non-bootable with FC5 & XP)

So far so good.

- MBR of hda lacked FC5 entry

What did you do then? Adjust the Ubuntu entry to match your FC5 data? In this case a file system mismatch could have crept in.

I would try this if you have not done so yet: copy the FC5 GRUB entry from sda to hda.

If this does not work, please let us know which file systems you are using and even better, post both hda and sda menu.lst files.

Best of luck

Ingo

PS: I have used the GRUB command line before and yes, blabla's link explains how to find the exact file name. Ask more if you want to...

---

### Post by AVH on 2006-11-12
Sorry I let this go so long, but life got in the way.

To recap:

I would like to be able to boot Ubuntu, FC5, and WinXP from the same gurb menu. I would prefer to do this from the Sata drive.

Booting off of sda, which has WinXP in a NTFS file system and FC5 in an Ext3 file system, the FC5 grub install works for WinXP and FC5 but gets error 17 trying to boot Ubuntu which is on hdc with an Ext3 file system.

Booting off hdc with the Ubuntu grub install both WinXP and Ubuntu work fine but trying to boot FC5 gets error 17

Here is the FC5 'menu.lst':
> # grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=2
timeout=30
splashimage=(hd0,1)/grub/splash.xpm.gz
#hiddenmenu
title Fedora Core (2.6.18-1.2200.fc5)
	root (hd0,1)
	kernel /vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.18-1.2200.fc5.img
title Fedora Core (2.6.15-1.2054_FC5)
	root (hd0,1)
	kernel /vmlinuz-2.6.15-1.2054_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.15-1.2054_FC5.img
title Win XP
	rootnoverify (hd0,0)
	chainloader +1
title Ubuntu 6.10 (2.6.17-10-generic)
	root (hd1,0)
	kernel /boot/vmlinuz-2.6.17-10-386-generic root=/dev/hdc1
	initrd /boot/initrd.img-2.6.17-10-386

Here is the Ubuntu 'menu.lst':
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
# kopt=root=UUID=d0074db6-7840-4fa4-a9c5-888ba8dab9a3 ro
# kopt_2_6=root=/dev/hdc1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Fedora core 5
root		(hd0,1)
kernel		/vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd		initrd-2.6.18-1.2200.fc5.img



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



---

### Post by gn2 on 2006-11-13
It's much easier to have the OS's on different drives: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Just a suggestion...:)

---

### Post by ingo on 2006-11-15
> **AVH said:**
>  # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Fedora core 5
root		(hd0,1)
kernel		/vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd		initrd-2.6.18-1.2200.fc5.img



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Right, now it all makes sense. Thanks for posting those files. 

The above is from your ubuntu menu.lst  XP is correctly pointed to (second hard disk, first partition) while feodora is supposed to boot off the second partition of the first hard disk. No wonder, things are going haywire...

Try 

title		Fedora core 5
 root		(hd1,1)
 kernel		/vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
 initrd		initrd-2.6.18-1.2200.fc5.img

And it should boot.

---

### Post by AVH on 2006-11-15
Switching the Ubuntu menu.lst from:
> title Fedora core 5
root (hd0,1)
kernel /vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd initrd-2.6.18-1.2200.fc5.img


To:
> title Fedora core 5
root (hd1,1)
kernel /vmlinuz-2.6.18-1.2200.fc5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd initrd-2.6.18-1.2200.fc5.img

Gets "Error 1, filename must be either an absolute path name or block list"
The same thing happens when I do a similar switch in FC5 menu.lst with the Ubuntu entry.

---

