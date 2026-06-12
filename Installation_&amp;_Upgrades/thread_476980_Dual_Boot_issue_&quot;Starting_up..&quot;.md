---
title: "Dual Boot issue &quot;Starting up..&quot;"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by drumstin on 2007-06-17
I have been searching and trying solutions for two days now.. Nothing seems to work like it should. .. In need of a guru to get me out of this mess: 

When trying to boot XP from Grub, it says: "Starting up..." but just hangs there...
I know it's not an issue with the XP installation because if I run fixMBR it will boot flawlessly..

In order to get back into ubuntu I have to restore Grub onto the MBR.. XP never works from Grub.. I've tried rootnoverify etc.. 

[SIZE="4"]**menu.lst: **[/SIZE]
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b0459d3c-906e-47c0-add6-c2d5ed458265 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b0459d3c-906e-47c0-add6-c2d5ed458265 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b0459d3c-906e-47c0-add6-c2d5ed458265 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b0459d3c-906e-47c0-add6-c2d5ed458265 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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
title		Microsoft Windows XP Professional
root	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

[SIZE="4"]**Result of fdisk -l:**[/SIZE]
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS
/dev/sda2            3189        6705    28250302+   f  W95 Ext'd (LBA)
/dev/sda3            6706       24792   145283827+   7  HPFS/NTFS
/dev/sda5            6593        6705      907641   82  Linux swap / Solaris
/dev/sda6            3189        6592    27342567   83  Linux

Partition table entries are not in disk order



Any help would be soooo apreciated as it's such a PAIN to restore MBR every time I want to switch. (I've also already tried putting grub into boot.ini file, no luck there...)

Thanks!!

---

### Post by merlinus on 2007-06-17
It looks like you have one hard disk.  If so, clearly something is amiss with the first windows entry in /boot/grub/menu.lst.

