---
title: "Can't Install on Vaio PCG-505VE"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by Adrastus on 2010-09-15
Hi all, I'm trying to do a complete install on an old Sony PCG-505 and, based on what I've learned so far, the BIOS automatically re-maps  the CARDBUS cd-rom to appear as IDE at /dev/hde instead of /dev/hdc.  Apparently, it was possible to use:

Ide2=0x180,0x386

to work around this issue with the 2.4 kernel, but this won't work with the new 2.6 kernel;
[http://ubuntuforums.org/showthread.php?t=390309 ]("http://ubuntuforums.org/showthread.php?t=390309")

I've just tried using the Alternate Installer (Debian) for a command line install but the installer gets to the partitioner and then appears to stop.  Now what??

I've left the old Win98 OS on the 6 GB hard drive expecting to be able to reformat the entire drive during the installation, but maybe that's not the case?

I have yet to successfully boot to any live CD from any distribution on this machine (including puppy and DSL) and I'm not really sure what to do at this point.

I'm a (very) new user and have little command line experience but I'm learning and I can copy-paste just as well as the next guy.

Thoughts?

---

### Post by Adrastus on 2010-09-15
Hi all,   Because this is such a specific issue, I thought I might get more responses posting in a more specific category.

I'm trying to do a complete install on an old Sony PCG-505VE:

Operating System: Microsoft Windows 98 (4.10, Build 2222)  A 
System Model: G23R2.0.0/ENU (Phoenix)
BIOS: EPP revision 9.00
Processor: Intel Celeron,  MMX, ~333MHz
Memory: 64MB RAM
Hard Drive: 6 GB
CD-ROM (external): (PCGA-CD51) Toshiba XM-1902B ATAPI PC-Card

So far, nothing has worked.  I've installed Ubuntu on newer hardware before and I've never had a problem before but I can't even get this old Vaio to run the live disk, let alone install to the hard drive.  There is no BIOS option for booting from USB and from what I've read, this BIOS doesn't have the ability to boot from USB devices of type CD or flash.  I've tried: DSL (latest release), Puppy 5.1.0, Mean Puppy (2.somethingorother), and I am currently using the alternate install CD from XUbuntu to try a command line install, but to no avail.


Based on what I've learned so far, the BIOS automatically re-maps  the CARDBUS cd-rom to appear as IDE at /dev/hde instead of /dev/hdc.  Apparently, it was possible to use:

Ide2=0x180,0x386

to work around this issue with the 2.4 kernel, but this won't work with the new 2.6 kernel; please see the following post for details written by people who actually understand this:
[http://ubuntuforums.org/showthread.php?t=390309 ]("http://ubuntuforums.org/showthread.php?t=390309")


When using the Alternate CD the installer gets to starting the partitioner and I get a screen with the prompt for starting it up and there are a bunch of question marks in the middle of the prompt screen:
[!!] Partition Disk
???   ???
<Go Back>  <Continue>

Selecting either option results in a blank blue screen with a gray bar at the bottom that I can type into but has no prompt and no effect on anything that I can see.  This is where I'm lost.


I've left the old Win98 OS on the 6 GB hard drive expecting to be able to reformat the entire drive during the installation, but maybe that's not the case?


I'm a (very) new user and have little command line experience but I'm learning and I can copy-paste just as well as the next guy.

Thoughts?

--Adrastus

---

### Post by Iowan on 2010-09-15
64 Meg ain't much to work with. I have a couple of 200 Mhz servers (CLI-only) but they have a bit more RAM.

Threads merged.

---

### Post by Adrastus on 2010-10-08
For anyone that has this problem in the future, the Ide2=0x180,0x386 command worked to get DSL loaded.  If I can find an XUbuntu version still using the 2.4 kernel I might try it.

--Adrastus

---

