---
title: "Installing Ubuntu on 2nd HD, bootloader problem"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by jamiefoxer on 2005-03-03
Hey Guys,

I have two harddrives.  The primary one is /dev/hda and it has THREE Windows partititions, the first is the WINNT partitition with windows 2000 systemfiles, and the other two are data partititions that hold my documents, mp3s, etc.

The second harddrive is my "Linux/Unix" harddrive.  It's /dev/hdb (8.0GB)  That's the one I periodically format completely to try out new "distros'. :D 

Recently, I heard of Ubuntu.  Wanted to try it.  The install process went smoothly onto /dev/hdb, when the bootloader option appeared, I didn't want it to write to the MBR of the First harddrive /dev/hda, so I pressed ESC, and it gave me a prompt to tell it where to write the bootloader info.  I put in "/dev/hdb".  Rebooted the computer.

My BIOS is set to boot to this order (Floppy, CD-ROM, Harddrive 2, Harddrive 1).  That's so the the Linux bootloader runs first.  If I put Harddrive 1 first, it will just go into Windows.

Well, the bootloader was recognized...the Ubuntu loader showed up, complete with options for recovery, and Windows bootup.  But, when I press Ubuntu, it says "FILE NOT FOUND", and does not bootup.  I assumed that the problem was that I put the bootloader on /dev/hdb, instead of the "boot" partition of Linux.  So, format the second HD again, reinstalled Ubuntu, and this time, put in /dev/hdb1 to specify the first Linux partition on the /dev/hdb.  Rebooted.  SAME PROBLEM.

How can I get Ubuntu to boot from the 2nd harddrive...what's the location on the /dev/hdb that I should place the bootloader so that it finds the boot files of Linux?

Also...does anyone know a good utility that can be burned onto a CD (iso image) that will run a process to "clean up" a Master Boot Record?  My /dev/hda has previous bootloaders from a Mandrake Distro that wrote the bootloader to the first harddrive (from my newbie days).  I want to be able to clean the MBR of the first drive, and reinstall Windows clean, so it just boots.  Thanks. :D

---

### Post by machiner on 2005-03-03
Do it again and this time let grub be installed  where it wants. It WILL NOT impede your ability to boot to windows should you find that necessary.

There are Grub tutorials all over this forum if you continue to decide to disallow its installation.  

It's not an especially good policy security wise to boot to floppy. I'm just completely paranoid and I always set to boot to hdd-0 and password protect my BIOS.  Of course, I boot to cd-rom when trying out cool new distros (that always suck leading me back to my beloved Ubuntu, sloppy).

---

### Post by jamiefoxer on 2005-03-03
I don't want to write to the first harddrive MBR...some Linuxes (I remember Mandrake 10.0 Community did) would mess up my Windows install.

I think I'm gonna forgo bootloaders...I've had more problems than satisfaction out of them.

I'll reinstall Windows on HDA1, and let the HDA MBR list it as the OS for that drive, and then install Ubuntu in HDB and let it write the HDB MBR as the only OS on that drive, and use the BIOS order to select the system I use.  A minor annoyance...but I'd rather take a few seconds to change some boot settings on startup, than all the problems I have getting bootloaders to work (this is the 3rd Linux distro that gives me bootloader problems).

Besides....I use Linux for everything except gaming...and I rarely have time anymore to even do that...so...I don't foresee myself touching the BIOS much  :D   I'll leave it to boot Linux most of the time.

Thanks again

---

