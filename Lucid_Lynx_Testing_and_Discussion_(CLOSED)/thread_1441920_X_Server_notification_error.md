---
title: "X Server notification error"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nu2linux6 on 2010-03-29
I keep getting the following notification error every time the desktop first appears:

'Could not apply the stored configuration for monitors
X Server does not support size requested'

My resolution is 1152x864 and I'm using the Nvidia binary driver.

Any idea how I can get rid of it? It's very annoying! Thanks.

---

### Post by dino99 on 2010-03-29
> **nu2linux6 said:**
> I keep getting the following notification error every time the desktop first appears:

'Could not apply the stored configuration for monitors
X Server does not support size requested'

My resolution is 1152x864 and I'm using the Nvidia binary driver.

Any idea how I can get rid of it? It's very annoying! Thanks.

go to system -- pref --screen and make your choice
by the way Lucid dont need xorg.conf, so rename it like xorg.conf.orig (if you want it to not be lost) and reboot

other solution: Xorg -reconfigure

---

### Post by nu2linux6 on 2010-03-29
It seems that every time I change resolution and save to the configuration file in nvidia settings, I then have to set it in Monitor Preferences as well or I get the dreaded notification.

Is anyone else getting this problem? Is it a bug? It's all very confusing...:confused:

---

