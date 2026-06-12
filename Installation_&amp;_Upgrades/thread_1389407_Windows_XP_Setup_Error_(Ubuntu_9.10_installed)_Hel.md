---
title: "Windows XP Setup Error (Ubuntu 9.10 installed) Help!"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by brokenrhythms on 2010-01-24
Hi Everybody-

I am currently trying to install windows xp after i have Ubuntu 9.10 already installed. I left 60 gigs of unpartitioned space for Windows Xp dual booting.

I just rebooted my system w/ the Windows XP Home Edition CD. It loads up for a little bit and then i get the following error:

"A problem has been detected and windows has been shut down to prevent damage to your computer. 

If this is your first time you've seen this error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on the computer.....etc.... etc...."

Any thoughts on how to fix this?

---

### Post by Mark Phelps on 2010-01-25
Well, this really is NOT a Windows XP forum (as the name Ubuntu Forums implies ...) but my guess would be that your machine has a SATA controller for the hard drive and your XP CD is not able to write to SATA drives.  If that's true, you would need to hunt down SATA drivers for your controller, put them on a CD (or diskette), and use F6 to load them during installation.

---

### Post by recluce on 2010-01-25
> **Mark Phelps said:**
> Well, this really is NOT a Windows XP forum (as the name Ubuntu Forums implies ...) but my guess would be that your machine has a SATA controller for the hard drive and your XP CD is not able to write to SATA drives.  If that's true, you would need to hunt down SATA drivers for your controller, put them on a CD (or diskette), and use F6 to load them during installation.

SATA drives in native mode (AHCI) are the most likely reason for a bluescreen during a Windows XP install. In addition to the suggestions above, you could either set your BIOS to "IDE emulation" instead of AHCI mode - which comes with a slight performance loss. Or google for "nLite", which is a tool that allows (among many other things) to slipstream SATA drivers into a XP installation CD, which would neatly avoid that problem. Unfortunately, to use nLite you need a working Windows installation, which might be a catch 22 for you.

---

