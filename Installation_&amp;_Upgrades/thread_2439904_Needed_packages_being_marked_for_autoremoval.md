---
title: "Needed packages being marked for autoremoval??"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by u666sa on 2020-04-03
I haven't tried a lot of Linux, just Fedora, and I never met this kind of stuff before.  Is this normal?  Is this a bug?  

Packages, needed packages are being marked for autoremoval.  Example:

[url=https://imgur.com/8wTyd8E.png]
  [img]https://imgur.com/8wTyd8E.png[/img]
[/url]

amd64-microcode gnome-system-monitor intel-microcode iucode-tool libburn4 libisofs6 libjte1 libmetacity1 metacity-common mousepad ristretto thermald tp-smapi-dkms xfburn

gnome-system-monitor --- I have gnome, and I might need gnome system monitor.
mousepad --- I'm using it along side with gedit.
xfburn --- it's part of XFCE.

What's going on here??

---

### Post by CatKiller on 2020-04-03
> **u666sa said:**
> What's going on here??

When you install a package it depends on other packages. The package that you've installed yourself is marked as "manually installed" and the dependencies that get pulled in with it are marked as "automatically installed". If you remove the package that you've manually installed then all those automatically installed dependencies are orphaned. As far as the package manager is concerned, you don't need them any more (which is generally true). So it marks them for auto-removal. 

The ones that you actually want to keep, even though you've removed the packages that brought them in, you can mark as manually installed, either by actually marking them as manually installed or just running the install command for that package. Then the package manager will know that the package is one that you have because you want it, rather than one that you still have by accident, and it won't try to auto-remove it.

---

### Post by u666sa on 2020-04-03
> **CatKiller said:**
> The package that you've installed yourself is marked as "manually installed" and the dependencies that get pulled in with it are marked as "automatically installed".

Ok..

Gnome system monitor is part of Ubuntu 18.04 installation.  It is installed during system install.  Why is it marked for auto removal?

---

### Post by deadflowr on 2020-04-03
gnome-system-monitor is a snap package in 18.04 not an apt package, so if it was installed as an apt you installed in manually.

---

