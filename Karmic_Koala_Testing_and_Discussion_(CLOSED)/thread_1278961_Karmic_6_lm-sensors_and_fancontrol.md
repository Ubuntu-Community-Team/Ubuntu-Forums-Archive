---
title: "Karmic 6 lm-sensors and fancontrol"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whitethorn on 2009-09-30
I have a Asus P5Q pro motherboard.  After upgrading to karmic I can't seem to get fancontrol to work.  Oddly enough sensors detects everything, I added the appropriate modules to /etc/modules.  When I run pwmconfig it tells me there are no pwm controllable devices (which is wierd considering it worked before the upgrade).  I haven't tried using the actual version from the webpage because the webpage is down.  I'll try again when the lm-sensors homepage is back online and post my results.

---

### Post by dino99 on 2009-09-30
mine is a p5w & i've filled a bug about missing driver for my chipset. Have you any warnings in logs ?

General comment: as karmic is still alpha, we have to wait beta to see those settings happen.

---

### Post by MacUntu on 2009-09-30
See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246)

---

