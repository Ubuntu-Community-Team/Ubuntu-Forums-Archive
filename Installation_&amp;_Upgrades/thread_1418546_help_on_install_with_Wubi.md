---
title: "help on install with Wubi"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by hyattjon on 2010-02-28
OK, I decided to try ubuntu again after a couple of years on Vista. 
 
I installed ubuntu-8.10-desktop-amd64.iso with Wubi onto an empty 35gb partition. It works fine, but when I go to update either individual updates or to Ubuntu 9 it says no space available, presumably as the terminal says running from a live CD. 
 
How do I change the install to a full version on the HD and not lose the dual boot option with Vista? I don't care if I have to start again, I just want to end up with a dual boot system with Ubuntu installed on the HD. 
 
Also, when I run the Ubuntu installer the partition manager is blank so I cannot continue, presumably also because at the moment I am in "live CD" mode?

---

### Post by tommark on 2010-02-28
I had the same problem, and finally decided to stop using Wubi.
First clean up your win machine: If you're short on space, first get rid of unnecessary crap. then de-frag. You should have AT LEAST 5Gig to install UU 9.10 so it can run comfortably.

 I downloaded a new version of Ubuntu 9.10, burned the ISO, then set my XP machine to boot from the CD by hitting F2, F8 or F12 at the initial boot, then going to the "boot" section and choosing "CD", or move it above "Vista" in the list of choices.
I booted up and after about a thousand clicks and rumbles the computer came up with UU running, but from the CD. But.. there is now the option to "install" UU.
Just choose this option, install it - again about a thousand clicks and rumbles, and now you'll have UU 9.10 running as a dual-boot machine. When you first turn your box on, you'll get the choice of Vista or a selection of UU versions.

---

### Post by garvinrick4 on 2010-02-28
Wubi installs as a folder in Windows. It is right next to Users in C: drive.
Do not understand Wubi in 35 gig partition?
Should be an uninstall in Wubi folder use it not add and remove programs. Sometimes
Wubi leaves itself in Windows bootmanager if not from its uninstall option in it's folder.
Then start normal install.

---

### Post by hyattjon on 2010-03-01
So am I being told that (ignoring my aborted attempts so far) that I can simply boot my Vista PC with the 9.10 cd to install Ubuntu to a dedicated partition and get a dual boot system automatically?

---

### Post by Mark Phelps on 2010-03-01
> **hyattjon said:**
> So am I being told that (ignoring my aborted attempts so far) that I can simply boot my Vista PC with the 9.10 cd to install Ubuntu to a dedicated partition and get a dual boot system automatically?

If what you intend to end up with is two separat installs -- Vista to one partition and Ubuntu to another -- what you're being told is incorrect.

Using the Ubuntu installer to shrink your Vista OS partition to make room for the other install is risking corrupting the Vista OS and rendering it unbootable.

However, is you really want to do a Wubi install (install INSIDE Windows), then you insert the CD while Windows is running and install from there.

It's better (and safer) to use the Vista Disk Management utility to shrink the OS partition, leaving the remaining space unallocated.

Then boot from the Ubuntu CD and install to the unallocated free space.

However, if you really do want to install inside Windows, then insert the CD while Windows is running, let it auto-launch, and install from there.

---

### Post by hyattjon on 2010-03-01
Problem solved, I am just slow sometimes. The partition manager from the Ubuntu installer is great, I just chose to sort out my own partitions, it allowed me to use a free space I had reserved for it, installed fine and I have got what I wanted, a dual boot system with OS's on separate partitions. 
 
Must say, the 9.04 is impressive!

---

