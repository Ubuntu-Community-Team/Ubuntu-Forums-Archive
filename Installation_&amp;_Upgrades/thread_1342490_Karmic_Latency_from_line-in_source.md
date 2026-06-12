---
title: "Karmic: Latency from line-in source"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by riverfr0zen on 2009-11-30
After upgrading to Karmic, I first found that I could not get any sound from my PS3, which is connected via a line-in socket to my soundcard. After some digging, I was able to get sound by adding the following line to /etc/pulse/default.pa

load-module module-loopback

(I also had to deal with some weird crackly/screeching noise issues by messing with mixing levels, but eventually, there was decent sound).

However, I notice now that sound from the PS3 arrives after a delay of about 0.5 - 1 second. Effects in games arrive that late, and video playback is obviously likewise horrid.

Searched around quite a bit, and it seems to have to do with pulseaudio but I don't know exactly how. Does anyone know how to fix this? It's not a hardware issue, since this setup worked fine in Jaunty. 

Thanks.

---

### Post by riverfr0zen on 2009-11-30
Resolved this issue by getting rid of pulseaudio as described in this thread:

[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

Works fine now, no latency from line-in source.

---

