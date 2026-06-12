---
title: "Xubuntu install problems and fixes"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by Jemod on 2006-06-12
I recently installed Xubuntu on a low-end machine and ran into a few problems.  I just wanted to post my solutions for other people who may run into the same thing.

The target machine was a Dell Dimension XPS Pro 200n - Pentium Pro/64 meg.  The Xubuntu doc said not to use the LiveCD install with a low-end machine and use the "alternate" cd instead.  The machine would boot with the alternate cd and the install would begin, but it would die with the error message "**Kernel panic - not syncing: Fatal exception in interrupt**".  After I ripped all the hardware out of the machine and after many attempted installs I discovered that the CD-ROM was too slow - it was a 12x.  I happened to have a 36x CD-ROM, which I installed, and the install ran perfectly.

After I had Xubuntu installed, I wasn't able to set the display resolution to anything larger than 800x600.  The video card was an S3Virge with an older Dell (Sony) Trinitron monitor. I had to manually edit the *xorg.conf* and set the DefaultDepth to 16, from 24.  This allowed me to get higher resolutions.  [I found this URL helpful.]("https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29")

---

