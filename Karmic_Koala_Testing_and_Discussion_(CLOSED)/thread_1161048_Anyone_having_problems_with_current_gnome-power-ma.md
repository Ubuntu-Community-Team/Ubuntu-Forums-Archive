---
title: "Anyone having problems with current gnome-power-manager?"
date: 2009-05-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-05-16
I've been having a problem with my screen returning from sleep starting with the last week's gnome-power-manager. Will have video corruption--tearing--wrong sizing that takes restarting in one of my other installs or doing a cold boot to clear up. Normal operation is fine----

Looks like a problem between power-manager & the nvidia driver...Thoughts anyone?


Bug report filed:  [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/377299](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/377299)

---

### Post by freeman2000 on 2009-05-17
Seems that some users are having this problem, but fortunately that's no longer the case for me.  It originally happened a few times a couple of days ago on my laptop, after approx 30-60 seconds the screen went black and I had to use the touchpad to bring it back, even though I had the Power Management set at 15 minutes.  Since the HAL & gnome-power-manager updates a few days ago the problem seems to have disappeared on my laptop.  It now sleeps/hibernates as programmed.  Good luck.

---

### Post by kingborel on 2009-05-22
I'm having issues with gone-power-manager, but slightly different ones. Every now and again it will get stuck in a loop between lowing the brightness and putting it back to 100%, maybe 2 or 3 times per second. This happens on AC and battery on my MSI Wind. killing and restarting gnome-power-manager fixes the problem. It also happens after a suspend or hibernate

---

