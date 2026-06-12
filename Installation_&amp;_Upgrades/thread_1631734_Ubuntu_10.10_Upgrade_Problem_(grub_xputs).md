---
title: "Ubuntu 10.10 Upgrade Problem (grub_xputs)"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by jay3 on 2010-11-27
Have just run the upgrade from version 10.04 to 10.10. The process all ran ok and then at the end when trying to restart I receive the error "The symbol Grub_xputs Not Found". And, I am given a "grub rescue >" command prompt. What happened? Anyone know what I need to do now? Thank you.

---

### Post by tommcd on 2010-11-27
> **jay3 said:**
>  I am given a "grub rescue >" command prompt. ... Anyone know what I need to do now?
See this tutorial on grub2 for info on how to boot from the grub rescue > prompt:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)
If it were me, I would just cut my losses and do a clean install from the Ubuntu 10.10 install CD. I always do clean installs instead of upgrades, and I never have these problems.
However, many people seem to fear doing a clean install of Ubuntu for some reason. So see if you can follow that tutorial and boot from the rescue prompt.

---

### Post by jay3 on 2010-11-27
I guess i didn't want to go the route of a full/new install of ubuntu 10.10 because I wanted to maintain all my setup (such as my email) and didn't want to have to backup and reestablish all my files/data etc.

---

### Post by Rubi1200 on 2010-11-27
Hi,
the xputs error indicates that GRUB is likely missing some files.

I recommend you use the chroot method outlined in this guide by drs305 to purge and reinstall GRUB:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
(use the correct partition for your setup)

Note: if you are also booting other operating systems, then I suggest you run the boot info script linked at the bottom of my post BEFORE using the method above and post the results here so we can take a look.

If you have any questions, feel free to ask.

---

