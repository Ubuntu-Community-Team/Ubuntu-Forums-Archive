---
title: "nVidia + Gutsy Gibbon, how I got it to work"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by rolf-c on 2007-10-19
I know several folks are having fits getting nVidia drivers loaded with 7.10.  I'm using an nVidia GeForce Ti 4200 and after my initial upgrade to 7.10 I was running in VESA mode.

This makes sense, however, since the nVidia drivers are tied to the kernel.  Kernel upgrade = lost video drivers for me.

So, I got the latest ENVY from the author at [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html").  Note his page lists 7.10 as one of the supported environments.

I installed it on my system, then ran 
```
sudo envy -g
```

Worked as advertised.  I'm up and running just like I was with 7.04.

---

