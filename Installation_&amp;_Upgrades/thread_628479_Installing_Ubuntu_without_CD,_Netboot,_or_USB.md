---
title: "Installing Ubuntu without CD, Netboot, or USB"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by dirtroad on 2007-12-01
First off:  I'm not a linux noob, but not an expert either.  I've dabbled with it on and off for several years.  I've done a lot of forum and web searches about this only to end up at dead ends.  

What I'm trying to do:  Install Ubuntu on an older laptop without a working CD drive, without a floppy drive, without the capability of netbooting, and without the ability to boot from USB.  

What I can do:  I remove the laptop's hard drive, adapt it to another PC running WindowsXP or booting a Linux CD.  The hard drive is not currently empty, but has a mangled XP installation on it that won't even boot in safe mode.

So my question is:  Using a different PC, how can I make the laptop's hard drive bootable, make it contain all necessary ubuntu install files, and then put it back in the laptop to do the installation.  

Thaks for any info.

---

### Post by Pumalite on 2007-12-01
Install in whole hard drive in similar computer, then transfer the hard drive to the old computer. At boot you might have problems with the xserver, but it's easily fixable.

---

### Post by dirtroad on 2007-12-01
the PC's at my disposal are very dissimilar.  My prior experience with Linux has been that it chokes badly on major hardware changes.  Kernel panic anyone?  I guess it might be worth a try though...

---

### Post by Pumalite on 2007-12-01
The kernel is supposed to load the modules according to the hardware it faces. It's true; sometimes it doesn't work.

---

