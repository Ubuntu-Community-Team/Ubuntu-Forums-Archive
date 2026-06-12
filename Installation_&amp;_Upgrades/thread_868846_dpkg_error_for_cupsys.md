---
title: "dpkg error for cupsys"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by kcoylenet on 2008-07-24
I was doing updates to gutsy gibbon, and I keep getting this error:

dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1

I've done apt-get -f install a number of times and this keeps happening. I tried:

apt-get -r cupsys

and got

 hplip depends on cupsys (>= 1.1.20).
 ubuntu-desktop depends on cupsys.
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is to be removed.
  Package cups is not installed.
 bluez-cups depends on cupsys.
 hal-cups-utils depends on cupsys.
 cups-pdf depends on cupsys.
 cups-pdf depends on cupsys (>= 1.1.15).
 cups-pdf depends on cupsys.
 cups-pdf depends on cupsys (>= 1.1.15).
dpkg: error processing cupsys (--remove):
 dependency problems - not removing

Oddly enough I can still print... but if there's something here I should fix I sure would like to fix it.

Would moving up to hardy-heron take care of this? If so, how do I do that?

Thanks,
kc

---

