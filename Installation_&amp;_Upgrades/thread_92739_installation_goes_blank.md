---
title: "installation goes blank"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by chevy on 2005-11-20
I'm trying to install breezy on my laptop as a dual boot with XP.  When I boot from the cd, the kubuntu install screen apeears, allows me to press enter to install, initializes the system, but goes no further.  I get a black screen instead of a language option screen.  I've tried the cd on another machine to be sure it wasn't the problem, passed.  Any ideas?

Chevy

---

### Post by pompeyjohn on 2005-11-20
um... it is hard to say without system specs, could you post them? and have you tried hitting F1 at the install prompt, there is information there that might be of help.

---

### Post by chevy on 2005-11-20
Dell 9300
-Pentium M 1.6
-512 RAM
-60 Gb hard drive
-NEC DVD-RW
-Intel Pro-Wireless
-Broadcom 10/100 Ethernet
-XP Pro

To further complicate things, I had Hoary installed on it previously on a three partition setup.  Well, I had some Windows problems and reinstalled that.  In doing so, I couldn't get back to my linux partition.  So, a friend and I got a wild hair and tried to do a grub-install by ourselves.  Here's where things get ugly.  Some where along the way we got to messing with the MBR and before you know it we're doing a FIXMBR.  So my theory is that messing with that has something to do with the problem.  Since then, I've wiped out all my partitions and just reinstalled Windows without any partitions.  I figured I'd just use the Kubuntu install to repartition the disk.  So now Window is working fine, but I just can't get the Kubuntu install process to get any further than the system initialization stuff.

---

### Post by chevy on 2005-11-21
If anyone else ever has this problem, my friend figured it out.  It was a resolution problem.  The installation discs could determine my resolution therfore giving me a black screen.  To solve this, at the boot propmt he type linux vga=791.  That seemed to work just fine.  I got the language option and everything worked good from then on out.

mike

---

