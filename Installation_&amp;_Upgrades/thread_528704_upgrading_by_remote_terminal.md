---
title: "upgrading by remote terminal"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by davidshere on 2007-08-18
I manage multiple Ubuntu machines both at home and at work, and I've noticed that doing upgrades by remote terminal to those machines (ssh) seems to update some packages, but not others.  It says "The following packages have been kept back". (Example below)  I have to physically go to the machine (or VNC) in order to update the remaining packages.  Is there a way to force those packages to not be kept back when upgrading via remote terminal?

```
root@warthog:/home/david# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data app-install-data-commercial bind9-host dbus dbus-1-utils
  dnsutils evolution-data-server evolution-data-server-common file firefox
  firefox-gnome-support gimp gimp-data gimp-python gnome-app-install
.........
  vim-runtime vim-tiny xfce4-terminal xscreensaver xscreensaver-data
  xscreensaver-gl
102 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 157MB of archives.
After unpacking 3875kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by Maylar on 2007-08-18
You can still do this through ssh. Take note of the packages that will be kept back and go ahead with the update. Once the update is finished, use

sudo apt-get install package-name

You can put all of the packages on one line seperated by a space for each one. Hope this helps

EDIT: fixed typo

---

### Post by davidshere on 2007-08-18
You see, that solution is so friggin' obvious that I didn't see it at all.  

Thanks!! :)

---

