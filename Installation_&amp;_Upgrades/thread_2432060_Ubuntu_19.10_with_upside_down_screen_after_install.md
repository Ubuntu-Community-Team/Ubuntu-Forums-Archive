---
title: "Ubuntu 19.10 with upside down screen after install but the mouse orientation fine"
date: 2019-11-26
forum: Installation &amp; Upgrades
---

### Post by dvdme on 2019-11-26
Hi!

I installed Ubuntu 19.10 on my laptop and my screen was upside down on the first boot. 
The odd thing was that the mouse was in the correct orientation and when I clicked the mouse it wasn't agreeing with the image behind.

Using ```
xrandr -o normal
``` or ```
xrandr -o inverted
``` didn't solved anything because the mouse would then flip over. 

I eventually fixed it by removing the package ```
apt remove iio-sensor-proxy
```.

What was this package doing?

---

