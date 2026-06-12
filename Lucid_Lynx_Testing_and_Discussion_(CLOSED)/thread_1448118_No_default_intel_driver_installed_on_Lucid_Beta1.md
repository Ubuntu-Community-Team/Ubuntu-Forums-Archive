---
title: "No default intel driver installed on Lucid Beta1"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by snurfle on 2010-04-06
Not sure if this warrants a bug report or not; just wanted to see if anyone could tell me if it's worth submitting one.

I upgraded from 9.10 last night to 10.4 Beta 1.
It went smoothly with one small exception:
My laptop (Inspiron B120) has a built-in intel GPU (i915), and I had been using the 'intel' driver in Karmic and Jaunty.
Lucid, according to the xorg.log, tried to load the 'i810' driver, failed to load it ('not found'), and defaulted to 'vesa'.
I found in synaptic that nearly every flavour of driver was loaded *except* the intel driver.
After removing the (literally) 15-20 other drivers and installing the "xserver-xorg-video-intel" driver all through synaptic, everything is running smoothly.

Should the gpu be detected during installation and the correct driver installed? Or was there a reason why it chose not to install it?

Thank you.

---

### Post by Mark Phelps on 2010-04-06
Please post your beta-related questions to the proper beta testing forum: Development & Programming, Lucid Lynx Testing.  thanks

---

### Post by snurfle on 2010-04-06
Posted there. Sorry about that; didn't realize it was there.

---

