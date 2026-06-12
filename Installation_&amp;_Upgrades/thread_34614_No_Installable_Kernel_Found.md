---
title: "No Installable Kernel Found"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by SuperLou on 2005-05-15
I'm completely new to ubuntu and not having any luck installing.  I'm doing the i386 install from an iso burned to a cd.  The iso was verrified clean by checksum.  Near the end of base system installation I get the following error:

[!!] INstall the base system
No installable kernel found
No installable kernel was found in the defined APT sources.
The current default kernel package is 'kernel-image'.
You may try to continue though this rather strange error is probably fatal.

I have some experience with DSL but other than that I'm completely new to linux.  I would appreciate any help greatly.

Thanks,
Louis

---

### Post by Xian on 2005-05-15
Read [THIS](http://ubuntuforums.org/archive/index.php/t-23050.html) thread and perhaps try the expert installation method as described.

---

### Post by SuperLou on 2005-05-16
I read over the thread.  Does the installer have to connect to the internet to grab the kernel?  I have installed DSL (damn small linux) on the PC for the time being and it hasn't recognized my wireless card (D-Link AirPlus DWL-520+.  Is there a way around this?  My funding for a new card is as generous as my knowledge of linux.

Thanks,
Louis

---

### Post by fuit_ilium on 2005-08-12
This was a bug under Warty Warthog too, it seems. Somebody suggested that the CD-ROM drive stopped spinning after awhile during the unpacking/config process, and suggested changing your hardware setup to HD-master CD-slave on the same channel. I tried this and it didn't work. However, I tried a weird workaround: open up your box and take out the CDROM drive. At a point during the install pretty soon before you've been hanging, unplug the power from the CDROM and then plug it back in. Maybe even eject the CD and reinsert it. It's like voodoo, but it worked for me, and got me past the "no installable kernel" redscreen.

I was using an old box:

HP Pavilion 6535 w/ HP CD-Writer Plus
Celeron 466
Samsung 8.5 GB HD
64 mb RAM
HD-master, CD-slave on same channel.

BTW, this happened later in the install when I left the computer for a while and came back. It seems the installer has trouble doing I/O with the CDROM after the drive spins down b/c it hasn't been accessed for awhile.

---

