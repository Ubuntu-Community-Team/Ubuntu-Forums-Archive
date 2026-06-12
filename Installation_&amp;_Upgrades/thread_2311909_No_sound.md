---
title: "No sound"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by chilliepot on 2016-01-31
Bought a laptop Lenovo T43, not new, sound works fine.
Wiped off XP and installed Ubuntu 15.10
No sound. 

I've tried the fixes as in many previous posts. Removing and reinstalling Alsa and Pulse.
Is there something I'm missing?


Other thing is
Also I have no $ alsamixer
as such

I have to type $ gnome-alsamixer

First time I have experienced that.

---

### Post by oldos2er on 2016-01-31
What audio device? ```
lspci | grep Audio
```

---

### Post by chilliepot on 2016-02-01
This is what I get: 

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

---

### Post by oldos2er on 2016-02-01
alsamixer is part of the alsa-utils package; if you need it run ```
sudo apt-get update && sudo apt-get install alsa-utils
``` But I don't understand why you can't use pulseaudio's sound settings to see what's going on?

---

