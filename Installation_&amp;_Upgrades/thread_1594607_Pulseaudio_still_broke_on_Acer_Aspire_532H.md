---
title: "Pulseaudio still broke on Acer Aspire 532H"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Seano1957 on 2010-10-12
The input/mic on the 532h (and some others I think) still has the L/R cancellation issue so if your settings get reset or you do a clean install it'll need working around again.

I've found the easiest way is to set default-server = 127.0.0.1 in /etc/pulse/client.conf rather than pulling one of the faders down which brings a lot of hum with it for me and doesn't help if you need to record in stereo.

--sean

---

