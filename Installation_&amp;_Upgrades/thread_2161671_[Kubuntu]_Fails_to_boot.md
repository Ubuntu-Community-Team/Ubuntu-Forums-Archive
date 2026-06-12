---
title: "[Kubuntu] Fails to boot?"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by zenbachry on 2013-07-11
I'm not exactly sure what to search for for this kind of problem, nor do I really know if the title is quite appropriate.

Allow me to explain the problem.

Live DVD of Kubuntu 13.04 boots, no problems, everything works fine.

A little troublesome connecting to network, but successful.

Setup and install, no problem.

Once I reboot, eject DVD to try to load into the fresh install.

Text goes across the screen as modules load, etc, etc...

Black screen, screen flashes, black screen.

20 minutes later, still black screen. HDD activity light flashes once in a while, but nothing.


Laptop is an Acer Aspire V3-551G

AMD A8 APU Quad core @ 1.9 GHz
4 GB DDR3 RAM
AMD Radeon HD 7640G + 7670M with 1 GB dedicated vRAM

Had Windows 8 when I got it, configured BIOS to legacy BIOS, replaced with Windows 7 for a while, then tried for Kubuntu, then Fedora. Using Fedora now, but would rather have Kubuntu (as I know it better)

Yesterday I couldn't get anything to load after install other than Windows until I updated my BIOS. Now it's just Fedora and Windows that'll load.

---

### Post by papibe on 2013-07-11
Hi  zenbachry.

I may be a graphic card compatibility problem. I would try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by zenbachry on 2013-07-11
I will try that now, and let you know.

Thank you.

---

### Post by zenbachry on 2013-07-12
It worked. Thanks a million!

---

