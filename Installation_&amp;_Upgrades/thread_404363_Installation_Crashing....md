---
title: "Installation Crashing..."
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by rboutros on 2007-04-08
Hi, 

I am very new to the Linux world and this is my first try at it. I cannot seem to install Linux on my HP. A819n. It seems to freeze during the initial stages of installation everytime. I have tried Ubuntu 6.06 & 6.1, both have the same problem. 


Does anyone have any ideas?

---

### Post by Jussi Kukkonen on 2007-04-08
Can you please post as much details as you can? E.g. the exact point of failure and any possible error messages. You might want to use the screenshots ([http://shots.osdir.com/slideshows/slideshow.php?release=751&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=751&slide=1)) to illustrate... Also, have you tried booting the live CD?

By the way, the version number is 6.10 (it's not a decimal).

---

### Post by rboutros on 2007-04-08
Not sure how to capture a screen shot from a frozen system, so I will just type it out. 

This is what happens when I try to install 6.0.6 boot disk:

I get to the initall screen, then I hit enter to begin the install. After about 15-20 seconds I get a bunch of code on my screen and it eventually stops at this at this line:

[17179658.372000]  <0>Kernel panic - not syncing: Fatal exception in interupt



Does this help at all?

---

### Post by Jussi Kukkonen on 2007-04-08
Yes it does. It seems some part of your system is not 100% compatible. Usually it's the motherboard, and usually it's not fatal: we can just tell the bootloader to not use that functionality. To decide correct boot options, we'll need more info, though...

If you have a digital camera, take a photo of the kernel panic and attach it here. If not, please write the function names below the "Call Trace" row -- the numeric codes aren't important, just the function names (e.g. "pci_bios_write" and the like)

---

