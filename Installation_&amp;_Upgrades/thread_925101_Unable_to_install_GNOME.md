---
title: "Unable to install GNOME"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by neonl on 2008-09-20
Hello all.

I installed Ubuntu from the minimal CD using the 'cli' option just to get a plain command line installation from which i want to install the packages I want to.

However, after installing xorg, when trying to install the 'gnome' package i can't do it. The problem, apparently is that '[gnome-desktop-environment]("http://packages.ubuntu.com/hardy/gnome-desktop-environment")' has an unmet dependency: gnome-keyring-manager (>= 2.20.0) - which actually doesn't exist.

From what I understood (currently i'm not an Ubuntu user so i'm not updated with this stuff) the gnome-keyring daemon itself is installed through the package 'gnome-keyring' - which is a dependency for gnome-desktop-environment too - but how can I (it's possible, right?) install GNOME?

Cheers.

---

### Post by Partyboi2 on 2008-09-20
gnome-keyring-manager is know longer in the ubuntu repo's it has deprecated.
Maybe as another option you could install ubuntu-desktop instead.

Edit: you could try manually installing gnome-keyring-manager and see if you have any sucess
[https://launchpad.net/ubuntu/hardy/i386/gnome-keyring-manager/2.20.0-1ubuntu1](https://launchpad.net/ubuntu/hardy/i386/gnome-keyring-manager/2.20.0-1ubuntu1)

---

### Post by neonl on 2008-09-20
Yes, i know that. The issue is that i want a plain gnome install without the Ubuntu desktop just with gnome itself... But the gnome meta-package is not even updated (2.20 - in Ubuntu desktop gnome components are in 2.22)...

---

