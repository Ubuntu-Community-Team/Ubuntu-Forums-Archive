---
title: "dpkg: error processing shared-mime-info"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by athlonshi on 2010-09-28
Hi, 
I am using 9.04 version. Since a few days ago (maybe after some updates), I have been encountering problems when installing packages. 
I tried to use dpkg --configure -a, but did not resolve the problem. 
The problem looks like below, for example I wanted to install gfortran
Does any one have similar experience? Thanks!
 
```
 subprocess installed post-installation script returned error exit status 245
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 xubuntu-desktop depends on thunar; however:
  Package thunar is not configured yet.
 xubuntu-desktop depends on thunar-volman; however:
  Package thunar-volman is not configured yet.
 xubuntu-desktop depends on xubuntu-default-settings; however:
  Package xubuntu-default-settings is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up xubuntu-gdm-theme (0.38) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing xubuntu-gdm-theme (--configure):
 subprocess installed post-installation script returned error exit status 245
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xfce4-places-plugin:
 xfce4-places-plugin depends on thunar; however:
  Package thunar is not configured yet.
dpkg: error processing xfce4-places-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up gfortran-4.4 (4.4.1-4ubuntu9) ...
No apport report written because MaxReports is reached already
                                                              Setting up gfortran (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/gfortran to provide /usr/bin/f95 (f95) in auto mode.

Errors were encountered while processing:
 shared-mime-info
 gnome-app-install
 gnumeric
 pidgin
 pidgin-libnotify
 pidgin-otr
 thunar
 thunar-archive-plugin
 thunar-media-tags-plugin
 thunar-thumbnailers
 thunar-volman
 xchat-common
 xchat
 xubuntu-default-settings
 xubuntu-desktop
 xubuntu-gdm-theme
 xfce4-places-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

