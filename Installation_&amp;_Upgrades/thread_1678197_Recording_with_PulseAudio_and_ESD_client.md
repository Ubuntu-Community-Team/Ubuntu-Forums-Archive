---
title: "Recording with PulseAudio and ESD client"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by arunasr on 2011-01-29
I want to use xoscope which can use DSP or ESD as input. 

I tried Pulse DSP simulation. Unfortunately, padsp spits out "unknown ioctl".

Downloaded xoscope source and esd-dev, recompiled. When I chose ESD as input, it displays "connect timeout" immediately.

My other recording applications, such as Audacity, Linphone and Skype, work no problem.

Does PulseAudio actually support ESD recording interface? The PulseWiki says it is drop-in replacement for ESD, applications should be able to _**output**_ without any problems. No mention about "input"...

---

