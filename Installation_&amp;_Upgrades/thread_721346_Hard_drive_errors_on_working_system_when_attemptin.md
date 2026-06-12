---
title: "Hard drive errors on working system when attempting reinstall"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by rillip on 2008-03-11
I recently upgraded my computer, which had a working 6.06 install.  As part of the upgrade, I put in a new hard drive.  I can boot the LiveCD, but no drive is detected.  When I say not detected, it doesn't show in gparted, and fdisk -l does not list it either. The one that should be is a 500 gig sata.  I know the drive works because I installed Windows on it first, readying the system for a dual boot (it's now formated as NTFS, but because it's Win 2000, it only detected 137 gigs. I planned to partition the rest out to Linux anyway so I didn't worry about it.

I read that sometimes pci=nomsi can force the system to recognize it, but I get errors saying that it's an invalid option when I try it.  I also read that others couldn't get the option to work with 6.06 so I burnt a 7.10 LiveCD.  

The 7.10 LiveCD boots past the spalsh screen, then gives me a pinkish background and mouse pointer (which works).  It then stops spinning and nothing happens for a long time, ten minutes or more.  Every now and then I'll hear the CD spin up, but still nothing happens after a few hours.

So on a whim I decided to try to restart the xserver with ctrl+alt+backspace.  It dropped me into console view between stopping and starting, and I saw tons of errors about hdb having logical errors. I hit ctl+alt+f1 to try to get to console, and it let me, but then it starts spewing errors and does not accept my input.  I can type, but it doesn't do anything, and error messages will split my lines.

The same thing happens on every terminal. What confuses me is that there is no hdb! There's one CD, one PATA (hda) and two SATA (sda and the one that I haven't been able to find yet)!

Any ideas on how to fix this or where to go from here? I was able to fix my 6.06 install by copying some stuff out of the LiveCD xorg.conf, and it's working fine, but I'd like to get down to one drive, and need to copy the data off the others once I get the install on the new drive.

---

### Post by rillip on 2008-03-18
For anyone who's run into this as well, I pulled my head out of my rear orrifice and decided to run a CD integrity check.  Immediately found errors.  FYI, I booted the GParted LiveCD and it found the drive and partitioned it without issue, so I'm pretty sure 7.10 will as well.

---

