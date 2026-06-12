---
title: "D-I or Ubuntu Installer Advice Needed"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by fatshame on 2005-06-23
First time post, so I'll try to make it as coherent as possible.  I promise this is applicable to Ubuntu, so PLEASE keep reading.  Also, it's a little bit time sensitive, so please get your ideas up here...

My Task
-----------
I have been tasked with developing a script to automatically resize and partition  drives for several WindowsXP-only laptops.  Basically, it would have to detect the size of the drive, shrink the existing NTFS partition, and create several linux partitions which will eventually house prebuild RedHat images.  Please read on for progress and my question...

Progress
------------
I have familiarized myself with several tools, including ntfsresize, fdisk, sfdisk, parted, QTParted.  I am aware that several applications, including the Hoary install CD can resize NTFS partitions.

I have used SystemRescueCD to resize the NTFS and create the needed partitions.  I do this with a Perl script which runs several commands in order to  pull information from the disk, generate sfdisk input and then run ntfsresize and sfdisk.  The sfdisk imput is generated in such a way to ensure that the partitions end and begin on cylinder boundaries.

Testing Procedure
------------------------
My testing sequence is :
1) Install Fresh Copy of XP
2) Boot with SysRescCD and run the Perl Script
3) Reboot to WinXP to make sure everything is ok

(eventually I will complete the installation process, but for now I need to get the resizer working)

The Problem
----------------
My test is only successful about 60% of the time.  'Success' is booting into Windows with no problem.  In the other 40% of cases, Windows begins loading (XP logo with progress bar) and quickly 'blue screens' giving a '0x7b' failure message.  Googling the message has determined that this message is issued in the case of unexpected boot changes (boot sector viri, controller hardware change).  

I know it's not a virus because I'm working from a clean install, and there certainly is no new hardware.

My Theory
-------------
XP is detecting something which was changed during the resize process and interpereting this mismatch as a problem.  I have looked at several possibilities, but have not isolated the cause.  It's not missing NTLDR because Windows loads initially, but halts itself.  I have also tried windows recovery console, running 'fixboot'  and 'fixmbr' which do not resolve the error.

I know I'm making a mistake somewhere in the process, because the Hoary install CD and other programs like QTParted are able to successfully resize NTFS partitions with no problem.  I'm just missing a step or two somewhere.  

Here's my plea: If there is anyone out there who is well-versed in the inner-workings of the Ubuntu installer or D-I, I could really use some help in figuring out exactly HOW they are able to use ntfsresize and partman to resize XP partitions without disturbing XP.  I have been trying to browse the d-i SVN source and cannot find any "Ubuntu" installer source.  I looking to either correct my script, or  hack an installer to do what I need to.

I realize that the sensible thing to do is cut my losses and just use one of the manual methods (QTParted, Partition Magic, Acronis, etc.).  Unfortunately, these are not an option because I need the process to be automated (my department is passing this along to another department).  I have no flexibility in terms of the distro which will eventually be installed either.  Basically, all I can do is try to correct this process.

My input to sfdisk, if it helps.  Drive is 29317680 bytes, 3876 cyl, 15120 sect/cyl.
```

# partition table of /dev/hda
unit: sectors

/dev/hda1 : start=       63, size= 29302497, Id= 7, bootable
/dev/hda2 : start= 29302560, size= 29302560, Id=83
/dev/hda3 : start=        0, size=        0, Id= 0
/dev/hda4 : start=        0, size=        0, Id= 0

``` 

Thanks for reading this far.  I appreciate any help.

---

### Post by k4p0w3r on 2005-06-23
This sound awfully familiar. I have no idea where I read this because I can not find the thread again... 

Anyway, here's what I remember:
Win XP creates the swap file at the end of the space in the partition. If a resize causes it (the swap file) to become corrupt you will have boot problems. Sometimes XP fixes this automatically - sometimes it fails.
Try to disable XP swap. (Optionally delete the swap file after this is done). Reboot. Resize. Boot XP and turn swap on again.
Parted and similar moves the NTFS swap before resizing.

Sorry for not having any concrete examples at hand or more detailed links. Hope this can lead you in the right direction!

---

### Post by az on 2005-06-23
You really want to go on the debian boot irc for your question.

Contacting us

The debian-boot mailing list is the main forum for discussion and work on Debian-Installer.

We also have an IRC channel, #debian-boot on irc.debian.org. This channel is used mainly for development, but occasionally for support. If you do not receive a response, try the mailing list instead; developers will often be hacking or sleeping.

---

