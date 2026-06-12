---
title: "which file in which package"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by mvdberg112 on 2008-01-16
Running Ubuntuu 7.10 Gutsy on one computer and Xubutu on another.
For whatever reason gksu or displayconfig-gtk was not installed.
I did not know in which package gksu or displayconfig-gtk is part of.

1) How can I find out which file/program is part of which package?
thanks in advance!
(i tried to do a search on this forum, but could not find it)

---

### Post by Partyboi2 on 2008-01-16
You can install the packages with
```
sudo apt-get install gksu displayconfig-gtk
```If you want to check out what they depend on you can go to
 [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for the package.
Another way is to open up synaptic package manager For gnome (System>Admin>Synaptic Package Manager) and search for the package and then click on properties and this will display more info on the package

---

### Post by mvdberg112 on 2008-03-03
Sorry for the late reply. Thanks for this info!  I see that package "gksu" contains "displayconfig-gtk".

Yes, the above methods are very helpful. However, how could I find out that this is the case, other then asking a question here? And how can I find out, even when gksu or  displayconfig-gtk are not yet installed at all. It is easier to find out what is installed, and that package XYZ contains piece, A and B and C, but if XYZ is not installed, it is hard to find out that in order to have B, one needs to install XYZ.

---

### Post by mvdberg112 on 2008-03-03
Sorry for the late reply. Thanks for this info!  I see that package "gksu" contains "displayconfig-gtk".

Yes, the above methods are very helpful. However, how could I find out that this is the case, other then asking a question here? And how can I find out, even when gksu or  displayconfig-gtk are not yet installed at all. It is easier to find out what is installed, and that package XYZ contains piece, A and B and C, but if XYZ is not installed, it is hard to find out that in order to have B, one needs to install XYZ.

---

