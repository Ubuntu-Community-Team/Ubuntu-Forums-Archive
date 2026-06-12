---
title: "Gurb2 and 1920x1080 resolution"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by mobal on 2012-01-15
Hello!

It is possible to set not framebuffer resolutions in grub menu? Both Intel and Nvidia graphics cards.

Thanks!

mobal,

---

### Post by dino99 on 2012-01-15
its not needed as gfxpayload is the default setting (see /etc/default/grub then run sudo update-grub)

---

### Post by mobal on 2012-01-15
GFXPAYLOAD is the default setting. I set the preferred resolution - 1920x1080 - int grub.cfg too, but still not working. I hate this, not supported FRAMEBUFFER resolution and no way to get my native res. *sigh*

Any one else?

---

### Post by fantab on 2012-01-15
In /etc/default/grub

Look for this line- "**GRUB_GFXMODE=1920x1080**" and change it accordingly. If there is "**#**" in front of the line, remove it. 

Then you have to ***sudo update-grub***

I too have a 1920x1080 screen and above setting works.

---

### Post by drs305 on 2012-01-15
Have you looked at what resolutions Grub supports? At the grub menu during boot, press 'c' to get to the grub prompt. Then run "vbeinfo" to see what resolutions are available to you. 1920x1080 may not be an option...

Note: As a mod I can also correct the typo in the thread title if you want.

---

