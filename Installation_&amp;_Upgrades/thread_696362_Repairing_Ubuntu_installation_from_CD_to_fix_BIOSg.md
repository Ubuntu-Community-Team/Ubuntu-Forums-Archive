---
title: "Repairing Ubuntu installation from CD to fix BIOS/graphics issue?"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by wordchisler on 2008-02-13
I have a laptop that from time to time, particularly it seems after any graphics intensive programs, goes haywire: freezes, then after a forced reboot, presents a boot screen with corrupted graphics and the following screens have corrupted letters: r replaces some of the S's, l for some of the Ms, and so forth. 

I fixed the problem, or so I thought, by installing Fiesty and then upgrading to Gutsy. No pixelated graphics, etc.

Today, I upgraded to KDE 4, but it ran poorly. This evening I ran Pingus for awhile. When I closed the program, I tried to log off, but the computer did not respond. Except that the mouse could be moved, the computer had hung. So I forced a reboot.The problem returned. Occasionally I get garbled UBUNTU screens, but then the login screen loads beautifully. I haven't successfully logged on yet to any of the users I created.

I didn't have much information on there, so I suppose I could reinstall UBUNTU, and just steer clear of games and graphics intensive applications (and kde sessions). Restoring the OS will clean up the graphics, but I am wondering if there might be a quicker solution? 

I have already tried the menu options at GRUB, repairing that way makes no difference.

---

### Post by Shazaam on 2008-02-14
How much memory is installed? Do you have graphics drivers installed?

Not help but a tip.......
Two things you can try when the laptop crashes.
1. Hit Control+Alt+F1 and type in either sudo reboot or sudo shutdown -h now.
2. If it is totally locked up and unresponsive hold down Alt+Sys Rq (PrintScreen) and slowly type in these letters= R E I S U B
Read this.....
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

