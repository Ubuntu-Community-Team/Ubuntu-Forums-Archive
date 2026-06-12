---
title: "Problem with Dual boot.  Windows doesn't load."
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by trancehed on 2006-11-10
I decided to install Ubuntu on a friends recommendation.  Decided to go with a dual boot since I'm not ready to completely switch yet.  I decided that since I was going to set up the dual boot, I might as well reinstall Windows (XP Pro) first since it had been a while.  And I plan on only installing minimal windows programs.  

I went through the installation of 6.10 rather easily.  I was most worried about partitioning, but I let it partition automatically which made things very easy.  Much to my delight, when I booted up after install, I was greeted with the GRUB menu which displayed options to load both Ubuntu and Windows (plus the various other options).  I booted into Ubuntu no problem.  I was very happy.  Easy as cake.  

Later that night, I decided to boot into Windows.  Much to my dismay, windows won't boot.  I chose Windows from GRUB, and it says "loading windows.." (or something like that) Just like it did for Ubuntu.  But it stays like that indefinitely.  Until I reboot and chose to load Ubuntu.

I searched various documentation, including the forums.  For days now.  My best guess was that GRUB was looking in the wrong partition.  Seemed like an easy fix to a common problem.  Unfortunately, it IS looking in the right place (disk 1, partition 1).

