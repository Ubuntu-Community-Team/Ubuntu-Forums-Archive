---
title: "GRUB Error 21"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by Frenzy on 2005-09-05
Hi All, I installed Ubantu 5.04 on my system to HDB with no problems.  The installation routine found  XP and gave me the option to dual boot which I did.  Upon reboot, I got a GRUB error 21.  As I could not boot into anything I repaied the MBR so I could get back into windows.  What do I need to do to fix this and boot into Linux.  Thanks

---

### Post by plb on 2005-09-05
perhaps these links can help you

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)
[http://www.linuxquestions.org/questions/showthread.php?threadid=338856](http://www.linuxquestions.org/questions/showthread.php?threadid=338856)

---

### Post by push_harder on 2008-01-23
Google super grub and follow instructions =]

---

### Post by matey3 on 2008-02-20
I also got GRUB error 21 but after doing crtl alt del a couple of times I got no where so I turned the power off, waited a few seconds and turned it back on, the dumb thing started! shoooh.
I read Bob's comment as someone was nice enough to post the link but I have a server with SCSI drives. No IDE so it would not do me any good to go to the CMOS (although adaptec has its own bios via crtl a or m) but any way I wanted to make sure others with similar problem try shutting down as well hopefully the problem will correct itself!?

Thanks for all the help!

---

### Post by i.am.technofreak on 2008-04-21
awesome thanks for the links they were just what i needed

---

### Post by CozmoK on 2008-07-22
My Issue was when I booted from Ubuntu 8.04 CD to install on a 4GB Flash Drive.

When I was finished and removed the flash, my dual boot system spat out grub error 21.

The Hard Drive boot was looking for the Flash Drive, but it was gone.

Solution Super Grub at [http://www.supergrubdisk.org](http://www.supergrubdisk.org)

I booted from the Super Grub CD and fixed my original Dual boot system.

Thanks for the help.

---