Try commenting out all of those lines (place a hash mark -- #) in front of them, reboot, and see what happens.

-merlin

---

### Post by drumstin on 2007-06-17
Can you be more specific? I'm not sure which lines to comment out.. 

thanks,

Drumstin

---

### Post by merlinus on 2007-06-17
> 
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


One of the reasons I am suggesting this is because the map lines refer to two different hard disks, hd0 and hd1.  So if you only have one hard disk, this may be part of the problem.

-merlin

---

### Post by confused57 on 2007-06-17
You might try hiding each of the Window's entries:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Professional
unhide (hd0,0)
hide (hd0,2)
rootnoverify (hd0,0)
chainloader +1
makeactive

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title Windows NT/2000/XP (loader)
unhide(hd0,2)
hide(hd0,0)
rootnoverify (hd0,2)
chainloader + 1
makeactive
```

---

### Post by drumstin on 2007-06-18
Yeah, sorry..  I should have taken them out.. I only had them in there because I read about that in another post, but they didn't help.. I'm editing my post..

Any ideas?

---

### Post by drumstin on 2007-06-18
I tried what you suggested.. Same thing happens.. Here is what I tried:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Professional
unhide (hd0,0)
hide (hd0,2)
rootnoverify (hd0,0)
chainloader +1
makeactive


(I completely commented out the second windows entry as it is my data partition and shouldn't even been there...)

Thanks for the suggestions.. Any other ideas would be great!

---

### Post by confused57 on 2007-06-18
I'm not sure why your Windows isn't booting from grub...you might try burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

SGD can boot either Windows or Linux and might be able to boot either of your OS, depending on which IPL you want on your mbr.

---

### Post by drumstin on 2007-06-18
I do have the Super Grub disk and love it.. It is what I am using to restore my grub installation after I run fixMBR to get into windows.. However, it will not get me into windows. I will post the error message it gives as soon as I get home from work today.. 

Thanks again for the continued help...

---

### Post by drumstin on 2007-06-18
Yeah, I just tried to boot to my windows partition from the super grub disk and it just says "boot" and sits there...

Any further ideas?

---

### Post by logos34 on 2007-06-19
> (I've also already tried putting grub into boot.ini file, no luck there...)

If all else fails to get grub to chainload the windows bootloader, I have a workaround you can try using xp to boot ubuntu.

---

### Post by drumstin on 2007-06-19
Sure, what'cha got? I don't care what bootloader I use. Anything is better then having to restore the MBR everytime I want to switch... 

I did try using "dd if=/dev/sda3 of=/mnt/share/ubuntu.bin bs=512 count=1" and then adding an entry for this file in boot.ini.. It didn't work.. But if you have another suggestion, I'd love to hear it!

Thanks!

---

### Post by confused57 on 2007-06-19
You might also try the GAG bootloader, it can be installed to the mbr, but you can try it first from a cd or floppy to see if it'll boot your Windows:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

To boot Linux, grub needs to be installed to the root partition, which you can do with the live cd(if GAG is able to boot Windows).

---

### Post by logos34 on 2007-06-19
> **drumstin said:**
> Sure, what'cha got? I don't care what bootloader I use. Anything is better then having to restore the MBR everytime I want to switch... 

I did try using "dd if=/dev/sda3 of=/mnt/share/ubuntu.bin bs=512 count=1" and then adding an entry for this file in boot.ini.. It didn't work.. But if you have another suggestion, I'd love to hear it!

Thanks!

Use this [guide]("https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29"), but modify it by adding links to boot.ini file and an entry for your ubuntu kernel in the menu.lst that is stored in C:\boot\grub.  ["Windows NT/2000/XP (using Grub)" section]

So when windows bootloader starts it pulls up boot.ini.  There will be a title link to 'Ubuntu', grldr will direct that selection to them menu.lst in C:\boot\grub and then you select your kernel there.

Get the latest grub4dos tar.gz, extract **grldr** to C:\ directory, and create new folders **C:\boot\grub**.  Extract **menu.ls**t there.  Put this entry at the top of that menu.lst:

> [B]title Ubuntu, kernel 2.6.20-16-generic
kernel   (hd0,5)/boot/vmlinuz-2.6.20-16-generic root=/dev/sda6 ro quiet splash
initrd   (hd0,5)/boot/initrd.img-2.6.20-16-generic[/B]

EDIT: or 'root=UUID=b0459d3c-906e-47c0-add6-c2d5ed458265' instead of 'root=/dev/sda6'.

Then add this line to boot.ini:
> **c:\grldr="Ubuntu Linux"**


Worked for me for netboot install from windows, and I've kept the ubuntu link on my windows bootloader just in case of disaster.

---

### Post by drumstin on 2007-06-20
Hmm.. I did it exactly as mentioned and the windows bootloader just freezes my PC when I choose Ubuntu..

Really appreciate the help from everyone..

---

### Post by logos34 on 2007-06-20
> **drumstin said:**
> Hmm.. I did it exactly as mentioned and the windows bootloader just freezes my PC when I choose Ubuntu..

Really appreciate the help from everyone..

Try choosing this entry down on that menu.lst:

> [B]title find and boot Linux with menu.lst already installed
fallback 5
find --set-root /sbin/init
savedefault --wait=2
configfile /boot/grub/menu.lst[/B]

Does that work?

---

### Post by alexathk on 2007-06-20
I come across the same problem. Hope to get a solution soon.

Thanks for all the replies;)

there is [another post]("http://ubuntuforums.org/showthread.php?t=478069&highlight=grub+windows&page=3") here with a similar problem but no better solution other than reinstalling

---

### Post by alexathk on 2007-06-20
Actually, my problem is similar to [this one]("http://ubuntuforums.org/showthread.php?t=478698&highlight=grub+windows").
It came up like this.
When I wanted to resize the windows partition by Ubuntu live CD, I accidentally delete the label of the partition, so the whole disk is like formated(in Gparted). However, I can still access my files in those partitions(seemed those label information is stored in RAM), so I used a external drive copied the whole system. After I installed the Ubuntu 7.04, and copied the files back to the primary  partition. I cannot find the winXP in the GRUB. Desperately, I reinstalled Ubuntu again. This time, the grub loader found windows. However, after choosing this option, the process would hang there. 
Does anyone have any idea to solve this problem?

Thanks

---

### Post by drumstin on 2007-06-20
To answer your question logos34, no it didn't work.. It seems like it freezes right when it I choose the option for grldr from the bootloader.. I never even get a chance to see the options in menu.lst..

---

### Post by logos34 on 2007-06-20
> **drumstin said:**
> To answer your question logos34, no it didn't work.. It seems like it freezes right when it I choose the option for grldr from the bootloader.. I never even get a chance to see the options in menu.lst..

you should be getting to the menu.lst at the very least.

If you EXTRACTED (and not just copied) grldr from the latest grub4dos to C:\ (same place as boot.ini), and you extraced menu.lst to the newly-created folder C:\boot\grub, then not sure what's going wrong. I just tried mine, works fine.  You might try the grldr and mneu.lst from the [[COLOR="DarkOrchid"]grub_for_dos-0.4.2.zip[/COLOR]]("http://sarovar.org/download.php/1138/grub_for_dos-0.4.2.zip") package instead of the 4.1 series tar.gz--I noticed the files in question are slightly different sizes. I think I may actually have used the zip.  Not sure if it will make a diff though.

My C:\boot\grub\menu.lst looks like this:

> # This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color black/cyan yellow/cyan
timeout 30
default /default

title **Ubuntu, kernel 2.6.17-11-generic**
kernel   (hd0,3)/boot/vmlinuz-2.6.17-11-generic root=/dev/hda4 ro quiet splash
initrd   (hd0,3)/boot/initrd.img-2.6.17-11-generic

title Install Ubuntu
kernel   (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   (hd0,0)/boot/initrd.gz

title Install Ubuntu (-->CD)
kernel   (hd0,0)/ubuntu/casper/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/casper/initrd.gz

...

title** find and boot Linux with menu.lst already installed**
fallback 5
find --set-root /sbin/init
savedefault --wait=2
configfile /boot/grub/menu.lst

...

So it's basically ntldr-->boot.ini-->grldr-->menu.lst-->boot ubuntu kernel.  

Would be nice if it worked for you.  Sure would save a lot hassle.  

I guess you should try next what confused57 suggested, GAG bootloader.

---

### Post by drumstin on 2007-06-21
Could the fact that my partition is NTFS be causing the bootloader not to be able to read grldr ?? I extracted and tried using grldr from the zip file you sent...

---

### Post by logos34 on 2007-06-21
> **drumstin said:**
> Could the fact that my partition is NTFS be causing the bootloader not to be able to read grldr ?? I extracted and tried using grldr from the zip file you sent...

no that's not it.  Mine's NTFS.  Actually the .zip files are for windows users. This proceedure is almost identical to what you do to start a linux netboot install FROM windows, the only difference being the kernel at the end.  I've successfully done the network install and cd approach using that method, and I added my own kernel entries to it and am able to boot ubuntu via windows bootloader. If you were getting as far as the menu.lst in C:\boot\grub but were unable to boot the kernel I could understand.  

I wish I could figure out what the problem is.  It would be an ideal workaround, at least temporarily.

---

### Post by drumstin on 2007-06-24
Forget workaround, I'd be pleased with just using that method.. It's a pain to wipe the MBR every time.. 

Thanks for trying though!

---

### Post by logos34 on 2007-06-24
this really frustrates me--this works for a lot of people and some not, and I don't know why.  You might want to google this or search the forums for a variation on this method (and I've seen a few)...one of them's gotta work.  What about GAG bootloader like confused57 suggested?  haven;t tried it out myself but maybe it will manage to boot both OS's.

---

### Post by drumstin on 2007-06-26
I did try the GAG cd before he mentioned it.. With no luck.. It will boot my linux installation, but not windows. Could SATA be the issue?

---

### Post by logos34 on 2007-06-26
> **drumstin said:**
> I did try the GAG cd before he mentioned it.. With no luck.. It will boot my linux installation, but not windows. **Could SATA be the issue**?

I wouldn't think sata is it, but could very well be wrong.

---

### Post by logos34 on 2007-06-26
I just reread through this thread again to refresh my memory, and I was thinking...first of all, do you have a floppy drive? If so wouldn't it be easiest to just come at this problem the other way and write grub to a floppy and use that to boot into linux?  Then you could leave windows bootloader on the mbr and use that to get into XP?  So you set the device boot order in the BIOS to floppy/removable-->cdrom-->hard drive.  Then when you want to boot into ubuntu you just nudge the floppy into the drive and boot; make sure it's out when you want to boot windows...Or make a Gnu grub boot cd/use supergrub cd to boot linux?  

I don't know what else to suggest because I have no idea why its freezing on grldr.  If the extracted file grldr is there in the same directory as boot.ini, NTDetect and ntldr, then it's supposed to work.

---

### Post by xzero1 on 2007-06-27
After restoring MBR, use the Super grub cd to boot Ubuntu but edit its default boot partition selection. I changed from hda(0,6) which WAS in menu.lst but didn't boot, to hda(0,5) and it booted. Super grub may not find the correct Ubuntu partition. Better, you can boot xp without restoring the MBR and use grub to boot Ubuntu. See this link:
[http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")

---

### Post by pxwpxw on 2007-06-27
Nothing to lose:
Referring to your original post menu.lst and booting from grub on MBR:
(not tried so far as I read the thread)

```

# Try adding this entry at the end and select it.
title TEST
root (hd0,1)
savedefault
makeactive
chainloader +1

```

Or find Herman.

---

### Post by Shininggg on 2008-06-06
Sorry to bring back this post but i've got the exact same problem  "Starting up..." issue after installing linux. is this fixable somehow?

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
# kopt=root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professionnel
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1


Disque /dev/sda: 200.0 Go, 200049647616 octets
255 heads, 63 sectors/track, 24321 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xd148d148

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        6421    51576651    7  HPFS/NTFS
/dev/sda2            6422       12158    46082452+  83  Linux
/dev/sda3           12159       12413     2048287+  82  Linux swap / Solaris
/dev/sda4           12414       24321    95651010    b  W95 FAT32

Disque /dev/sdb: 500.1 Go, 500107862016 octets
240 heads, 63 sectors/track, 64601 cylinders
Units = cylindres of 15120 * 512 = 7741440 bytes
Identifiant disque: 0xbd2c5c34

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1       64601   488383528+   7  HPFS/NTFS

Disque /dev/sdc: 495 Mo, 495452160 octets
16 heads, 63 sectors/track, 960 cylinders
Units = cylindres of 1008 * 512 = 516096 bytes
Identifiant disque: 0x0ccb0cca

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1               1         960      483719+   6  FAT16

---

