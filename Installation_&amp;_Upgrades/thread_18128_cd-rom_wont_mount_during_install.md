---
title: "cd-rom wont mount during install"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by smarthur on 2005-03-04
i decided to try ubuntu today on my old celeron box.  the cd boots fine, and as i start working my way through the install, it gets hung up when it tries to mount my cd drive.  i've tried booting with noapic and nolapic options, but no dice.  i've experienced this same problem with slackware on this particular machine, but i've had gentoo linux and debian woody working just fine from cd installs.  any thoughts would be much appreciated!

---

### Post by alastair on 2005-03-04
Try something like :

ide=nodma

as a kernel arg.

Maybe this will help ...

---

### Post by smarthur on 2005-03-04
no dice :( but thanks.

---

### Post by Elegy on 2005-03-05
I had something similar. It booted OK from the CD, went through the language & keyboard stuff and then, after doing the hardware detect bit, it said that it couldn't find the CDROM. The motherboard is fairly new and the CDROM is a standard IDE device. I have successfully installed Fedora Core 3 on the same hardware.

---

### Post by ubuntu_seeker on 2005-03-06
I have the same problem. I'm booting Ubuntu Hoary Live CD (Array 6 and the MD5SUM checked out fine) and it boots ok and begins detecting various pieces of hardware but coughs on the CD-ROM drive, meaning, it could not find a driver for my CD-ROM so then I have to stop the installation,  .

I've seen others post about this problem in several places, but still there have been no replies... hoping for one soon.

My hardware is: Dell XPS Gen 3 (Pentium 4 3.6 GHZ), DDR-2 RAM, SATA 7200 rpm hard drive.

The CD-ROM is a CD / DVD RW combo drive.

MEPIS had no problem detecting my CD drive. And the drive works just find in Windows XP SP2.

Thanks for any ideas!!! :^D.

I'd really like to be able to try out the live CD before installing Ubuntu. I'd much prefer to go with Hoary since Warty is kinda out of date by now. Tho' I suppose I could try Warty and do the upgrade perhaps.

Anyway, thanks again! 

[QUOTE=Elegy]I had something similar. It booted OK from the CD, went through the language & keyboard stuff and then, after doing the hardware detect bit, it said that it couldn't find the CDROM. The motherboard is fairly new and the CDROM is a standard IDE device. I have successfully installed Fedora Core 3 on the same hardware.[/QUOTE]

---

### Post by ardvark on 2005-03-08
I believe I saw somewhere that Hoary array 6 did not have the fixes in it for SATA drives. I know array 6 wouldn't load on my PC with SATA , with same problem.  Looking back at some of the bug reports, this problem has been around since last September.  You'd think this would be fixed by now.

---

