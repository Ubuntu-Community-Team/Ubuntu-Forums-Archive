---
title: "Nvidia 195 drivers and overclocking"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Unitas on 2010-01-06
Hello, I just recently upgraded to the 195 drivers (from 190) from the nvidia PPA. Tried restarting gdm and they didn't load. Long story short all I had to do was reboot and everything was fine.

EXCEPT 

After enabling coolbits to be able to underclock my card, any settings I made to the 3D clocks refused to stick. I would move the sliders to where I wanted them, but once I hit "apply" they would zip right back to stock speeds. I tried nvclock as well, same results. I tried running nvidia-settings as root, same thing.

Only solution was to downgrade back to 190. Once I did so I was able to get the clock speeds set, as I had done before.

xorg.conf is the same, no changes.

---

