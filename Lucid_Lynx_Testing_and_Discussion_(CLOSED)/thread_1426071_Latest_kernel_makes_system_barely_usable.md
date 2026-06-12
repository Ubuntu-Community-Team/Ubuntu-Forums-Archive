---
title: "Latest kernel makes system barely usable"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2010-03-09
Made a bug report reguarding this, please check and see if it affects you aswell.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535444](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535444)

thanks

---

### Post by QwUo173Hy on 2010-03-09
It's running fine for me on Intel Graphics.

---

### Post by sports fan Matt on 2010-03-09
Intel here as well, no issues.

---

### Post by DoeRayMe on 2010-03-09
Hmmm maybe an ati related problem then, wait to see if we get any nvidia users respond :P

thanks for letting me know guys :)

---

### Post by jensbjorgensen on 2010-03-09
Here's one thing you could check:

glxinfo | grep 'direct rendering'

If you're getting software rendering, despite have an ATI card that can accelerate compositing, this could be a reason why. If you get:

direct rendering: No

then the slow sleep is probably due to something in the chain of the hardware acceleration not happening.

---

### Post by euphro on 2010-03-10
Getting the same problems (system freezing every ten seconds and compiz not working) with Radeon HD 3450 on an Intel P4 2.8 GHz system with 2 GB RAM, but only on kernel 2.6.32-16.25. When I revert to 2.6.32-15.22, the problems go away.

---

### Post by philinux on 2010-03-10
Fine here. Using nvidia nouveau.

Boot 23 seconds, very snappy in use.

---

### Post by SevenMachines on 2010-03-10
I'm on 2.6.32-16 with nvidia binary, being dumped into software gl at the moment. theres a change to a new drm stack and nouveau setup going on so this might be something to do with it. it'll certainly slow down compiz if gl's missing for you

X log:
(EE) Mar 10 10:09:14 NVIDIA(0): Failed to initialize the GLX module;

---

### Post by sgage on 2010-03-10
No problem here (using nvidia drivers)

---

### Post by tcchris on 2010-03-10
Not experiencing this .
I have a hd4200 igp

---

### Post by joffe on 2010-03-10
I'm also using the latest kernel and together with the xorg-edgers repo I finally have kms + HDMI sound with my Radeon HD 3300!!! No problems at all.

---

### Post by Uncle Spellbinder on 2010-03-10
The latest update cleared thing up for me as well. Finally able to use the system without issue. Was hoping for a few fixes (the white frame around the desktop, logging in twice and Plymouth), but Rome wasn't built in a day.

---

### Post by ranch hand on 2010-03-10
My ATI card seems to love it (card in sig).

---

