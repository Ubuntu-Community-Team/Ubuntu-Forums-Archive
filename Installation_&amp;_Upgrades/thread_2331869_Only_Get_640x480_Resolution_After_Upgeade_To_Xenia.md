---
title: "Only Get 640x480 Resolution After Upgeade To Xenial"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by typos1 on 2016-07-26
Just upgraded to 16.04 from 15.10 and the only resolution I get is 640x480. My device has AMD HD8510G graphics, my monitor is a Samsung LED with 1920x1080 resolution, I had no such problems with 15.10. I was expecting possibly poor performance due to the lack of flgrx support, but not this. I ve tried changing the resolution using xrandr, I always get :

 " Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
   640x480       73.00* "

The gamma problem is not overcome by coding " xrandr --output default --gamma 0:0:0 " and because there is no name for the display it wont let me add another resolution. I m stumped . . . and my eyes are hurting from trying to do it all at 640x480 !!

Help

---

### Post by typos1 on 2016-07-26
OK, after a lot of searching I need to purge flgrx, so problem sorted, thanks for all your help @Typos1. lol.

---

