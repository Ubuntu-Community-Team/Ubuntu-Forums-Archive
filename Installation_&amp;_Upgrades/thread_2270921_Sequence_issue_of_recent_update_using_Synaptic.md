---
title: "Sequence issue of recent update using Synaptic"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2015-03-26
Updates for 03/24/2015 had sequence of install issues which wanted to remove necessary packages (gut the system) updating the following packages:
The following sequence of package update worked without having to remove any packages or get the notice. 
1.) libgbm1 (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
2.) libxatracker2 (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
3.)libopenvg1-mesa (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
4.)libegl1-mesa (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
    libegl1-mesa-drivers (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
    libgl1-mesa-glx (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
    libglapi-mesa (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
    libgles2-mesa (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
    libwayland-egl1-mesa (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4
5.)libgl1-mesa-dri (10.1.3-0ubuntu0.3) to 10.1.3-0ubuntu0.4

One of the reasons I still use Synaptic is the easily accessible history which does not exist in the updater.
Hope this helps.

P.S: I updated the security claas packages first if that helps anyone understand this.

---

### Post by dino99 on 2015-03-26
in such a case it usually means that some versions conflict, for example when package(s) from ppa and/or third parties are installed
or the updates are not (yet) complete

---

