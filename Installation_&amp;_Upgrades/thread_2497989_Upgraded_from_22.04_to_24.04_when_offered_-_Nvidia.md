---
title: "Upgraded from 22.04 to 24.04 when offered - Nvidia drivers + USB hot plug not happy"
date: 2024-05-25
forum: Installation &amp; Upgrades
---

### Post by adfh on 2024-05-25
Hey folks,

Upgraded from 23.04 to 24.04 (Edit.. makes sense now.. i think I had 23 on this machine not previous LTS 22)

I have an NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1) video card with two displays connected, one in portrait.
... it seems to suggest nvidia-driver-390 or -470 (I've tried adding graphics-drivers PPA)

Initially on first boot, it would only show me an image on one display.
I tried a dance of uninstalling and reinstalling the nvidia components, and I got a mix of it working with Nouveau, but crashing with the nvidia driver.
At one point it mentioned something about secure boot whitelisting?
When I try to use nvidia drivers, it shows me an "Oops something went wrong" after logging into GDM.. then it'll boot me back out to GDM.

What am I missing? Should I just stick with nouveau for now?

Have also noticed that hotplugging USB storage devices seems to be broken.

---

