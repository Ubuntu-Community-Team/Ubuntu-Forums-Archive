---
title: "Kernel panic when booting from 12.04 Live CD"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by keiichi_morisato on 2012-06-29
Hi,

When I boot my Dell desktop system with a 12.04 LiveCD I get this error after seeing the initial boot screen.  It never gets to the "Install or run from CD choice":

*hctosys.**c: **unable to open rtc device (**rtc0)*
kernel panic not syncing vfs unable to mount root fs on unknown-block(1,0)

I have searched, especially about the kernel panic error but all of what I can find refers to booting from a hard disk when GRUB is misconfigured.

Where does the LiveCD try to put "/"?  How should I interpret this error?  

I have downloaded the ISO twice and made different LiveCDs to sure I didn't mess up burning it.  I also made a bootable USB drive and it causes the same error as the LiveCD.

Many thanks,
Keiichi

---

