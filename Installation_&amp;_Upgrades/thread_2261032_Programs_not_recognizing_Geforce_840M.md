---
title: "Programs not recognizing Geforce 840M"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by jrdobelmann on 2015-01-15
I recently went through the process of installing the drivers for my Nvidia 840M.  I was able to install the open source drivers, as well as nvidia-prime and nvidia-settings, but my programs don't recognize my card.  Is there something I still need to set up?

---

### Post by efflandt on 2015-01-16
I have not installed 14.04 on my laptop yet (I want to put it on mSATA and currently have 13.10 on its hard drive which was just beginning to support hybrid Intel/Nvidia video).

You should have already had drivers by default for the integrated Intel video and if you installed an nvidia driver package it should have automatically installed nvidia-prime and nvidia-settings. Then it is my understanding that you should have something in NVIDIA X Server Settings to enable your nvidia video. Which Ubuntu version are you running and which nvidia package did you install? I imagine **nvidia-331-updates** would be best, unless you installed a newer version from xorg-edgers ppa. I just would NOT recommend nvidia-346 from the ppa right now because it has some non-fatal module compile error when doing kernel updates.

---

### Post by tokyobadger on 2015-01-17
> **jrdobelmann]I was able to install the open source drivers, as well as nvidia-prime and nvidia-settings[/QUOTE]
Please clarify - when you say open source drivers do you mean nouveau? If that is the case and you somehow managed to install nvidia-prime and nvidia-settings without the main driver package then your set-up will not work.

As efflandt said, you should be go only with the full nvidia package and by installing the standard nvidia-331 you should get all the required components.


Offtopic:
[QUOTE=efflandt said:**
> I just would NOT recommend nvidia-346 from the ppa right now because it has some non-fatal module compile error when doing kernel updates.
[newer version 346.35 landed 2015/1/17](http://www.ubuntuupdates.org/package/xorg-edgers/utopic/main/base/nvidia-graphics-drivers-346) and seems to address the issues above plus includes patches for 3.18.x kernel. Available for 12.04, 14.04, 14.10, and 15.04

---

### Post by jrdobelmann on 2015-01-19
Apparently my drivers were working the whole time.  I was confused because Blender wouldn't recognize the graphics card, but now I know that's because I hadn't installed CUDA support yet.  Thanks for your help, regardless.

---

