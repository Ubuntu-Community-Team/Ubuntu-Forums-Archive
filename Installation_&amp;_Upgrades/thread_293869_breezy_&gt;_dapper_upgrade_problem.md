---
title: "breezy &gt; dapper upgrade problem"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by toastedcheese on 2006-11-05
I'm experiencing an odd problem that I just wanted to get advice on before I do something extreme (like reformat and reinstall *everything*, as is tempting.)

Last week I (tardily) began a Dapper upgrade. I realized halfway through my upgrade that my /boot partition had run out of space, again. It seemed to be hindering the install, so I ended up rebooting and resizing it using a Live CD; this went fine, as far as I can tell.

The last time I upgraded Ubuntu, I also had problem with /boot being too small, and although I enlarged it, I also ended up with the most recent kernel going into kernel panic when I tried to use it. Instead of fixing that, I've just been using a slighly outdated kernel, and it's worked fine.

Now, after rebooting, I have a new kernel or two added to the startup list, which I'm assuming is the product of my half-baked upgrade. Two of the kernels go into kernel panic when I try to use them. The oldest one boots up okay, but when I get to the login screen, neither the mouse nor the keyboard work (despite the fact that the keyboard works when I'm choosing which kernel to use.)

In contrast, I dual-boot Windows, and when I tried using that instead, initially the mouse worked but the keyboard didn't. I recently bought an external USB hub, and on a whim I switched the keyboard, which was plugged into the hub, with the mouse, which wasn't. This made both the keyboard and the mouse work, but both continue not to function in Ubuntu.

Lastly, when I'm booting up the Ubuntu kernel that works, it fails its attempt to start PCMIA; not sure if that's related.

I thought this might be a hardware problem - before now, occasionally when I started my computer, my keyboard wouldn't work when it reached the Linux/Windows selection menu - but my brother thought it might be a mysterious kernel problem. Either way, I wanted to know if there's anything I should do before I give up and do a clean install.

---

