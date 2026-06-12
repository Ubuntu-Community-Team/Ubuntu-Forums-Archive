---
title: "cant install and unknown devices"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by Pord on 2007-08-07
Hi there,

I recently upgraded my PC and I went to install ubuntu onto it as a dual boot. However when I came to it I came across it not picking up my Xeon processor correctly It said it was an unknown device. Also It wasnt picking up my hard disks.

Here is my set-up:
Quad Core Xeon 2.4GHz
Nvidia 7900 GS graphics card
4Gig of DD2 Ram
Abit IP35Pro motherboard
Maxtor SATA hard disks
Nebula Electronics DigiTV PCI tv card

Any1 got any ideas? Does ubuntu support the new motherboard I have with its new P35 chipset and the quad core processor?

Ive tried this with Ubuntu feisty 7.04 (32bit) and gutsy gibbon alpha7 (32bit) and neither pick it up.

---

### Post by dbd on 2007-08-07
Well, it isn't the Chipset. I have a GA-P35-DS3R, which also has the intel P35 chipset, and that detects my Quad Core Q6600 and my SATA drive fine. (My only problem is with the on board network :()
Edit: Now Fixed! I'm using Gutsy (which alone didn't fix it). Then discovered that windows is disabling it at shutdown, and only re-enabling it at windows boot, To fix this just Enable wake on lan in the device manager. (I know this is totally irrelevant to the thread, but anyone searching for this mobo which has these problems may want to see this)

Also, Abit are quite a big brand, so I'd expect there'd be loads of mentions about it if one of their mobo's didn't work properly.

A really crazy idea, but you tried using less RAM? I know that 32bit operating systems can only handle so much RAM (I *think* the max is 4Gb, so you should be OK, but I have heard from other people that it is 3Gb. Also, on a similar thread, you could give the 64bit live disk a spin.


Good luck! :)

---

### Post by Pord on 2007-08-07
well ive tried with 4gig in my old set-up and worked before

---

