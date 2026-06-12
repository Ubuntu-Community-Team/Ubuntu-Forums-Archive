---
title: "XBMC media center on Ubuntu 9.10 beta"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DEagleson on 2009-10-11
Im trying to set up a working Ubuntu 9.10 beta install with XBMC and vdpau to work on a ASRock Ion 330.

ASRock Ion 330 Specs:
OS: Ubuntu 9.10 x86 beta
Intel Atom 330 Dual Core with Hyperthreading @ 2,1 GHz
Nvidia Geforce 9400m (aka Ion GPU)
4096mb ram (3gb used by OS, 512mb reserved for GPU)
500gb 5400rpm HDD

Im finished with the OS install, updating and installing the GPU driver.
As of now everything works great exept audio over hdmi.
(As im going to use my LG HDTV with it i really want to have audio trough hdmi.)

Lots of thanks and gratitude in advance. :)

---

### Post by whoelse on 2009-10-13
Have you activated HDMI audio in BIOS?
Check page 32 in the manual...

Please tell me if it works and if you are happy with your ASRock, as I am also thinking about getting one.

---

### Post by wild_oscar on 2009-10-24
> **DEagleson said:**
> Im trying to set up a working Ubuntu 9.10 beta install with XBMC and vdpau to work on a ASRock Ion 330.

ASRock Ion 330 Specs:
OS: Ubuntu 9.10 x86 beta
Intel Atom 330 Dual Core with Hyperthreading @ 2,1 GHz
Nvidia Geforce 9400m (aka Ion GPU)
4096mb ram (3gb used by OS, 512mb reserved for GPU)
500gb 5400rpm HDD

Im finished with the OS install, updating and installing the GPU driver.
As of now everything works great exept audio over hdmi.
(As im going to use my LG HDTV with it i really want to have audio trough hdmi.)

Lots of thanks and gratitude in advance. :)

Have you tried this: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/385076](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/385076)
?

---

