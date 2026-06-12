---
title: "Install dependency problem!"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by gkhewitt on 2004-12-16
Hi there

I have been running Linux as a server OS for over a year now, and after several false starts, would like to make a foray into the Linux Desktop world, hopefully with Ubuntu!

My desktop machine is a P4 2.4GHz, 512mb ram, I have downloaded the ISO (warty-release-install-i386) and confirmed the MD5 hash. The first time I burnt the CD at full speed (48x) and began the install.

It failed during the base install with the following error (courtesy of tty4 iirc)

[code]The following packages have unmet dependencies

linux-386: Depends: linux-image-386 but it is not installable
                 Depends: linux-restricted-modules-386 but it is not going to be installed

E: Broken Packages

So I thought... corrupted installer! Rechecked MD5 (fine) and even burnt a new CD at a much slower speed, just getting the same problem. And each time I have to load up the partitionmagic bootdisks to fix the boot process to get into windows.

My original thought was that I was using the wrong package, but i386 is right (right?) and there are no other packages, i686 etc...

Does anyone have any ideas??

Many thanks!

---

### Post by Zhivago on 2004-12-16
I've suffered the exact same problem, and so far after searching the forums I found [this thread](http://www.ubuntuforums.org/showthread.php?t=3029&highlight=valid+kernel) which indicates to me we aren't alone with this install problem.

I get through the disk prep and hardware recognition, but when it gets about 85% of the way through the base setup it gives me the same dependency error you have.  I've tried installing with three different CD copies (md5sums verified) burned at 32x, 16x and 8x, each handled by their edges in textbook fashion, so I don't think it's the iso or media.  I'm at a loss, and it sucks because I really want to try out ubuntu. 

FWIW, here's my setup:

CPU: Intel Pentium 4 Northwood 1.8GHz
Motherboard: Giga-Byte GA-8IRX (845D chipset)
RAM: Crucial PC2100/DDR266 512MB DIMM
Video: GeForce4 Ti-4600 128MB AGP
Sound: Turtle Beach Santa Cruz
NIC: 3Com 3C905TX 10/100 PCI
Optical Drive: NEC 3500A 16x DVD+/-RW
Hard Drives: 80GB Maxtor (40GB NTFS: WinXP SP2, 40GB FAT32 for storage); 40GB Seagate for linux

Partition scheme:
/boot - 64MB
/swap - 512MB
/ - the rest of the 40GB

Let's hope someone here knows of a solution to this problem...

---

### Post by gkhewitt on 2004-12-17
Same, I really would like to give this a go...!

Has someone already submitted this to Bugzilla, I can't seem to find it?

Hopefully this can be resolved. What is it likely for the problem to be, since it's not a universal problem?


Cheers

---

### Post by gkhewitt on 2004-12-18
Just as an update to this, I am successfully posting this from the Live CD version of Ubuntu so I'm not sure if that elimates a few possible problems?

---

### Post by Rhodan on 2004-12-19
[QUOTE=gkhewitt]Just as an update to this, I am successfully posting this from the Live CD version of Ubuntu so I'm not sure if that elimates a few possible problems?[/QUOTE]
 Well I'm getting this exact same problem, I've installed it with a problem in VMWARE,  so it can't be the cd / cd-drive.

Any idea's ?

---

### Post by Rhodan on 2004-12-20
[QUOTE=gkhewitt]Hi there

I have been running Linux as a server OS for over a year now, and after several false starts, would like to make a foray into the Linux Desktop world, hopefully with Ubuntu!

My desktop machine is a P4 2.4GHz, 512mb ram, I have downloaded the ISO (warty-release-install-i386) and confirmed the MD5 hash. The first time I burnt the CD at full speed (48x) and began the install.

It failed during the base install with the following error (courtesy of tty4 iirc)

[code]The following packages have unmet dependencies

linux-386: Depends: linux-image-386 but it is not installable
                 Depends: linux-restricted-modules-386 but it is not going to be installed

E: Broken Packages

So I thought... corrupted installer! Rechecked MD5 (fine) and even burnt a new CD at a much slower speed, just getting the same problem. And each time I have to load up the partitionmagic bootdisks to fix the boot process to get into windows.

My original thought was that I was using the wrong package, but i386 is right (right?) and there are no other packages, i686 etc...

Does anyone have any ideas??

Many thanks![/QUOTE]
 OK I managed to solve my problem by installing Ubuntu using the expert option, for some reason this installed perfectly without any issues, and I'm now typing this from Ubuntu !

So try the expert install !

---

### Post by frank42 on 2005-01-03
[QUOTE=Rhodan]OK I managed to solve my problem by installing Ubuntu using the expert option, for some reason this installed perfectly without any issues, and I'm now typing this from Ubuntu !

So try the expert install ![/QUOTE]

Also managed to install warty using the expert mode!

I had to slow down my CDROM drive using the parameter -E 4 for hdparm.

After this it worked as expected, and I have now a running ubuntu system  :-D 

CU

---

