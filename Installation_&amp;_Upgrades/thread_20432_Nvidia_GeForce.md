---
title: "Nvidia GeForce"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by Cybermagellan on 2005-03-16
I know I keep bugging everyone on the forums with such simple issues however nothing is working.

I have a Verto GeForce FX 5500 Video Card, PCI, 128MB DDR made by PNY. Now the problem is that it is considered a Nvidia Chipset I believe. However when I load the Nvidia Drivers it doesn't recognize the card. That and xorg comes up and says it can't start  :-| . 

I'd like to use my card and skip using my intergrated card however PNY doesn't seem to have a website or anything for the drivers. How would I go about doing this?

Shawn

---

### Post by wylfing on 2005-03-16
Please explain the steps you take to "load the nvidia drivers." I assume Hoary because of the xorg comment. Did you install the drivers through Synaptic/apt-get, or did you download them from the nVidia site?

Also post the exact error messages you're getting from X.

---

### Post by Cybermagellan on 2005-03-16
Well I tried to download them from the nvidia website. I also found a site about nvidia-kernel-kernel source (Can't remember now sorry) and even though Synaptic says my computer is up to date It still isn't finding drivers for it... :-( Anything else you need to know? The exact error is a blue screen that says X cannot start because it cannot find a supported screen or something like that

---

### Post by wylfing on 2005-03-16
I would strongly suggest using the packages provided by the Hoary repository. Fire up Synaptic, hit Control-F, and search for "nv" (without the quotes). Find "nvidia-glx" or its equivalent and install it. 

After that, report back with any problems you're still experiencing.

Edit:

It is most helpful if you can post the exact error messages you see, rather than summarizing them.

---

