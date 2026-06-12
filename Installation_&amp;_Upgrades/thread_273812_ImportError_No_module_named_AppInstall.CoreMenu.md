---
title: "ImportError: No module named AppInstall.CoreMenu"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by amslonewolf on 2006-10-08
Hello - I am trying to intall ubuntu-desktop after upgrading to Edgy, but I keep getting the following error. Any guidance or suggestions on how to fix this.

thanks,

```

Setting up gnome-app-install (0.2.16) ...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 17, in <module>
    from AppInstall.CoreMenu import *
ImportError: No module named AppInstall.CoreMenu
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up vlc-plugin-esd (0.8.6-svn20060918.debian-1ubuntu3) ...
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

---

### Post by abben on 2007-04-30
I am also getting this problem

---

