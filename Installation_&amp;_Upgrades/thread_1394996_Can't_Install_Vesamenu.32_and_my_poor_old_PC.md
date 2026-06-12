---
title: "Can't Install: Vesamenu.32 and my poor old PC"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by ultrageeky on 2010-01-31
For the past 2 days I have tried to install Ubuntu i386 onto an old (2002) PC. The installation fails at every step due to vesamenu.c32 which attempts to run VESA code through the PC's BIOS which doesn't support it. The issue has nothing to do with the condition of CDROM or the iso image burned to it; I've checked with multiple flavours of Ubuntu and I have installed it into a virtual machine on another desktop so I know the disk is fine. 

A BIOS update could fix the issue except I can't flash the BIOS because it's on a PC Chips mobo that is no longer supported by PC Chips (the update file no longer exists).

For now I've installed an old version of Win XP (sorry for swearing).

I know it is possible to boot the installation CD through the Windows boot menu by adding an option to start the Ubuntu installation process without the need for an installation menu but I don't how to do it. Please can someone provide instructions or advise another means to start the installation that doesn't require fancy VESA graphics.

---

### Post by ultrageeky on 2010-07-27
Not a problem with 10.04 but for those who need to install an earlier version, type "live vga=ask" when it drops to a prompt and leave it running. The screen will remain blank for a few minutes but it will eventually load (listen for the disk being accessed).

---

