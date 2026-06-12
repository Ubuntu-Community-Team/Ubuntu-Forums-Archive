---
title: "How to install 9.10 server 64bit edition?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by poonaka on 2009-11-25
I've tried many times now to get the server edition to install on my box.  Most attempts the installer refuses to install grub.  Sometimes I can get it to install but then the system won't boot up because it's waiting for devices.

I have an ASUS P5K Deluxe wifi motherboard with 5 sata drives.  I want to install the OS on drive 1 and then use the other 4 for raid 10.  I've tried using IDE, RAID and AHCI modes.  IDE and RAID mode won't let me get past the grub install.  AHCI won't let me boot after the install.  Each install the installer tells me it has detect and active sata raid device(s).  Choosing yes or no does not fix the problem.

I can however install the desktop edition (64bit) via live cd install.  It detects all the drives and boots fine in AHCI mode.  I haven't tested the others.

This box used to have Win7 (64bit) and Win2008r2 (64bit) installed on it with the same configuration in RAID mode with no problems and no extra drivers needed during install.

Please help me figure this out as I've wasted 2 days on this already.

---

### Post by poonaka on 2009-11-25
no one has had this problem?

---

### Post by poonaka on 2009-11-26
Went back to Win2008r2 since it works.  Maybe I'll try again in a couple of releases once ubuntu server edition supports my hardware.

---

