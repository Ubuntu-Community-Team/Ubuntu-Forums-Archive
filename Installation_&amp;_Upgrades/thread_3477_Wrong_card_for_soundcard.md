---
title: "Wrong card for soundcard"
date: 2004-11-06
forum: Installation &amp; Upgrades
---

### Post by Simon on 2004-11-06
In my computer I have two multimedia cards, one is my sound card (Cirrus Logic Chipset) and the other is a TV tuner (Brooktree Bt878 chip). When I install a preview release of Ubuntu everything is fine, but when I upgrade to the final release my TV card is swapped as my main soundcard. That means when I use 'alsamixer' it gives the levels of the TV card, and all output is sent to that card, so I have no sound anymore. The other card is detected as it shows up in the gnome-volume-control, so how do I configure alsa (or what ever else) so that it uses the proper card?

Thanks,
Simon

---

### Post by im_ka on 2004-11-06
try "gnome-alsamixer" (you need to install it from universe). you can switch between the two cards with that.

hth

---

