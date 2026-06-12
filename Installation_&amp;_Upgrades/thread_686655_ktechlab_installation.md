---
title: "ktechlab installation"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by moon_star on 2008-02-03
can anybody tell me how to install Ktechlab ? when i type ./configure --prefix=$(kde-confix --prefix) it gives the following error
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
Where can i download the following packages:
kdelibs-devel(KDE libraries>=3.2)
gpsim-devel
readline-level

---

### Post by Partyboi2 on 2008-02-03
Make sure you have universe repo enabled under Software Sources. From a terminal
```
sudo apt-get installl ktechlab
``` or use the synaptic program that comes with kde not sure what it is called.
or manually (no internet)
[http://packages.ubuntu.com/gutsy/kde/ktechlab](http://packages.ubuntu.com/gutsy/kde/ktechlab)

If for some reason you need to compile this package make sure you have build-essential installed and you can look for the packages you are missing from 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

