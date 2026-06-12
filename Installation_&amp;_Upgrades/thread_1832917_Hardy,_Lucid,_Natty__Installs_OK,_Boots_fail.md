---
title: "Hardy, Lucid, Natty:  Installs OK, Boots fail"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by chertknife on 2011-08-25
If you're trying to install late versions of Ubuntu on a system using a classic PATA (parallel-ATA) IDE HD (hard drive), [COLOR=Blue]make absolutely certain the jumpering on the HD is set for CS (cable-select)[/COLOR], rather than Master or Slave.

This requires - or at least, very strongly implies - use of an 80-conductor UDMA cable to connect IDE controller to HD, and, in multiple-HD PATA systems, that the primary (#0, master) HD on an IDE channel be connected to the device plug at the end of the IDE cable, and the secondary (#1, slave) HD to the cable's intermediate or in-line connector.  See:  [http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)

Oddly, Ubuntu doesn't care whether PATA CD/DVD drive(s) on a secondary IDE controller, even with an 80-conductor UDMA cable, are jumpered for Master(/Slave) or Cable Select -  they work OK, regardless.  (I do so love consistency!)

Not my discovery, OK?  I'm stubborn, not bright.  I did a bit of exploring, and some less-than-more systematic testing, trying to trace alternatives and map reactions, but [COLOR=Red]all credit[/COLOR] (and my sincere thanks!) goes to:  
Craig, "TheRealDeal", Comment #7 (10-Jul-2008, 09:31 PM), 
[COLOR=Blue]http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-install-not-finding-ide-disk-dev-hda-650951/[/COLOR]

I spent two weeks trying to get Ubuntu up on an older system:

MB - Biostar NF 325A7-03
Processor - AMD Athlon 64, 3400+ stepping 00
RAM - OCZ4001024V3 (X2), 2 x 1 Gb, DDR 400
HD - Western Digital WD800JB-00JJC0  (80 Gb, PATA)
CD/DVD - Optiarc DDU1678A-0B, PATA
Graphics Adapter - ASUS N7600GS Silent

Without an Ubuntu install on the HD, the "Please insert a system disk..." message came up before the grind of the floppy-seek at the end of POST (power-on self test) had died away.  With an Ubuntu system on the HD, there was a brief but noticable pause before the message showed up.  Obviously, something was going on, that didn't end well.

I wanted 32-bit Lucid, but ended up trying the 32-bit Lucid "alternate" install, too, also Natty, Hardy (LiveCD from a public library book), and 64-bit Lucid, as well.  The result never varied:  Live-CDs would fire up in "Try-me," installs went uneventfully, and the installed file-systems didn't look any kind of unusual (that I know to look for, anyway).  Every effort to boot an installed system failed the same way, with the (BIOS?) message that there was no bootable disk in the CD drive.  (My boot-device order was floppy, HD, then CD.)  I even went back and installed Windoze, about 10 days into the morass, to make sure nothing dire had happened to my 80-GB PATA HD.  Windoze didn't have any problem booting up...

[COLOR=Blue]At a guess, this is applicable to all versions of Ubuntu that map PATA HD as "sfa*" [/COLOR](vs. the earlier "hda*").  I doubt it's a cure-all, but - after reading more than a thousand posts in this forum - it should eliminate some number of problems, and clear the deck for investigating and resolving the rest.

-chertknife

---

