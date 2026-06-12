---
title: "[SOLVED] upgrade feisty to gutsy without ubuntu-desktop"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by duncan.hawthorne on 2007-10-31
is it possible to upgrade without the ubuntu-desktop package (i'm running very low on disk space, and dont want to install all of the dependencies of ubuntu-desktop that i have removed)

also, what would happen if i ran out of temporary disk space during the upgrade (due to the extra space needed to hold the temporary .deb files)

---

### Post by ruibernardo on 2007-11-01
Yes it is, check this page [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades),  point 4 applies to servers, but I think it can be used to upgrade without GUI.

About the disk space, it depends on the number of packages you have installed. Be prepared for the deb package space and the space they will required after they are installed. 

Usually the final space is the space used by the new kernel (200-300 MB) plus the deb packages you downloaded (from something like 600MB to various GB, depending on what you have installed) plus some temp space for the upgrade process.

To free some space you could empty your package cache directory (/var/cache/apt/archives) by removing only the *.deb packages that are in it.
```
 sudo rm -rf /var/cache/apt/archives/*.deb
```

---

### Post by zvacet on 2007-11-01
i think you need ubuntu-desktop meta package to do upgrade.Do you have any other partition you can shrink and give extra space to the root?You can do it by download Gparted live CD.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by ruibernardo on 2007-11-01
> **zvacet said:**
> i think you need ubuntu-desktop meta package to do upgrade.

From the [webpage]("https://help.ubuntu.com/community/GutsyUpgrades") I've pointed: 

> Network upgrade for Ubuntu servers (recommended)

If you run an Ubuntu server, you should use the new server upgrade system.

   1.

      Install update-manager-core if it is not already installed:

      sudo apt-get install update-manager-core

   2.

      Launch the upgrade tool:

      sudo do-release-upgrade

   3.

      Follow the on-screen instructions.So this would do a dist-upgrade without update-manager - the GUI of update-manager-core that is in ubuntu-desktop. Since duncan doesn't have ubuntu-desktop (and don't want it), I would recommend this process.

---

### Post by duncan.hawthorne on 2007-11-03
do-release-upgrade worked
thank you :D

---

