---
title: "Can't find adduser when upgrading"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by roylez on 2006-08-07
Hi, at the end of last week when i was doing a regular upgrade, some errors came up. Warning messages at the setting stage said "adduser: command not found". However, I am quite sure that adduser is already there under /usr/sbin/. Also, there are some warnings said the setting scripts did not have permission to some files. That is strange! I have noticed SELinux libraries have been added to the respository, and it is installed on my box. Is it possibly because the incorrect configure of SELinux? Any suggestions will be appreciated.

> Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up cupsys (1.2.2-0ubuntu0.6.06) ...
/var/lib/dpkg/info/cupsys.postinst: line 54: adduser: command not found
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 127
Setting up cupsys-client (1.2.2-0ubuntu0.6.06) ...
/var/lib/dpkg/info/cupsys-client.postinst: line 36: adduser: command not found
dpkg: error processing cupsys-client (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-menus (2.14.3-0ubuntu1) ...
Sorry [Errno 13] Permission denied: '/usr/lib/python2.4/site-packages/debconf.pyo'
Sorry [Errno 13] Permission denied: '/usr/lib/python2.4/site-packages/drv_libxml2.pyo'
Sorry [Errno 13] Permission denied: '/usr/lib/python2.4/site-packages/libxml2.pyo'
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 1
Setting up language-selector-common (0.1.20.1) ...
Sorry [Errno 13] Permission denied: '/usr/lib/python2.4/site-packages/debconf.pyo'
Sorry [Errno 13] Permission denied: '/usr/lib/python2.4/site-packages/drv_libxml2.pyo'
Sorry [Errno 13] Permission denied: '/usr/lib/python2.4/site-packages/libxml2.pyo'

[interrupt]
dpkg: error processing language-selector-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.1.20.1); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-bsd:
 cupsys-bsd depends on cupsys-client (= 1.2.2-0ubuntu0.6.06); however:
  Package cupsys-client is not configured yet.
dpkg: error processing cupsys-bsd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on cupsys-bsd; however:
  Package cupsys-bsd is not configured yet.
 ubuntu-desktop depends on cupsys-client; however:
  Package cupsys-client is not configured yet.
 ubuntu-desktop depends on gnome-menus; however:
  Package gnome-menus is not configured yet.
 ubuntu-desktop depends on language-selector; however:
  Package language-selector is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-client
 gnome-menus
 language-selector-common
 language-selector
 cupsys-bsd
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

