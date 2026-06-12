---
title: "problems with fixmbr"
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by redfox on 2005-08-17
I botched a couple installs (am now wiser), got a grup error 15, used the system disk to run fixmbr, and lost the ability to boot into XP.  There are a handful of files I would like to retrieve off my XP partition.  I've gone in and deleted the linux partitions and ran fix mbr again.  Still no luck.  Does anybody know how to get me into XP or at least help me save those few files?

---

### Post by adwait on 2005-08-17
If you ran fixmbr, GRUB is now gone. So you should be able to boot into XP....What's the problem? WHat errr does it show now?

---

### Post by redfox on 2005-08-17
Whups.  Operating System not found.

---

### Post by adwait on 2005-08-17
For lack of a better idea..........is reinstalling XP an option?

---

### Post by vimo on 2005-08-18
I got your problem just yesterday. You have to run FIXBOOT also if you want to fix the problem.
Start the system with the WinXP Installation disk.
Choose R to enter the restore console.
Run FIXBOOT DRIVE: (where DRIVE is the letter of your main disk)
Run FIXMBR
But unfortunately these operations are not sufficient.

You have to set your original partition as ACTIVE because GRUB set to ACTIVE the actual EXT3 partition.
You can do that with FDISK or a dedicated program such as Partitio Magic (booting the system with the rescue floppy disks, of course.
(I do not remember if FDISK is available from the restore console itself)

---

### Post by redfox on 2005-08-18
Oh, it makes sense about the partition not being active.

Should I run fixboot and fixmbr before running fdisk?  Also, what are the steps for settting the drive as active in fdisk (it is available)?

---

### Post by vimo on 2005-08-18
Running Fixboot & Fixmbr before or after fdisk is the same thing I think.
Currently I don't remember all the options of Fdisk so you have to try yourself. Naturally pay attention at what your fingers do with fdisk... :-)
Sorry. I used Partition Magic...

---

### Post by redfox on 2005-08-18
Partition Magic....  I've been to the Symantec web site, but I haven't figured out what's special about it.  Could you fill me in as to the benefits?

Ok, so fdisk isn't available for me.  But I've been trying to use bootcfg to put my install first in boot order.  However, everything I'm trying in there isn't working.  The install is there, I just can't boot into it!

---

### Post by bob k on 2005-08-18
Gparted is in synaptic and is the same thing as partition magic.

---

### Post by littlepr on 2005-08-18
Redfox,

When I get home today I will tell you how to fix this. This will be soem time after 5:00 pm Eastern Time (NEW YORK).

---

### Post by vimo on 2005-08-18
I think you are not able to fix the problem because it actually depends on the partition state (active or inactive)

Symantec Partition Magic is a partition manager. It allows you to delete, create, resize, format partition and several different file sistems (such as NTFS, FAT, FAT32, Ext2, Ext3 etc.). Naturally it can make active a partition, or even hide it.
But if your system doesn't boot and you don't have the rescue diskettes than can be create with the program itself, you cannot do anything. This program helped me many times during may experiments (obviously I am not an expert).

I don't think bootcfg is useful for the task.
Maybe, if you have a old Win98 or WinME installation disk or even a Win98 boot floppy, you can find fdisk there. So, insert the win98 installation Cd, boot the system and run FDISK. After activating the support for partitions larger than 512Mb, you have 4 choices. The choice 2 is "Make a partition active (or similar).
Be sure tha Fdisk recognize your NTFS partition.

Good luck

---

### Post by littlepr on 2005-08-18
redfox,

Go here and download the ebcd emergency boot cd:


[http://ebcd.pcministry.com/](http://ebcd.pcministry.com/)

Read up on it to see how to recover your WINXP mbr. If you need any help leave me a message.

Emergency Boot CD     


EBCD – Emergency Boot CD


EBCD is a bootable CD, intended for system recovery in the case of software or hardware faults. It is able to create backup copies of normally working system and restore system to saved state. It contains the best system software ever created, properly compiled and configured for the maximum efficient use.You may download image (.ISO file) of EBCD disk and write it to CD-R or CD-RW, and then everytime you'll need convinient and powerful system tools they'll be just at hand.


EBCD will be very useful when you need to:
·     copy/move files (with long names, not necessary in CP437 encoding) from/to the disk but OS which can handle them (windows, linux...) cannot boot. In particular, you may create a backup copy of normally installed and configured Windows and later restore Windows from such backup copy. So, in the case of fault OS itself and all software and its settings can be restored in 5-10 minutes.·     perform emergency boot of Windows NT / 2000 / XP. When the loader of this OS on the hard disk is damaged or misconfigured, you are able to load OS using another, standalone loader from this CD.·     recover master boot record of HDD. This allows to boot OS after incorrect uninstallation of custom loader (LILO, for example), which made all OS on your PC not bootable.·     reallocate disk space between its partitions without data loss. Delete, move, copy to file (image) and re-create partition from file. Image transfer over network is also supported: so you may configure one PC and then make contents of harddisks of other PCs same as contents of the harddisk of the first one.·     change password of any user, including administator of Windows NT/2000/XP OS. You do not need to know the old password.·     recover deleted file, even file re-deleted from Windows Recycle Bin, and, in contrast, wipe single file or a whole disk so that it will be impossible to recover it in any way.·     recover data from accidently formatted disk. Sometimes it helps to recover data from the disk, damaged by a virus.·     recover data from a floppy disk, which is not readable by OS. Fromat 3.5" disk for 1.7 Mb sizeAlso the disk includes full set of external DOS commands, console versions of the most popular archivers/compressors.Moreover, emergency boot CD includes minimal Linux distribution (Tom's BTRT distribution) which may be very useful to a professional user.


####################################################
Basic .iso creation and burning  tutorial

####################################################

Emergency Boot CD-ROM, version 0.6.0

Copyright © 2003 Mikhail Kupchik, see [http://www.ebcd.i-am.ru/](http://www.ebcd.i-am.ru/) for more info.

 

This program is free software; you can redistribute it and/or modify it under the terms of the

GNU General Public License version 2 as published by the Free Software Foundation.

There is no warranty of any kind, however.


1. The EBCD
EBCD stands for “Emergency Boot CD-ROM”, a toolkit to created user-customized bootable CDs. It includes base package of system software intended for crash prevention and crash recovery purposes. All software included to the base disk package is distibuted freely, or under terms of GNU GPL/LGPL licenses; or is demo version of shareware product. The distribution consists of following parts:

·        makeebcd.exe — build utility

·        settings.xml — master configuration file

·        CDROM-PRO or CDROM-LITE — a folder which contains description of top-level CD-ROM contents. 

·        BOOTRDn-PRO or BOOTRDn-LITE — a folders which contains description of nth boot ramdisk contents.

 

2. How to build the CD (for impatient)
Run makeebcd.exe (without any extra command line options). Build process consists of 5 steps (none of them requires interaction with user), so just wait for a while. If all goes as expected, you should see something like this in console window:

 

 

Emergency Boot CD-ROM build utility.

makeebcd.exe build date: Aug 21 2003 17:46:56

Copyright(C) 2002-2003 Mikhail Kupchik          See [http://www.ebcd.i-am.ru/](http://www.ebcd.i-am.ru/) for more info.

 

This program is free software; you can redistribute it and/or modify it

under the terms of the GNU General Public License version 2 as published

by the Free Software Foundation.

There is no warranty of any kind, however.

 

 

STEP1: Reading primary configuration file...

STEP2: Reading user configuration files...

STEP3: Building CD-ROM filesystem...

STEP4: Building Ramdisks...

STEP5: Building CD-ROM image...Warning: creating filesystem that does not conform to ISO-9660.

 

Size of boot image is 4 sectors -> No emulation

 14.56% done, estimate finish Thu Aug 21 18:14:11 2003

 29.7 % done, estimate finish Thu Aug 21 18:14:08 2003

 43.63% done, estimate finish Thu Aug 21 18:14:07 2003

 58.14% done, estimate finish Thu Aug 21 18:14:08 2003

 72.71% done, estimate finish Thu Aug 21 18:14:07 2003

 87.23% done, estimate finish Thu Aug 21 18:14:07 2003

Total extents actually written = 34378

Total translation table size: 2048

Total rockridge attributes bytes: 2715

Total directory bytes: 8926

Path table size(bytes): 54

34400 extents written (67 Mb)

 

Build successful

Press any key to continue...

 

 

If everything is OK, then you should see a new file called ebcd.iso (by default), which was created by makeebcd.exe.

The next step you have to do is to burn ebcd.iso to the CD-ROM medium (It is recommend to burn CD-RW mediums, because it is very likely that you’ll prefer to add something to CD after you test it).

If you use Nero, start the program, close all windows that arise automatically (Wizard, New Compilation, File Browser etc.). Then open main menu item “File > Burn Image…” and open ebcd.iso file in standard file open dialog. “Write CD dialog” should appear. Insert the medium and press “OK”. 
If you use CDRWIN, choose "File Backup and Tools" after starting the program, then select an option "Record an ISO9660 image file" and pathname to image in "ISO 9660 options" / "Image filename". 
If you use any other CD-recording software, you’ll have to explore the way yourself ;). The main idea is following: you have to burn ebcd.iso as image, not as a single file or boot HDD image or whatever except “disk image”. It contains all files files, folders, boot information etc. — everything which you’ll see on the CD-ROM after you’ll burn it, i.e. it is a complete “snapshot” of ISO9660 CD filesystem. 
[Don’t try to decompile ISO file and manually write separate files which it includes to your CD, it won’t work — the problem is that bootloader expects special structure called “boot info table” properly initialized. There is only one CD-ROM filesystem builder known to me which is able to fill it; is called MKISOFS (a part of CDRTOOLS). It is compiled into makeebcd.exe utility.]

After you burn the CD, check that it contains BOOT folder and INFO_RU.TXT, INFO_EN.TXT files in root folder. (You should see them if you burned image as image, not as single file.) Then reboot your PC, and check your BIOS settings: booting from CD-ROM must be enabled. Usually, to enter BIOS setup program, you should press and hold DEL, F1 or F2 key at boot time.

If your BIOS doesn’t have CD-ROM booting option (usually, old ones, released before 1997 year), you may try to boot the CD with extra floppy disk. Boot process starts from that floppy, and then it is switched to CD-ROM. This floppy disk image is available through web site, see FAQ section. If you PC can boot normally from Windows 2000/XP installation CD-ROM, or Red Hat Linux install CD (6.0+), but can’t boot EBCD, then this tool won’t help. If you can’t, it should help not only for EBCD.


####################################################

The entire EBCDML Reference guide can be viewd here:

[http://ftp.sanguine.net/pub/sahughes/utils/rescue/ebcd/ebcd-0_6_1-pro-sfx.exe.htm](http://ftp.sanguine.net/pub/sahughes/utils/rescue/ebcd/ebcd-0_6_1-pro-sfx.exe.htm)

####################################################

---

### Post by redfox on 2005-08-18
The problem with the Win98 boot floppy is that I think my A: drive is dead.  Bummer, I know.  I just tried to use a Knoppix 3.9 disk, but that's not booting either.  I'll have to test the disk on another computer to see if it's the disk.  I don't have a Win98 CD, but I do have a WinME CD.

As for the EBCD, I'm downloading that and will give it a shot.

EBCD is in the same boat as Knoppix is.  Neither are booting.  Last shot is probably the WinME CD in order to be able to fdisk.

---

### Post by littlepr on 2005-08-18
Redfox,

Have you changed the bios boot order to boot from cdrom?

---

### Post by redfox on 2005-08-18
Yes, I made sure at the start of the process that it was booting first from the CD.  I'm sure it doesn't hurt for me to check again, though.

Yeah, checked it and tried again.  No es bueno.

---

### Post by littlepr on 2005-08-18
Redfox,


Eres hispano?

---

### Post by redfox on 2005-08-18
Nope.  Just a couple semesters of Spanish.  I did enjoy the classes, though.  Sometimes I like to throw little Spanish phrases into conversation to get odd looks.  I figured it would add to the board's international flavor.

I'm going to try the WinME CD, but after that I might be out of options, not sure.

---

### Post by littlepr on 2005-08-18
Oh,


Well it's nice to know that you paid attention in class...lol. So You downloaded the ebcd-0_6._1-po-sfx.exe file in windows and ran it to create the .rar file. Then you extracted the files and ran the makeebcd .exe to create the .iso file and burned it as an image, correct?

---

### Post by redfox on 2005-08-18
Right.  I created the .iso file and burned it correctly as an image file.  It's strange that the two .iso disks aren't working yet WinXP is.

WinME gets me to a command line.  A:/>  However, I can't switch out to the c: drive.  The command is, I believe, A:/>c:  But that is not working.  "help" will not work either.  I don't know what's up with that.

In all truth I'm just concerned about backing up 10 .odt files that I used as a journal of my summer.  It'd stink to lose them, but I'm not seeing a workaround at this point.  I don't think even PartitionMagic could save me now.  Unless I can get WinME to work for me.

Why are the Win disks working and not the .iso disks?

---

### Post by littlepr on 2005-08-18
Redfox,

I don't know why this is not working for you? What OS is it that you have installed? WinME? Win X?



What are the contents of the ebcd burnt cd.


Try this too:


 Hi,

If you can not start the PC normaly that you are trying to fix.
To verify that the machine can read the CD that you have just made, you can try the floppy boot disk that is created with Oldbios.exe.
This is available on the download page of this site. 

[http://ebcd.pcministry.com/-----downloads](http://ebcd.pcministry.com/-----downloads) link at bottom of page.
The disk does the booting of the machine then transfers control to the CD.
This will give you a better idea of the state of the CD that you have made.
If the CD works using the disk, then it may be a compatibility problem with the type of CD disk that you have used for the burn. (The lack of booting is the first thing to show up)
Have you tried to boot the CD on the machine that you made it on?
If it will not boot on this machine, then I would say that it was a bad burn.

---

### Post by redfox on 2005-08-18
I have XP installed.  I've just really scrambled the boot loader.  I have both XP and ME install disks.

I'm not sure what the contents of the EBCD are.  I just ran the exe, created the iso and burned it.

---

### Post by littlepr on 2005-08-18
redfox,

Post the contents to verify a good creation of image and burn. I just downloaded the latest, created the .iso and burnt it and it works. So I can only asuume you have a bad burn or your cdrom is not compatible with the media used. Did you test it on the pc used to burn the image?

---

### Post by redfox on 2005-08-18
The CD drive on the computer used to create the CD is currently not recognizing the CD.  However, the same computer created my Knoppix disc today and boots up with that.  It's not booting the EBCD.  I'll make another one.

How am I going to use the EBCD to save files?

Contents are:
boot (folder)
boot.catalog
info_en.txt
info_ru.txt
thanks.to

(This is the lite version.)

---

### Post by redfox on 2005-08-18
IT WORKED!  I'M IN WINDOWS!  I reburned with EBCD lite this time.  I set my primary partition as active (the stinking problem this whole time).  Booted, picked my install, and went straight to XP.

I'm now going to grab my files and nuke.  Hopefully I'll have a nice dual boot by tomorrow evening.  Thanks for all the help.  I'll keep the EBCD handy.  Again, gracias.

---

### Post by littlepr on 2005-08-18
Redfox,


Download the pro version. First we will use it to try to recover the MBR. Once you get it to load select option1. Then select the option to recover MBR. If that fails. Then reboot with the ebcd and select option9 (smart bootloader. Select to boot the drive/partition where WinXP is. If this works then back up those files you want to back up and then do a clean install of WinXP. If this fails the reboot again with disk in and elect option 10 (more info0 and read on how to recover/back existing image/partition.


Hope one of the first two work.

---

### Post by Donshyoku on 2005-08-18
I know that this is not entirely productive for this thread, but I think it can come in useful in the future...

When you want to get rid of Linux on a dual-boot, simply boot into Windows from GRUB.  Now, go to Control Panel -> Administrative Tools -> Disk Management. From here, you can look at all partitions (though it will show ext3 as uknown).  You can simply secondary-click and choose to delete the partition.  Then, boot with your Windows disc, go into the Recovery Console, and FIXMBR.  I am not genius, but it has worked for me countless times before when I dealt with what you are dealing with.

Just for future reference! :)

---

### Post by littlepr on 2005-08-18
Redfox,


De nada amigo (for nothing my friend).  But you might not have to nuke. After backing up those files reboot again without the ebcd and you should be ok. Then reboot with ubuntu install cd and try to install again.


By the way, keep that EBCD. It will come in handy plenty of times in the future. I would burn the pro version. It has more tools that you might like.

---

