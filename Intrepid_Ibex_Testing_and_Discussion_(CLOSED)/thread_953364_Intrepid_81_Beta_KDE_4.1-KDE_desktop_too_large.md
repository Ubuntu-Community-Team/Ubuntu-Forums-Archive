---
title: "Intrepid 8/1 Beta/ KDE 4.1-KDE desktop too large"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mibadt on 2008-10-20
Hi,
I tried to install the beta of the new Kubuntu Interpid (8.1) on a Fujitsu laptop (Amilo 2030) supporting (in MS/XP) a screen resolution of 1024x768 @ 60HZ.
The resulting KDE desktop (the main desktop) is too large (I can see only its left "half).

I've tried:
a. Editing xorg.conf, adding a Display SubSelection in the Screen with above parameters - didn't help and probably ignored by the xserver.
b. Running KRandRtray (screen resize application)-wouldn't run.

How can I solve this problem?

---

### Post by takowl on 2008-10-20
Can you see enough of it to bring up system settings, Display, and change your resolution there?

KRandrTray may be loading, but it appears in the system tray, which is by default in the bottom right, so doesn't really help you.

If the above doesn't work, let's try using xrandr. Bring up a terminal (Alt+F2, "konsole"), and enter "xrandr" to see what you've got.

---

### Post by mibadt on 2008-10-20
Thanks,
As you guesses, I can't see the lower right corner of the screen.
xrandr ran and showed my default resolution to be 1600X1200 (while the screen supports only 1024X768), yet, as it's a laptop, I don't have a separate numeric keypad so I don't know how to switch among screen result ions.

Please advise!

Thanks

Michael Badt

---

