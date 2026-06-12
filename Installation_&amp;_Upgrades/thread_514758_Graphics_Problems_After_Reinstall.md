---
title: "Graphics Problems After Reinstall"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by Josh_b on 2007-08-01
Hey

I just reformatted my PC (all hdd's. So it was a clean slate). I installed Windows, everything went fine. I installed Ubuntu (the same version I had on before the reformat (6.06 alternate i386), the install went perfectly (although, I lost 3gb worth of space trying to put in a swap space, but that doesn't matter). Anywho, I went to boot it up. Everything goes fine, until it comes to the logon screen, and everything is messed up. I can't see what I'm doing, however I can log in. I can also boot into recovery mode, via GRUB. I'm kinda newish to linux.

Any help would be great.

Josh

---

### Post by mathewb on 2007-08-01
this is probably a problem with the graphics card driver. if you install the proprietary driver for your graphics cards, it may solve the problem. Since i think you have a card with an nvidia chipset (i'm not familiar with the LeadTek 7900GT), installing the "nvidia-glx" package will install the proprietary driver and may solve the problem.

---

