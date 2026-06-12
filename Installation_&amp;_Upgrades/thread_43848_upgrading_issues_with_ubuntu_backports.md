---
title: "upgrading issues with ubuntu backports"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by ubuntulnx on 2005-06-23
hi.. ive been continuesly upgrading all security upgrades. some time ago the marillat debs did not work anymore for me. 

so i deactivated:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

and i activated:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 


but after making the suggested changes, somehow ubuntu wants me to install updates for below packages..

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
mozilla-firefox mozilla-firefox-gnome-support
The following packages will be upgraded:
file-roller foomatic-db-hpijs foomatic-filters-ppds gaim gaim-data gimp
gimp-data gimp-python gnome-btdownload gnome-menus hpijs libgcc1 libgimp2.0
libgnome-menu0 libnspr4 libnss3 libsmbclient python-xdg python2.3-samba
python2.4-samba samba-common smbclient synaptic totem totem-xine xchat
xchat-common
27 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 42.6MB of archives.
After unpacking 2140kB of additional disk space will be used.
Do you want to continue [Y/n]?


why is that? and what harm could i do going ahead with the update? and what happens if i eliminate both marillat and backports? how can i make sure that i only update the marillat part of the backports.

i think i only installed the gstreamer-mad package from marillat. THANKS!!

---

