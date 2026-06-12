---
title: "Tried to install WICD, now have no wireless"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by paulbtucker on 2008-10-06
Hey guys,

I'm running 8.04 hardy heron on an Asus 1000h eee-pc.  I had been having problems connecting to my universities secured network so I wanted to switch to WICD and try it out against the Network Manager. That didn't work, and now I'm stuck without any network connectivity.  I tried reinstalling NM from .deb files from Ubuntu's website, but the applet won't load, and I can't update any of the packages.  

How do I restore my Network Manager?

---

### Post by imdano on 2008-10-07
If you have an ethernet cable you can probably connect by running ```
sudo ifconfig eth0 up
sudo dhclient eth0
```in the console.  From there you can use apt to reinstall NM.

---

