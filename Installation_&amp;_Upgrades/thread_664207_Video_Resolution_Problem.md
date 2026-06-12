---
title: "Video Resolution Problem"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by webguy on 2008-01-10
Hey,

I have a HP Pavilion A230N, which has AMD Athlon XP processor, 512, 120 gig hd, integrated Nvidia. When I run LiveCD it boots to the desktop, but I don't have any status bar at bottom showing. I need to know how to change resolutiion so every thing is correct.

Thanks

Webguy

---

### Post by dburnett77 on 2008-01-11
On the top menu, it's:

"system...preferences...Screen Resolution..."

If that doesn't work, you'll have to monkey around with xorg.conf, and I recommend that you do a little research first, and always make a back up copy of xorg.conf when tweaking.

Be warned, in xorg.conf, there are definitely ways to destroy equipment.  So, learn before you mess with it.

---

### Post by Amstell on 2008-01-11
def hit up the screen resolution option.  If you installed the nvidia drivers do

sudo nvidia-settings

and adjust it from there.  Good luck

---

