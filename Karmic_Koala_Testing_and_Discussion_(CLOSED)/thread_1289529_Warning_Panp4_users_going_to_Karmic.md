---
title: "Warning Panp4 users going to Karmic"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by betrunkenaffe on 2009-10-12
Just installed Karmic beta, worked fine until I installed nVidia 185 drivers, now it boots to a non-gui login and screen flashes on an off repeatedly.

Going to do further testing but there might be an issue there.

---

### Post by thomasaaron on 2009-10-12
Thanks for the heads up. Did you have any other driver options?

---

### Post by betrunkenaffe on 2009-10-12
I did a basic install and then loaded nVidia drivers. I'll be reinstalling, doing system76 first then looking at nVidia drivers.

---

### Post by zeronothing on 2009-10-12
I'm not sure what nvidia card you have (I have a Desktop 7950GT) but did you try and do the command "sudo nvidia-xconfig" to set the xserver config file? I had to do this for my setup.

I'm also using the 9.10 beta

---

### Post by betrunkenaffe on 2009-10-16
I think I had a combination of factors glitch, I reinstalled, issue resolved. Using 185 driver fine now.

I had dual screens connected so think that might have been it.

---

