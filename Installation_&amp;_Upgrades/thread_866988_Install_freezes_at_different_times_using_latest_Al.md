---
title: "Install freezes at different times using latest Alternate CD"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by Solidcell on 2008-07-22
So I'm trying to install the latest Ubuntu (ubuntu-8.04.1-alternate-i386.iso), and it freezes at different times every time I try to install.  Of the two times I tried this morning (I didn't have enough time for more tries), the first time got past the CD Check and then froze at the blue background with the grey bar at the bottom.  The second time got to 34% of the install (it was unpacking something).  Last night I hadn't even gotten as far as the install program, it had seg. faulted and dumped the stack after loading the Linux Kernel (after choosing to install).  This weird behavior happens with DBAN as well.  As I recall, DBAN crashes and dumps its stack once I tell it to start (or right before showing the available HDDs, I don't remember).  I also tried to install Gusty Gibbon to make sure it's not a problem with 8.04, and it also seg. faulted.

What could be the problem?  Any ideas I should try?  Thanks guys.

EDIT:

The problem was eventually resolved.  A BIOS update did the trick.

---

### Post by Pumalite on 2008-07-22
Check and fix if necessary your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Burn to disk and boot from it.

---

### Post by Solidcell on 2008-07-22
> **Pumalite said:**
> Check and fix if necessary your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Burn to disk and boot from it.

But I'm not trying to save whatever is on the HDD, I want a fresh install.  Do you mean you want me to use the CD to test the integrity of the HDD itself?  I'm fairly certain it's not a problem with the HDD as I've had the same problem when trying to install onto two different HDDs (one a SCSI, one an IDE).

---

### Post by snowpine on 2008-07-22
What are your system specs? I had similar issues on my 256mb ram computer (the bare minimum), but I just kept trying and it worked eventually. Sometimes it will get stuck in one spot for 15-30 minutes but then keep going after that.

---

### Post by zipperback on 2008-07-22
1) Please provide us the exact detailed specifications of your system.

2) Can you boot and run the LiveCD without problem?

3) Did you run the media verification test before attempting to install?

- zipperback

---

### Post by Solidcell on 2008-07-22
> **zipperback said:**
> 1) Please provide us the exact detailed specifications of your system.

2) Can you boot and run the LiveCD without problem?

3) Did you run the media verification test before attempting to install?

- zipperback

1) I'm running an HP XW8000 (with 2 cpus and 6GB of ram).  I've tried it with different amounts of ram and it's always the same problem.

2) Yea, I've booted into the non-Alternate CD's LiveCD.  It seemed to work, but it also screws up when trying to install.

3) Yea, the CDs I've used are always good.  And the memory tests start to get tons of errors late in the tests (but I've heard this is normal).

---

### Post by Solidcell on 2008-07-23
I tried it again about 6 times last night with memory from a machine that is working, and I still get the same problems (the memory may not be perfect though, but that machine was working with it).  I get to random parts of the install process before it either freezes, or I get an error and am asked which step I want to go back to.  The farthest I've gotten is past the installation and on to the setup (or whatever it was called, I forget).  It froze (or got an error) while configuring the kernel or something.  Man this is frustrating, I've never had problems like this on any machine before.

---

### Post by Solidcell on 2008-07-24
So I tried using the boot parameters "noapci nolapic" and I still got issues.  I also tried Fedora 9 and chose the text based installer and it dumped the stack before even making it to the next screen.  I just don't get it, what could possibly be doing this????

---

### Post by Solidcell on 2008-07-24
So I got a floppy today and I updated the BIOS.  Right now DBAN is at 34% and hasn't segfaulted yet.  Before the flash, DBAN would fail instantly or before 2%.  It's looking like the problem is gone, so I'll come back and report on the Ubuntu install to come in about 1-2 hours.

I don't know why I didn't try a BIOS update earlier.

EDIT:

EUREKA!  Oh thank god.  The BIOS update did the trick.  Hopefully somebody searching finds this thread in the future and saves themselves the trouble.

---

