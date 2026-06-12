---
title: "Shuttle X50 V2 touch screen problem"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by papegoj on 2010-04-27
I've tried Ubuntu 9.1 both 32/64-bit but it crashes on install reporting a CRTC -22 problem. 

Ubuntu 10.0.4RC worked. Then I tried installing touch screen eGalax using drivers from [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm) . But it crashes on calibration. I've tried both 32-bit and 64-bit systems. Should I use some other drivers?

Please I'm a newbie so I really dont know what more to try, please help.

---

### Post by papegoj on 2010-04-27
Hm okay, I managed to install Ubuntu 9.10 32-bit in safe graphic mode. 

The touchscreen seam to work alot better in this version of Ubuntu but.. I'm in safe mode 1024x768. The Shuttle X50 V2 seam to have a Intel GMA 3150. And if it worked in Ubuntu 10 it should work in ubuntu 9.1... right? I've tried to update but still I'm in 1024..

Any ideas? Please

---

### Post by papegoj on 2010-04-27
updated xorg-server-video-intel from:
1. ppa:ubuntu-x-swat/x-updates
2. ppa:xorg-edgers/drivers-only

updated /etc/X11/xorg.conf
Driver "vesa" to Driver "intel".
*reboot*

Didnt work, had to start ubuntu in safe mode. Hm, any ideas? :)

---

