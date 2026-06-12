---
title: "apt-get and cdrom"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by nonutopia on 2005-04-15
hello all.

i have some old pc's that are being for all kind of stuff. i want to install ubuntu on some of these. yet they dont have cdrom boot. so i install in one computer and put the hardisk in the other. now will apt-get understand that when i dont have a cdrom in the pc it cant install packages from cd ? and how in general does it know wich package it should get from the internet and wich from the cdrom?

---

### Post by heimo on 2005-04-15
apt-get looks for sources of packages in */etc/apt/sources.list* and there's also the line for CD. You can manage these repositories also with System->Administration->Ubuntu Update Manager->Preferences.

---

