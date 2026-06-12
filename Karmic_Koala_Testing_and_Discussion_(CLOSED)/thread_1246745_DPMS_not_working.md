---
title: "DPMS not working"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-08-22
hi, dpms not working on my pc. with jaunty, dpms works well. i think that problem depends on gnome-power-manager and switch from hal to devicekit. 

i'm using nvidia 9600 gt and the Xorg log shows that the DPMS module was loaded succesfully.

doing "xset dpms force off", dpms works fine, so the display is capable of going to sleep.

When I close the laptop lid, the external screen shuts down correctly as well.

The screen never goes to sleep, only blank. And if the screensaver activated, then, after a set period of time the screen saver activated, after a few more minutes the screen goes blank (but not turns off), and after a few more minutes screen saver reappears and stays on.

---

### Post by wnelson on 2009-08-22
kill the gnome-power-manager and then restart it. I have found this to work. The startup order of the screen saver then power manager I think is the problem?

---

### Post by biasquez on 2009-08-22
for me, this fix doesn't work...

---

