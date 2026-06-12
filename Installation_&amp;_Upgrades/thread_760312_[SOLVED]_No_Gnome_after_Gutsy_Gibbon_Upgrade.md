---
title: "[SOLVED] No Gnome after Gutsy Gibbon Upgrade"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by lynwode on 2008-04-20
I have just performed a Gutsy Gibbon upgrade and things didn't go well.... :(

First up I get  kernel panic which I have got around by choosing a different kernel in grub, not a perfect solution but at least I'm in. Now when I start gnome via gdm or startx i get a grey screen with a pointer and thats it. I'm guessing some config file may have been overwritten by the upgrade. 

Anyone got any ideas on a) how to go back to Feisty Fawn b) get my gnome back.

Cheers.

---

### Post by Partyboi2 on 2008-04-20
when you get to the grey screen press Ctrl+Alt+F2 to get to a terminal then
```
sudo dpkg-reconfigure xserver-xorg
``` and work your way through the questions.

---

### Post by lynwode on 2008-04-20
Thanks Partyboi2,

Your suggestion pointed me in the right direction. I tried what you suggested but this failed. Something along the lines of dpkg was half way through something as needed to complete.
I did as the prompt suggested and all is working now.

---

