---
title: "HDMI audio on ATI Radeon HD 4670"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by Ultor on 2010-09-12
Hi,

I just installed 10.04 for dual boot on my Windows machine with almost no problems.

My only problem is that I can't get the HDMI audio to work with my ATI Radeon HD 4670.
I found this [guide]("https://help.ubuntu.com/community/RadeonHD") which suggests adding lines to the xorg.conf to enable HDMI audio. As I found out apparently there is no xorg.conf in /etc/X11, so I tried to create one by pressing CRTL-ALT-F1 and then

```
sudo service gdm stop
sudo Xorg -configure
```but all I get at this step is that my system freezes at a black screen with just a white bar in the top left corner and no xorg.conf is created.

Any help would be appreciated.

Thanks,
Ultor

---

### Post by Ultor on 2010-09-13
bump

---

