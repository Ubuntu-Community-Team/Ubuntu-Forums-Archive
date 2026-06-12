---
title: "Boot CD halts after decompressing Kernel"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by gdi2k on 2005-02-15
I'm having trouble getting the installer to start. Here's what happens:

1. The PC boots, detects a bootable CD-ROM, correctly displays the Ubuntu splash screen. I can navigate all the help areas (F1 - F8 I think).

2. I hit enter to use default settings. 

3. It says something along the lines of "Decompressing something-or-other......".

4. Beneath that it displays "Ready." and halts. Have to do a hard reset to get out.

I've been through all the various boot options, disabling hardware detection, noapic, nolapic etc. I've also tried expert mode, and activating debug stuff and so on, but nothing seems to make a difference.

The CD is fine, I can get the installer running with no problem on an Acer Laptop I have close by.

I've never had any trouble with bootable CDs before on this machine either - had various installers from other flavors of Linux (RedHat, Debian, Gentoo) run without a hitch. Knoppix LiveCDs run fine too, as does Windows 2000's installer. 

It's an MSI board (K7N420 Pro) running a K7, 768 MB RAM.

Any ideas?

GDI

---

### Post by gdi2k on 2005-02-15
Hmm, it seems if I change some BIOS settings around (not sure which ones now), rather than halting after "Ready.", the screen goes blank, with just a blinking cursor in the top left corner of the screen.

It still halts, but in a slightly different way.

Any pointers would be greatly appreciated!

GDI

---

### Post by gdi2k on 2005-03-02
**SOLVED:**
In case someone stumbles upon this mono-voiced thread with a similar problem, here's what I found out:

The issue is with the graphics card (in my case a dualheaded Matrox Millenium G400 or 450) being used in combination with a kernel which has been compiled with RAM Disk support (Graphics > Block Devices) enabled. Ubuntu's LiveCD, along with most other LiveCDs is compiled with RAM Disk support.

If you're trying to get a distro installed, switch graphics cards, install your distro, recompile your kernel with RAM Disk disabled and switch your graphics card back. Or maybe installing the latest Card BIOS (must be done under Windows) fixes it, I don't know.

---

