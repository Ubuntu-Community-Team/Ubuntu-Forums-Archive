---
title: "Toshiba Sat Pro A10 - Black screen on boot"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Oscar193 on 2010-07-18
Hi, I am trying to install Ubuntu 10 (latest) on my Toshiba Satellite Pro A10 laptop. Unfortunately when I boot, all I get is a black screen. I can boot from the disc, it'll show the loading screen then just show a black screen after that. I've tried using the "nomodeset" option but that doesn't seem to have any effect. Is there any other options I can try? Thanks in advance.

P.S The GFX device I have is "Intel 852GM Integrated graphics controller; 32MB internal shared video memory"

---

### Post by davidmohammed on 2010-07-18
its probably a graphics issue - depending on what the graphics card - can I suggest you try pressing F6 from the live CD. At the bottom of the screen is your boot string - add one of the following immediately before "quiet splash --"

i915.modeset=1
i915.modeset=0

then select the option "try without installing".

---

