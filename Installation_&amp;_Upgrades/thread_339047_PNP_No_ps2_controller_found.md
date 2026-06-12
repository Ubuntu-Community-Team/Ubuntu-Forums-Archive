---
title: "PNP: No ps2 controller found"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by teust on 2007-01-15
Hi all,
      
      trying to install ubuntu but installation stalls at this point, PNP: No PS/2 Controller found.  Has anyone any experience with this problem.  My keyboard and mouse are connected through USB.  I've tried to disks now with the same issue arising.  Should I disable PNP in the bios??  I'm using a dell xps 700, intel core 2 2.66ghz,  2 gig RAM, 2x250 SATA drives.

Thanks
T

---

### Post by teust on 2007-01-15
ok, I experimented and tried to install freespire and opensuse.  Same thing happened I get to the initial menu but when I choose install or start it just hangs and is unresponsive.  Anyone any ideas.  I'm a newb so would appreciate any tips.

---

### Post by teust on 2007-01-16
Still having same problem.  Did install in text mode worked fine, restarted booted ubuntu get starting up....  then nothing.  Shut down restarted went into ubuntu recovery mode and it freezes on pnp: no ps/2 controller found. probing ports directly.  Anyone??  :confused:

---

### Post by jlstyle on 2007-03-25
I have a similar setup (Dell XPS, 2g ram, 3 sata drives, USB mouse/keyboard) with the same issue.  The last line I see during startup is:

PNP: No PS/2 controller found.  Probing ports directly.

Then the system hangs, and I have to do a cold restart.  Were you able to resolve this problem?  I'll keep investigating...

---

### Post by snthelion on 2008-07-13
I also have the same issue, but had no issues on my older machines which had PS/2 mouse and keyboard and IDE disks.

Is this is lmitation of ubuntu ? I don't have PS/2 ports (both my newer machines don't have these) and both are SATA, so am i out of luck here ?

Please help.

---

### Post by pmlxuser on 2008-07-13
For problems above incase of SATA. Change the bios setting on disk mode to IDE. Ubuntu install perfectly after that about PS/2 have to check (ie have no idea)

---

