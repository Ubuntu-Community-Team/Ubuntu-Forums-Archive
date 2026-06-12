---
title: "Poor Video Performance!"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by higashi on 2010-01-17
Ever since my upgrade to karmic, I've been having video performance issues. I've posted about this several times already, searched for days, and still no luck.

If i try to play a video with Totem, it usually doesn't play. If i press play, it immediately turns back into a pause button. If it does manage to play, it lags..  A LOT.

If i try to play a video with Miro, it lags like crazy, and the sound doesn't play on time. (same goes for MPlayer)

I don't have any proprietary drivers. What can i do!?

---

### Post by fancypiper on 2010-01-17
What video card/chipset do you have? You probably need to install the drivers for it.

Have you tried to play them with VLC?

---

### Post by higashi on 2010-01-17
hm..VLC works quite well (but i still dont want to have to use it for everything)

Video Card:
> 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by fancypiper on 2010-01-17
Try installing the driver for your chipset.

sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

---

### Post by higashi on 2010-01-17
When i do that, it tells me that xserver-xorg-video-intel is already the newest version

EDIT: i noticed that the example video that came with karmic (which is of .ogv format) works perfectly fine

---

### Post by gradinaruvasile on 2010-01-17
Press alt+f2, type gstreamer-properties, press enter. Go to the video tab, select X11 with xv device, Intel texture output.

Install the Medibuntu repositories:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Update your system and install the w32codecs package.

---

### Post by higashi on 2010-01-17
I installed the medibuntu repositories, and got w32codecs. I then selected X Window System (X11/XShm/Xv), but it won't let me choose a device

EDIT: in the Device dropdown menu, it says "unsupported"

---

### Post by higashi on 2010-01-19
bump

---

