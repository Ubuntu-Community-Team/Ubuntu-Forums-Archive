---
title: "Use HDAPS to auto rotate Tablet screen and inputs using think-rotate in 13.04"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by lklk on 2013-05-12
I installed think-rotate ([https://github.com/martin-ueding/think-rotate](https://github.com/martin-ueding/think-rotate)) to rotate the screen and Wacom inputs on my Thinkpad x230t running 13.04. Now I am trying to get it to autorotate based on the accelerometer but I can not figure out where HDAPS or SMAPI output to. According to thinkwiki ([http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)) the outputs are in /sys/devices/platform but my systems does not have hdaps or smapi in that directory and using find in / did not give me there locations even tough both packages are installed.

I don't have any experience with scripting for hardware control but if I can understand HDAPS output I think I would be able to right a script that automatically runs think-rotate to give the correct orientation.

I would have tried Magick Rotation ([https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)) but it is not compatible with 13.04. Also I am not sure it disables the multitouch when the pen is close like the think-touch or the touchpad when rotated like think-touchpad do in think-rotate.

---

