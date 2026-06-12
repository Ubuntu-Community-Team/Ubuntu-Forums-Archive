---
title: "trying to update video driver."
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by CastorTroyXXIV on 2009-12-03
im trying to update my video driver, i downloaded the update and tried running it, but it says NVIDIA-Installer must be run as root. do i put the file where the nivida driver is? and where would it be?

---

### Post by hal10000 on 2009-12-03
You don't need to download the installer from the nvidia site.

I you are using gnome, then install jockey-gtk. In case you are using kde, then install jockey-kde and run it:
```
gksudo jockey-gtk
``` or ```
kdesudo jockey-kde
```. This will do the job for you.

As an alternative you may install (and run) the package envyng-qt.

---

