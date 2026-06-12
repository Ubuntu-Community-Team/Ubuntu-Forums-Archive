---
title: "Multi-boot system for testing purpose"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by satimis on 2006-04-28
Hi folks,

I'm prepared using a newly built AMD64 box to build a multi-boot system for testing OSs.


HD - total capacity 40G
10G - WinXP (now running)

the remaining capacity is spare without partition nor FS.

I'll install Ubuntu 5.10_64 from the install CD (installer) supplied by Ubuntu on the next ~10G space of the HD.

Please advise:-
- can I run the installer to partition the remaining space of the HD during installation
- do I need to create 100M space as bootloader tabbed
- will 2G swap space be sufficient (RAM 1.024Mb)
- is 10G space sufficient for / and /home, etc.  I'm not going to create a partition for /home.  Because on installing another OS a further /home partition will make the HD complication.
- will installing ubuntu influence the running WinXP

Further suggestion will be appreciated.  TIA

B.R.
satimis

---

### Post by ajgreeny on 2006-04-28
With only 40gig to play with I think probably the best way to do what I think you want to is to use a separate home partition, which you make when you install ubuntu.  You can then use this same partition for home on all your other distro's.  You could even format it as fat32 and use it to read and write to with windows as well as linux.

40gig is not much if you really mean multiple boot machine! as most distros will end up with several gigs used for the OS + swap + tmp, etc etc.

You can allow the installer to use all the available space, or manually size and format partitions.
I don't think you need to do anything about the 100M space as bootloader.

2gig swap is too much and may not be needed at all with 1gig of ram; I'd reduce that to no more than 1gig swap which you may be able to share between all your OS's

10gig is enough for all the requirements of a linux OS, but I repeat my comments about a shared home partition.

Ubuntu will see your windows partition when you install and add it to the grub menu automatically.  On boot you can then chose which to boot to.  Install grub to your MBR for ease unless you think you may want to remove linux later.  If so you will need to have the WinXP install disk to repair your windows MBR.  If you don't have a proper WindowsXP istall disk this could be a bit more difficult.  You could always install grub to a floppy disk if you have a floppy drive on your machine.  I did this the first time I looked at linux just in case I didn't like it, as then it did not take over the booting sequence on the hard disk, and I could always go back to just windows if I wanted.

Good luck.  Let us know how you get on!

---

### Post by satimis on 2006-04-28
Hi ajgreeny,

Tks for your advice.

> With only 40gig to play with I think probably the best way to do what I think you want to is to use a separate home partition, which you make when you install ubuntu.  You can then use this same partition for home on all your other distro's.Yes common /home will be easy for approaching shared data on running different distros instead of mount/umount frequently.  But with shared /home would it add difficulty to distro upgrade?  If maintaining separate /home for each distro upgrade will be easier.  

I haven't figured out how to build a common data storage partition which can be shared amongst all distro on the same HD including Windows without mount/unmount to retrieve data.  At the same time to maintain separate /home for each Linux distro.  Have you had any suggestion?  Tks.

> 40gig is not much if you really mean multiple boot machine! as most distros will end up with several gigs used for the OS + swap + tmp, etc etc.Can swap be shared amongst distro?  Or it has to be retained separately for each distro?

> I don't think you need to do anything about the 100M space as bootloader.Sorry I don't follow.  Whether !00M space will be sufficult to cater all distro on the same HD?

> Ubuntu will see your windows partition when you install and add it to the grub menu automatically.I heard some bad news before, after installing Linux Window gone unexpectedly.

> Install grub to your MBR for ease unless you think you may want to remove linux laterYes, I'll install Grub as bootloader.

> If so you will need to have the WinXP install disk to repair your windows MBR.I have WinXP install disks, 6 of them.  However I don't understand how to repair its MBR if removing a Linux distro and why?

> You could always install grub to a floppy disk if you have a floppy drive on your machine.  I did this the first time I looked at linux just in case I didn't like it, as then it did not take over the booting sequence on the hard disk, and I could always go back to just windows if I wanted.Yes, this AMD64 box has floppy drive.  I'm prepared to have a trial.  Would 1.44Mb size be sufficient to install the bootloader?  If I understand your advice correctly, on booting Linux distro set the floppy as first boot on BIOS.  Before installing Linux distro whether I have to activate the floppy as boot?

Others noted with tks.

B.R.
satimis

---

### Post by Irony on 2006-04-28
Swap can be shared amongst distros - for example during the install of another distro you can skip the swap creation if you already have swap.

10G is plenty, simply install Ubuntu to the 10G free space and let it set up your swap and root. The root install takes up about 2G leaving plenty of space - you can always move home to its own partition later if you want as it is easy to do.

You don't need to allocate bootloader space, simply install the grub bootloader to the MBR when prompted - it will automatically point at your grub/menu.lst which can later be edited to include other distros (skip installation of grub again with other distros as it is simpler to add the entries in your ubuntu grub/menu.lst, it also avoids the possiblity of not being able to boot up). Grub should detect your windows installation but if not it can be added to the grub/menu.lst later.

Windows won't disappear (unless you rather pointedly select to install over it).

To restore the XP Bootloader;

Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc

---

### Post by jimbo-62 on 2006-04-28
Thought I would share my experience with multi boot systems. I have WinXP in a primary 80 GB partition and seven Linux distros each installed in a 5 GB partition. All of the Linux OSs use a common 512 MB swap partition. The distro which uses the most of the 5 GB is a full installation of Slackware which uses 3.5 GB. Most other distros use about 2 GB. I haven't installed ubuntu yet, so I can't comment on requirements. I use a STABLE PCLinuxOS as the "master" boot loader. I had PCLinuxOS installed Lilo to the MBR and PCLinuxOS lilo.conf controls all OS boots.

Good luck with your project, jimbo

---

