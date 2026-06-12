---
title: "[SOLVED] Partition Installation Fails during Hardy Install"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ztirffritz on 2008-04-30
I'm installing Hardy x64 on a Dell Precision 390 Core2Duo.  The installation fails during the partitioning process almost immediately after 5% completion.  Investigation after the failure shows that it managed to create 1 small partition, presumably swap space.  Does anyone know how to troubleshoot or fix the installation?

---

### Post by dstew on 2008-04-30
Are you using the Alternate Install CD, or the Live CD? Did you check the CD integrity (menu item)?

---

### Post by ztirffritz on 2008-04-30
Live CD.  Yes I checked the CD Integrity. It passes.  I've gone into the BIOS and disabled all but one drive and set the 'SATA Operation' feature to 'RAID Autodetect / ATA'.  The default was 'RAID Autodetect / AHCI' but that didn't work either.  I let it sit over night thinking that maybe it was just taking a LONG time to configure the EXT3 file system, but that wasn't it.

---

### Post by dstew on 2008-04-30
Maybe try to make the partitions ahead of time using a separate partitioner, not part of the installation disk. The [gparted Live CD]("http://gparted.sourceforge.net/livecd.php") is worth a try.

---

### Post by ztirffritz on 2008-04-30
I can try that.  Do you know what the default Partitioning scheme is, and how much size I should allow for each partition?  The drive is 75GB.  I have 8GB RAM.

I'm thinking 2-4GB for Swap.  What about the rest?  I've never done the manual partitioning before.  I'm not dumb, but I am ignorant.

---

### Post by dstew on 2008-04-30
Do you have any other OS on the hard drive that you want to save? If not, I would recommend 1 Gb for swap, and the rest for the root system (mount point /).

---

### Post by ztirffritz on 2008-04-30
The Ubuntu installer created a 3GB swap partition.  I've heard that swap space is a function of the RAM installed.  I've also read that this ratio was a rule of thumb that applied when computers were limited to 32bits, CPUs were slower, and hard drives were smaller.  It won't hurt to have 3GB of swap will it? Most of my files are stored on a server anyway, so I'm not concerned about not having enough space locally.

---

### Post by ztirffritz on 2008-04-30
OK, I think that it has something to do with the configuration in the BIOS with the disks.  I tried installing 7.10 x64 and it failed at the same spot.  Manual installation attempt on existing partitions failed and said that there was a firmware problem of some type.  I think that I'll just open up the box and unplug one of the drives next and try again.

---

### Post by ztirffritz on 2008-05-01
I've stripped down the machine as much as I can.  When I try to install using manually created partitions from GParted LiveCD I get an error saying:

The following file did not match its source copy on the CD/DVD:

/target/lib/firmware/2.6.24-16-generic/iwlwifi-3945-1.ucode

This particular errir is often..blah blah

Basically says that it must be a bad CD or a bad drive.  The problem is that I've downloaded the file twice from two different sources (UMinn and Portland) and burned on two different computers 4 times each and always the same error.  I think that there may be something wrong with the ISO image that was offered.

---

### Post by dstew on 2008-05-01
Can you continue installing anyway? It seems that is a firmware file for wifi hardware, but you may not need it. Did you check the CD for defects (opening screen menu item)?

---

### Post by ztirffritz on 2008-05-01
Yeah I can skip the files that fail then it looks like it is reloading the X server.  As the desktop returns it locks up.  That is as far as I can get it to go

---

### Post by ztirffritz on 2008-05-01
I tried to use the DVD drive instead of the CD drive to install the OS, and I skipped the 'missing' files and now I received a error:

[Errno 30]Read-only file system

Then the message says the same thing as before about a possibly faulty cd/dvd or hard drive.  I doubt that either is the case.  I am now trying to unplug the first Hard drive and re-connect drive to try the install again.  I'm getting sick of the install routine.  I've tried it about 50 times now...

---

### Post by ztirffritz on 2008-05-01
I tried to create the partitions in GParted and it allowed me to delete the partitions, but it wouldn't allow me to create new ones.  It locked up just like the installer did.  I'm disabling the 'Execution Bit Protection' in the BIOS now.  I'm getting desperate, but maybe the Execution Disable Protection Bit feature is preventing the installer from modifying the drive?

---

### Post by dstew on 2008-05-01
It is probably the software on the installation disk that is not working well with your hardware. The gparted disk also uses a Linux kernel, though it is probably different from the installer kernel. It is possible a BIOS setting change will help, but sorry I don't have any specific recommendations for you. Maybe try installing the 32-bit system. Its drivers are more reliable.

---

### Post by ztirffritz on 2008-05-01
The whole point of 64 bit is that I want to use the 8GB of RAM that I've installed.  32bit will only see 4GB.  Maybe I'll try OpenSuSE 64 or something like that.

---

### Post by dstew on 2008-05-01
That's probably a good idea.

---

### Post by ztirffritz on 2008-05-01
I'm going to install the 32 bit version again(if I can) then try to update the BIOS.  There is an update on Dell's website.  I doubt that it will help, but at least I can say that I honestly tried EVERYTHING.

---

### Post by ztirffritz on 2008-05-01
Heilige Sheise!  I think that I got it!  The BIOS update added an 'OS Install' feature mode that enables access to only 256mb of RAM.  Apparently the installation process uses a 32bit version and can only address 3-4 GB of RAM so it chokes on the 8GB of RAM that is installed.  It is installing now.  I'm up to 50% and climbing.  Persistence pays off!  (I hope it finishes)  Thanks for the attempted help.  In retrospect this is an obvious problem, but I never would have guessed it before hand.  This is the first time that I've tried to install x64 on a system with more than 2GB of RAM.

---

### Post by ztirffritz on 2008-05-01
Oh, and I didn't need to install the 32bit version of Linux.  I was able to do the BIOS update using the LIVE CD.  It just loads the new version into a small amount of flash RAM or CMOS on the mobo, reboots, and runs the update from the on-board storage.

---

### Post by dstew on 2008-05-01
> Apparently the installation process uses a 32bit versionYes, in retrospect it would seem that the installer kernel might be 32-bit, and have problems with 8 GB memory. Probably this hasn't been seen before because very few people have that much memory. Thanks for your persistence.

---

### Post by ztirffritz on 2008-05-07
I found that the problem was related to RAM, but not in the way that I thought.  It does install with all of the RAM available.  I had at least 1 stick of RAM that was not seated properly.  I ended up re-installing several more times after this because the OS was becoming corrupted.  I finally reseated the RAM and the install process went with no problems then.  I just thought that I should clarify.  My 'solution' above did in fact work around the problem by limiting the amount of visible RAM, but the problem came back when I enabled it later.

---

