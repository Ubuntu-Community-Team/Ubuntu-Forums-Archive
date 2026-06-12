---
title: "Synaptic upgrade wants to remove plymouth"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by ubuntubrian on 2012-03-27
10.10 Ubuntu on a Toshiba Satellite-
I have been getting a partial upgrade option with update manager which includes many linux kernel packages as well as others. I have run apt-get update and upgrade and many packages are held back. With Synaptic I can mark all upgrades and the linux kernel as well as the others are marked but Synaptic wants to remove the following:

friendly-recovery
plymouth-label
plymouth-theme-kubuntu-logo (and the same for xubuntu and ubuntu)
plymouth-X11
qgis-plugin-grass
xchat

I think some of these are necessary, yes? Plymouth itself would still be installed but I am not sure how to proceed. I would like to get out of the partial upgrade issue that I've now had for a couple of months.
Thanks

---

### Post by ubuntubrian on 2012-03-28
Here's the apt-get dist-upgrade for more info:

```
Calculating upgrade... Done
The following packages will be REMOVED:
  friendly-recovery plymouth-label plymouth-theme-kubuntu-logo
  plymouth-theme-ubuntu-logo plymouth-theme-xubuntu-logo plymouth-x11
  qgis-plugin-grass xchat
The following NEW packages will be installed:
  apg libgtk-sharp-beans-cil liblaunchpad-integration-common libmatecanvas
  libmatecomponent libmatekeyring libnotify-bin libpython2.7 libqgis1.7.4
  libtasn1-3-bin linux-headers-2.6.35-32 linux-headers-2.6.35-32-generic
  linux-image-2.6.35-32-generic mate-common mate-conf mate-conf-common
  mate-corba mate-menus mate-mime-data python-corba python-mate-desktop
  python-mate-menu python2.7 python2.7-minimal
The following packages have been kept back:
  banshee banshee-extension-soundmenu gnome-control-center grub-common grub-pc
  grub2 gtk2-engines-pixbuf launchpad-integration libboost-all-dev
  libgail-common libgail-dev libgail18 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev
  libical0 liblaunchpad-integration1.0-cil libplymouth2 libvmime0 mintmenu
  plymouth python-launchpad-integration python-software-properties
  software-properties-gtk software-properties-kde tomboy usb-creator-common
  usb-creator-gtk usb-creator-kde yelp
The following packages will be upgraded:
  liblaunchpad-integration1 linux-generic linux-headers-generic
  linux-image-generic python-qgis python-qgis-common qgis qgis-common
  qgis-plugin-grass-common qgis-providers qgis-providers-common xchat-common
```

---

### Post by Frogs Hair on 2012-03-28
Partial upgrades can be a problem when kernel updates are involved . I've   found waiting until all the packages are available on the server is best . I run check for updates until packages are all available . Broken packages can occur when running a partial upgrade and when all packages are located the partial option will no longer be offered.

---

### Post by QIII on 2012-03-28
+1. The general advice is just not to do partial upgrades.

---

### Post by ubuntubrian on 2012-03-28
Thanks and that is what I have heard/read. It's just that this has been an issue for about 4 months now. In any case I'll not do the partial.

Thanks again

---

### Post by Claus7 on 2012-03-28
Hello,

does laptops have different updates than desktops? I have not come across (if I recall correctly) about such an update, yet in desktop edition. I'm using plymouth as well. I'm just mentioning this in case you have altered something on your system about the updates...

Regards!

---

### Post by ubuntubrian on 2012-03-29
As far as I know I have done nothing to change the update schedule. I have quite a few PPA repos and maybe one of them is the problem. Nothing though with Plymouth or important items.

---

### Post by Claus7 on 2012-03-29
Hello,

I can see that you have packages that they are: kept back. I think that you have to take a look on the dependencies of your plymouth libraries.

In order for some packages to be kept back there is a reason ubuntu does that. I'm really sorry, yet I do not remember the case, only that because of having such packages I was not able to upgrade my system at the time.

There are specific commands that you can tell which dependencies are stuck and the like, yet I do not remember them. 

Take a look in here, this might help you more:
[http://ubuntuforums.org/showpost.php?p=10645501&postcount=4](http://ubuntuforums.org/showpost.php?p=10645501&postcount=4)

Regards!

---

