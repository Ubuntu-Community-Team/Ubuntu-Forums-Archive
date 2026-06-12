---
title: "Nvidia Drivers crash Lightdm"
date: 2015-02-24
forum: Installation &amp; Upgrades
---

### Post by jrdobelmann on 2015-02-24
After several months of trying to install nvidia-340 and cuda, I was finally able to get it to work.  I noticed, however, that cuda was kind of slow.  I tried changing the powermizer setting in nvidia-settings, but then shortly after, my computer crashed.  Now, whenever I turn my computer on, lightdm will just show a black screen, and the only way to fix it is to go into a console and remove nvidia* and cuda*.  After that it works fine, but whenever I try to reinstall the drivers, the same thing happens.  I tried to purge nvidia and cuda, but lightdm still won't start unless I uninstall the packages.  Is there any way I can get rid of this problem without reinstalling Ubuntu Studio?

---

### Post by dino99 on 2015-02-26
have you tried gdm instead ?
install it if not yet, then sudo dpkg-reconfigure lightdm, and choose gdm

---

### Post by jrdobelmann on 2015-02-27
I tried installing the drivers with gdm, it makes no difference.

---

### Post by dino99 on 2015-02-27
is your card able to use the 346 driver ? (more stable than 340)
maybe also some conflict with cuda: related to package(s) version installed that disturb lightdm

---

### Post by jrdobelmann on 2015-02-28
I was able to get the driver and cuda installed.  I'm noticing cuda is stil kind of slow, but I'll work on fixing that later.  Thank you.

---

