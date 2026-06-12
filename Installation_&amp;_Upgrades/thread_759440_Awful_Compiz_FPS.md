---
title: "Awful Compiz FPS"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Auctionedllama@gmail.com on 2008-04-19
Hi, I just installed compiz with a fully working X1650 ATI pro (512 mb). The only compiz options I have are the basics and the cube. Now it seems that when I enabled the xserver-xgl file thing I got horrible FPS no matter what, even if compiz isn;t enabled. Is there anyway to fix this? Thanks..

---

### Post by Rocket2DMn on 2008-04-19
Have you enabled the restricted drivers?
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
or using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (works for ati cards)

---

### Post by Auctionedllama@gmail.com on 2008-04-19
Yes, the driver is enabled and it says I'm running the fglrx driver..

---

### Post by Rocket2DMn on 2008-04-19
OK, can you tell us what your framerate is by running
```
glxgears -info
``` (let it run for 20 seconds or so).
Where are you noticing a drop in frame rate?  Watching movies?  Playing games?

---