Any ideas?  It's been pretty frustrating.  I figured that I would be able to use Windows while I began to learn Ubuntu.  Making the transition fairly easy.  Unfortunately I hadn't planned on not being able to access windows :(

---

### Post by happy hacker on 2006-11-10
i would install xp last thats what i did had no problems

---

### Post by bulldog on 2006-11-10
How many hard disks do you have?
If you have more than one and ubuntu and windows are on separate hard drives it could be a mapping issue.

Can you give us the output of```
sudo fdisk-l  (l as in like)
```

And as we are looking into it can you give us your menu.lst as well? :D

---

### Post by foxmulder881 on 2006-11-10
> **happy hacker said:**
> i would install xp last thats what i did had no problems

Sorry, you're wrong with saying this. Always install Windows first and then Ubuntu. If you install Ubuntu first and then Windows, the Windows install will write over the MBR and you will more than likely lose your GRUB loader.

How you avoided this by installing Ubuntu first, I don't know!

---

### Post by trancehed on 2006-11-10
> **bulldog said:**
> How many hard disks do you have?
If you have more than one and ubuntu and windows are on separate hard drives it could be a mapping issue.

Can you give us the output of```
sudo fdisk-l  (l as in like)
```

And as we are looking into it can you give us your menu.lst as well? :D

I'm on my way home from work and will post the requested information when I get there (in about an hour).

Both Ubuntu and Windows are on the same drive.  Windows is in partition 1, Ubuntu on partition 2.  Initially, when I set everything up, I only had the one drive plugged in.  As I'm always paranoid of losing data when I install/format drives.  But I do have a total of 4 drives in my tower.  Ive tried with all drives plugged in, and with just the boot drive.  Doesn't seem to make a difference.  Figured it wouldn't but trying everything I can think of :P

---

### Post by trancehed on 2006-11-10
I doubt it makes a difference, but I have also adjusted the partition sizes last night using gparted.  Shouldn't really relate though as the problem was the same b4 and after.

---

### Post by trancehed on 2006-11-10
also, again probably shouldn't make a difference, but in case it does.. I didn't do all of the windows updates after installing windows.. just the first batch..  I have an old CD and it takes hours to update everything so I decided to wait to do all of the updates until I knew the Ubuntu was working.  Really don't see how that would cause this.  But figured I'd mention it.

---

### Post by trancehed on 2006-11-10
Here...
> Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       18116   145516738+   7  HPFS/NTFS
/dev/hda2           18117       36480   147508830    f  W95 Ext'd (LBA)
/dev/hda5           18117       36480   147508798+   7  HPFS/NTFS

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       18116   145516738+   7  HPFS/NTFS
/dev/hdb2           18117       36480   147508830    f  W95 Ext'd (LBA)
/dev/hdb5           18117       36480   147508798+   7  HPFS/NTFS

Disk /dev/hde: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        1298    10426153+   7  HPFS/NTFS
/dev/hde2            1299        3507    17743792+  83  Linux
/dev/hde3            3508        3736     1839442+   5  Extended
/dev/hde5            3508        3736     1839411   82  Linux swap / Solaris

Disk /dev/hdf: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hdf2            6375       25496   153597465    7  HPFS/NTFS
/dev/hdf3           25497       36481    88237012+   7  HPFS/NTFS


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
# kopt=root=UUID=464393b2-9324-4943-8bf0-bf1c81b982da ro
# kopt_2_6=root=/dev/hde2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hde2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hde2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by foxmulder881 on 2006-11-10
I'd suggest a complete reinstall of both OS. By the time you figure out the source of the issue, you could have had both of them reinstalled. Providing you don't run into the same issue that is.

---

### Post by rvickers on 2006-11-10
You might try XP repair console which is boot XP cd and f8.
Once you're in repair console, do fixmbr. If it boots, then XP is ok.
There's tricks on how to reinstall grub but I would just reinstall ubuntu since it's so easy. Good Luck...

---

### Post by trancehed on 2006-11-10
> **foxmulder881 said:**
> I'd suggest a complete reinstall of both OS. By the time you figure out the source of the issue, you could have had both of them reinstalled. Providing you don't run into the same issue that is.

yeah I'm willing to do that but only as a last resort.  Especially since I don't know for sure it will fix the problem.

---

### Post by trancehed on 2006-11-10
> **rvickers said:**
> You might try XP repair console which is boot XP cd and f8.
Once you're in repair console, do fixmbr. If it boots, then XP is ok.
There's tricks on how to reinstall grub but I would just reinstall ubuntu since it's so easy. Good Luck...

do you mean the Windows CD?  Or a boot disk?  I tried a boot disk but I can only find instructions for how to make one on a floppy.. and I don't have a floppy drive.  I tried just doing it on a CD but it doesn't boot.

if you mean from the windows CD, please explain a bit more.. When do I hit f8?  do you mean repair install?  It's a brand new install and it worked prior to loading ubuntu.

---

### Post by foxmulder881 on 2006-11-10
If you wipe all drives of their current partitions and reinstall again from scratch installing Windows first and then Ubuntu, you should have no worries. You have nothing to lose from the position you're in now.

---

### Post by trancehed on 2006-11-10
> **foxmulder881 said:**
> If you wipe all drives of their current partitions and reinstall again from scratch installing Windows first and then Ubuntu, you should have no worries. You have nothing to lose from the position you're in now.

I'm definitely not wiping all my drives.. I have over 500g of data.  I could wipe my boot drive.. but again that's pending there is no other solution.  It certainly sounds like a last resort to me..

---

### Post by foxmulder881 on 2006-11-11
> **trancehed said:**
> I'm definitely not wiping all my drives.. I have over 500g of data.

Yeah, sorry, that's what I meant. Stupid me just phrased it wrong. Obviously only the boot drive.

---

### Post by pradish on 2006-11-11
Hi,
  I did a lil mess up with my system. I was unaware that if i install MS OD after Ubuntu i will loose GRUB. I installed Windows Server 2003 and it now just boots to Windows and there are no option given to boot Ubuntu. I have 2 HD. Windows is on hda and Ubuntu is on hdb. Could some one assist me in re installing just the GRUB?

---

### Post by Herman on 2006-11-11
[Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") can boot all kinds of operating systems and install various bootloaders to hard disks or partitions and help you solve most booting problems.
It's free and it's a very small download. It should boot either Windows or Linux for you for now, until you get tie to sort things out properly.
Super Grub Disk can be used in GUI (menu) mode, or you can always drop to a Grub [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") at any time by pressing your 'c' key. Grub's Command Line Interface provides access to many clever procedures that can be applied using Grub commands that you can use for troubleshooting and booting any bootable system. Normally, you can also get a GRUB Command Line from your installed Grub, but not always. Grub's menu.lst file uses pretty much same commands as are good for Command Line Grub, so if you take notes while you are investigating your computer with Command Line Grub, you can use the same commands for editing your menu.lst after you boot successfully. 

Trancehed, it looks to me as if you Grub's menu.lst is configured as if you have Windows in partition 1 in your first hard disk, and Ubuntu in partition 2.
Your fdisk output says your number 1 and 2 disks are both data disks, by the looks of it, and your operating systems are on disk 3, with another data disk as disk 4.
I'm surprised your Ubuntu boots at all, much less Windows. Using Grub's Command Line interface will be the best way to find out what's wrong.
Unless you can unplug your hard disks again, and replug and jumper them as necessary to make your operating systems disk your first hard disk again, you can conifgure grub to boot it as a third hard disk or whatever. You will need map commands to trick Windows into thinking it's actually on a first hard disk, or it won't boot. For details, just keep reading that link I already gave, [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), it's all there.

pradish, you can either use Super Grub Disk for restoring Grub to MBR in either of your hard disks, or if you have a Ubuntu or any Linux LiveCD, you can also do it this way, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

Regards, Herman :D

---

### Post by trancehed on 2006-11-12
thanks guys.  I ended up having a friend help me.  He suggested the windows partition may have been screwed up when i resized it.  So he had me reinstall everything.. and I partitioned windows the size I wanted it when I installed it, and then manually partitioned all the ubuntu partitions and everything seems to work fine now :)

---

### Post by gn2 on 2006-11-13
This may have helped: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by blue_skwid on 2006-11-24
I have the exact same problem. One hardrive, windows on the first partition ...

I really would like to avoid re-installing everything :( Should i try to fix the mbr from windows ? Then reinstall grub ?

Thanks for your help !

---

### Post by Psquared on 2006-11-24
> **Herman said:**
> [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") can boot all kinds of operating systems and install various bootloaders to hard disks or partitions and help you solve most booting problems.
It's free and it's a very small download. It should boot either Windows or Linux for you for now, until you get tie to sort things out properly.
Super Grub Disk can be used in GUI (menu) mode, or you can always drop to a Grub [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") at any time by pressing your 'c' key. Grub's Command Line Interface provides access to many clever procedures that can be applied using Grub commands that you can use for troubleshooting and booting any bootable system. Normally, you can also get a GRUB Command Line from your installed Grub, but not always. Grub's menu.lst file uses pretty much same commands as are good for Command Line Grub, so if you take notes while you are investigating your computer with Command Line Grub, you can use the same commands for editing your menu.lst after you boot successfully. 

Trancehed, it looks to me as if you Grub's menu.lst is configured as if you have Windows in partition 1 in your first hard disk, and Ubuntu in partition 2.
Your fdisk output says your number 1 and 2 disks are both data disks, by the looks of it, and your operating systems are on disk 3, with another data disk as disk 4.
I'm surprised your Ubuntu boots at all, much less Windows. Using Grub's Command Line interface will be the best way to find out what's wrong.
Unless you can unplug your hard disks again, and replug and jumper them as necessary to make your operating systems disk your first hard disk again, you can conifgure grub to boot it as a third hard disk or whatever. You will need map commands to trick Windows into thinking it's actually on a first hard disk, or it won't boot. For details, just keep reading that link I already gave, [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), it's all there.

pradish, you can either use Super Grub Disk for restoring Grub to MBR in either of your hard disks, or if you have a Ubuntu or any Linux LiveCD, you can also do it this way, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

Regards, Herman :D

Herman - I tried using Super Grub but couldn't get Windows to boot. On my system I have 1 harddrive. Previously I had Vista RC1 and Ubuntu 6.06 dual booting with no problem. I dist-upgraded to Edgy and it changed my Grub settings. I tried to manually insert the chainloader + configuration but it won't boot windows. Depending upon how I set the root partition it either gives me error 17 or says it can't mount the partition.

In fstab, the Windows (NTFS) partition is commented out. Does Grub look at fstab when it tries to boot?

---

### Post by Psquared on 2006-11-24
Well I'll be danged. I fixed it. Didn't need Super Grub or anything else fancy. Just elbow grease. :) 

Root was (hd0,1) not (hd0,0)
Didn't need savedefault

This baby's bootin like there's no tomorrow. No more ](*,)

---

