---
title: "Fresh in stall of 14.04 wont allow me to install mysql"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by David_Bloom on 2014-10-03
I just installed a fresh 14.04 version, and all update are current. The last thing on my list was to install mysql, and phpmyadmin.

sudo apt-get install apache2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
The following packages were automatically installed and are no longer required:
  alacarte gimp-data gimp-help-common gimp-help-en gir1.2-gconf-2.0
  gir1.2-panelapplet-4.0 gnome-applets-data gnome-media gnome-panel-data
  gstreamer0.10-gconf kde-l10n-engb libamd2.3.1 libbabl-0.1-0 libcamd2.3.1
  libccolamd2.8.0 libcholmod2.1.2 libgegl-0.2-0 libgfortran3 libgimp2.0
  libgnome-media-profiles-3.0-0 libjavascriptcoregtk-1.0-0 liblapack3 libmng2
  libumfpack5.6.2 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,224 kB of archives.
After this operation, 0 B of additional disk space will be used.

Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,224 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
dpkg: error processing package phpmyadmin (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Neither program has been loaded in the past, yet is say their current?

I've try everything I could find on the Ubuntu site and nothing works. Even tryed synoptic manager to try to re-install, and or remove,but
again more errors.

Ok, so I figure something happend during the new install. I Re-install Ununtu 14.04. This time I try from the Software Center. Again the same error.

Well, I surely cant figue out the problem, maybe one of you guys can.

David

---

### Post by zvacet on 2014-10-03
In terminal type

```
sudo dpkg --configure -a
```

---

### Post by David_Bloom on 2014-10-03
Zvacet thanks for responding. Tried that and got this....

sudo dpkg --configure -a

dpkg: error processing package phpmyadmin (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 phpmyadmin

Here is whats so strange about the whole thing. Niether mysql or phpmyadmin have ever been installed
remember this a fresh install

---

### Post by zvacet on 2014-10-03
To se if you have package installed 

```
 dpkg --get-selections
```

if it is there try to reinstall 

```
sudo apt-get install --reinstall  phpmyadmin
```

---

