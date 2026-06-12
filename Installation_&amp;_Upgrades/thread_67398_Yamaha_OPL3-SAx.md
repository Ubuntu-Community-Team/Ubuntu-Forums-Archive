---
title: "Yamaha OPL3-SAx"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by mimmori on 2005-09-20
I've installed linux on my Clevo 980 (AMD K6-2 300MHz).
All is ok but I don't know how install the audio driver, the board is the "Yamaha OPL3-SAx". This is the first time that I use Linux and i want to learn to work with it.
Could someone teach me how the driver work and How i can install it?
Thanks
Mimmo :razz:  :razz:

---

### Post by MrCheese on 2005-09-20
[QUOTE=mimmori]I've installed linux on my Clevo 980 (AMD K6-2 300MHz).
All is ok but I don't know how install the audio driver, the board is the "Yamaha OPL3-SAx". This is the first time that I use Linux and i want to learn to work with it.
Could someone teach me how the driver work and How i can install it?
Thanks
Mimmo :razz:  :razz:[/QUOTE]

From memory of quite a few linux installs over the years the OPL SAx is a nightmare. I never succeeded in getting the card to work, either using the modules provided or building a custom kernel with the drivers rolled in. 

I eventually gave up & installed a cheap pci Soundblaster 16 card. If Ubuntu didn't pick up the card on installation chances are that it won't work as modern hardware detection is pretty good. You may as well phone the computer store now......

---

### Post by az on 2005-09-20
Try this:

[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)


That sound card is on the isa bus and the 2.6 kernels can not safely probe them.  You need to tryto load the module yourself and then add it (the module name) to /etc/modules so that it gets loaded every time you boot.

Try these modules (offhand, I could not tell you which ones are included in the stock ubuntu kernel, but I think there are at least two):


snd-opl3sa2= Yamaha OPL3SA2

opl3= Yamaha OPL2/OPL3/OPL4 FM Synthesizer (on card chip)

opl3sa= Yamaha OPL3-SA FM Synthesizer (on card chip)

opl3sa2= Yamaha OPL3-SA2/SA3 FM Synthesizer (on card chip



Let me know if you get it working.  It should not be *that* hard.

---

