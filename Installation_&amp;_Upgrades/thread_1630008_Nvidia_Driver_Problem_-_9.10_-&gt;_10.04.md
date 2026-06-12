---
title: "Nvidia Driver Problem - 9.10 -&gt; 10.04"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by samnardoni on 2010-11-24
I have a nVidia Geforce 7800GT graphics card. Here's the output from lspci:
```
VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
```

I've been trying to install ubuntu 10.10 from CD, but no luck -- the screen is blank. I can get further by using the "nomodeset" param/flag, but that only gets me on to a terminal which I can't do much with.

I had a 9.10 disk lying around, so I installed that. I (naively) thought that upgrading through synaptic from 9.10 -> 10.04 would magically make it work, but it didn't. Same blank screen.

From what I can gather, it's due to ubuntu not supporting the nVidia drivers any more.

So, now I'm on a fresh install of 9.10. I want to get 10.x installed. Is there some way I can install the drivers while on 9.10, then upgrade to 10.04, and have the drivers still installed? (or will the upgrade overwrite the drivers in some way?)

Any info on this is much appreciated.

- Sam

---

