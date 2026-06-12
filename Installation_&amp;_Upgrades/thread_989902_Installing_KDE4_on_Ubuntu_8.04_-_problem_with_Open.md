---
title: "Installing KDE4 on Ubuntu 8.04 - problem with OpenOffice 3"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by AMAMH on 2008-11-22
When I requested KDE4 (pack name : **kubuntu-kde4-desktop**) to be installed on my Ubuntu 8.04 , I noticed that it required OpenOffice2 to be installed (which I replaced with OpenOffice3) and also required that a package named **openofice.org-debian-menus** to be uninstalled (I didn't know then that this is the integration package for OpenOffice 3) , I unmarked all openoffice2 packages , but left the integration package to be uninstalled , after the installation I found that OpenOffice isn't installed , so I figured out that this is because that strange package openofice.org-debian-menus was uninstalled and when I tried to install it again from Adept Man or Synaptics it wasn't found , after some search on the internet I found that actually the package was responsible for integration with the system and it was inside the openoffice3 installation archive (wich contains a lot of packs for installing openoffice3) and not on the internet and that's why Adept Man couldn't find it , so I got it from the archive (and its name was **openoffice.org3.0-debian-menus_3.0-9354_all.deb**) and installed it again then OpenOffice3 appeared again.

**So the whole prob is that KDE4 tries to uninstall the integration pack for OpenOffice3 and reinstall the old OpenOffice 2 , and u should prevent that by unchecking these changes.**:)

---

