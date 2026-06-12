---
title: "X borks after upgrade (can't find font fixed)"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by enigma_0Z on 2005-11-18
OK, just upgraded to breezy, but now X borks whenever I try to start it up (either via startx or thru a DM). It says that it cannot load the default font, "fixed". Is there something I missed? I ran apt-get dist-upgrade, and apt-get install ubuntu-desktop kubuntu-desktop. Thanks.

---

### Post by invalid on 2005-11-19
Try
```
sudo dpkg-reconfigure xserver-xorg
```

Cheers,
Cb

---

