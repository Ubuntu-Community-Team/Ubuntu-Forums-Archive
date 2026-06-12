---
title: "Dual boot problem: XP won't start"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by ahalin on 2008-11-08
*For some unknown reason, my Ubuntu/XP dual boot machine will not let me start XP (sorry, need it for the kids' games). The grub is working fine and brings up the Ubuntu kernel and Windows XP options. Ubuntu 8.04 Hardy Heron starts without a hitch. But choosing either of the windows XP options restarts my Dell Dimension 5100 and brings me back to the grub boot options. Windows repair options chkdsk /f, /p and /r did nothing. Fixmbr and fixboot didn't work either. As per other threads on this the system info is shown below:*

sudo fdisk -l *returns:*

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11474    92164873+   7  HPFS/NTFS
/dev/sda2           15447       19452    32178195    7  HPFS/NTFS
/dev/sda3           11475       11540      530145   82  Linux swap / Solaris
/dev/sda4           11541       15446    31374945    f  W95 Ext'd (LBA)
/dev/sda5           11541       13490    15663343+  83  Linux
/dev/sda6           13491       15446    15711538+  83  Linux

Partition table entries are not in disk order
==================

sudo mount /dev/sda1 /mnt
*then* cat /mnt/boot.ini [I]returns the following:
[/I]
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT

==================
*My menu.lst looks like this (sda1 is windows hard drive, sda2 is windows documents):*

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
timeout		4

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
# kopt=root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d48c09fc-8ca0-42a4-b9b6-b1f8fd06d8cc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

*Having poked around with various fixes, including adding mount sda to the Windows options in menu.lst, I am still no closer to being able to open windows. I can see all the windows programs and files through Ubuntu, so it's still there.  Any suggestions?*

---

### Post by caljohnsmith on 2008-11-08
If booting either of the Windows selections takes you back to the Grub menu, that is usually a case of having accidentally installed Grub to the boot sector of those partitions. "fixboot" will fix that type of problem, but you did mention you ran that command all ready; but since you have two partitions, I would suggest doing the following first from your Windows Install CD:
```
map
```
That should show the drive letters for your two NTFS partitions, most likely C and D, and then you can do:
```
fixboot C:
fixboot D:
```
Or whichever the drive letters are. Try that, and then let me know exactly what happens when you try the first menu entry you have for Windows.

---

### Post by ahalin on 2008-11-09
Followed the above steps, C and D drives were the correct drives. Fixboot reported that it had written a new boot sector to both drives.

Restarted and same problem: it just reboots until I choose a Ubuntu kernel
[http://ubuntuforums.org/images/icons/icon9.gif](http://ubuntuforums.org/images/icons/icon9.gif)

---

### Post by caljohnsmith on 2008-11-09
OK, it might be that your Windows boot sector needs its file system parameters fixed. How about booting into Ubuntu, make sure the Universe repository is enabled in System > Admin > Software Sources, open a terminal (Applications > Accessories > Terminal), and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens when you boot Windows from Grub.

Also, just to clarify, is Windows XP on sda1 I assume? You don't have a Windows recovery partition?

---

### Post by ahalin on 2008-11-10
Many thanks for that.

Ok, ran the above without errors, apart from telling me that the boot and backup sectors are identical. 

I rebooted and tried both windows "kernels" (the first is the OS, the second is my [windows] documents partition). Both started with the apologetic screen saying "windows did not start normally" and gave a number of start mode options (safe mode, normal mode, etc). I tried every option and, as before, it simply reboots to the grub loader without any error messages. 

So no closer! [If it weren't for iTunes and a number of games, I would happily do without windows. I have tried the Linux alternatives and am sad to say they just don't cut it when you have 2500 music files and lots of ratings and playlists built up over the pre-Linux years. I have also tried all the work arounds for Rhythmbox, gtkPod, iTunes through WINE, etc and so am sticking to Windows for just these couple of things.]

---

### Post by Otustelija on 2008-11-10
From Grub: When you select Windows, do you see any errors briefly on the screen before getting back to the menu? Have you tried rootnoverify instead of root?

From XP recovery console: Does chkdsk report errors on the disk? What does diskpart show? Have your tried bootcfg /rebuild?

Ps. If you only needed Windows for iTunes, you could use a virtual guest XP through eg. VirtualBox. No good for games, though.

---

### Post by caljohnsmith on 2008-11-10
If nothing else works, you could do a "Windows Repair" from your Windows Install CD, and that will hopefully be enough to get Windows booting again. Note you won't lose any of your installed programs with the Windows Repair option, only if you do a complete reinstall will you of course lose all your installed programs.

---

### Post by wieoui on 2008-11-10
I have a few pc's with dual booting XP and Ubuntu 8.04 without problems except yesterday with a Dell gx150 20gb HD.
Partitionated the HD 1 primairy NTFS, 1 logical NTFS and 1 primairy unallocated. I installed XP, no problems, installed also Ubuntu and XP and Ubuntu were OK. I Updated Ubuntu, restarted, tried XP and PC started again and again after the Windows logo, but no XP. Ubuntu started normal.
Tried to reinstall XP, error screen appeared and I could not install XP. So I inserted a Hiren's bootcd but Partition Magic Pro 8.05 didn't recognize the hd, boot error. Partition Commander 9.01 did the job to partition the HD the same way as above.
Reinstalled Xp and Ubuntu, started XP and Ubuntu without problems. Starting XP again gave an network error (don't have a network) but XP started. Started Ubuntu and got no problems but a restart with XP did rebooting and rebooting the pc after the Windows logo.
Than I found caljohnsmith's solution with "testdisk" on this forum and I could manage to run XP again. I restarted XP and Ubuntu several times without problem but after installing the Ubuntu updates XP failed to start again.
Again I did "sudo testdisk" in Ubuntu terminal and the problem was fixed. I started XP and Ubuntu again a few times without problem. Hope it stays without problems but at least I know a solution to solve it now.
This pc is now handed to a child to learn pc-skills and is intended to run Ubuntu, so XP is only "for in case off..."
Strange that my other pc's with the same OS's don't have this problem.

Thanks and thanks again caljohnsmith for the solution.

wie

---

### Post by ahalin on 2008-11-13
Thanks everyone, sounds like we all know way too much about windows! Answers to the questions are:

When I select windows from the grub list there are no errors or screen funnies, it just reboots and returns to grub. 

I enabled boot logging and disabled auto restart [*to get to these options I hit the F8 key as it tries to start windows*]. However, when I bring the F8 options up again it doesn't now say "disable boot logging" or  "enable auto restart", so they don't appear to be active. 

Using windows repair:

First, I noticed that now it is finding the Windows install on the D drive, rather than C which is where it was a week ago (I think). It is calling the *My Documents* partition "C" and the XP OS partition "D" which is the reverse of what I think it was.

*chkdsk /p* finds "one or more errors" and *chkdsk /r* says it fixes them ... NOT. (To be fair, I haven't done */r* for a few days because it takes so long, but I did do *chkdsk /p* and */r* previously, followed by *fixboot* and *fixmb,* all to no avail).

*diskpart* found the five partitions

*bootcfg /scan* "failed to successfully scan disks for windows installation ... corrupt ... use chkdsk" so can't *bootcfg /add* or *bootcfg  /rebuild* so this might be it!

What is rootnoverify?

I think I'll have to try the windows repair install, although I really don't want to have to go through it and the SP updates, etc.

I'm going to give virtualisation another go, but this time XP in Ubuntu rather than the other way around. I am going to create a Ubuntu user account entirely devoted to windows. I hear you can set it so that you don't even realise you are in a virtual box.

Sadly iTunes 7 through WINE is still disfunctional.

---

### Post by ahalin on 2008-11-13
Tried all of the above again, without joy.

A Windows repair install did the trick. The system seems to be up to date, so all good.[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

Now I am playing with virtual XP in Linux Mint.

---

