---
title: "Safe to upgrade &quot;gnome/default.list&quot;?"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by putz3000 on 2011-12-15
I just installed 11.10 on my work laptop. I was having troubles installing Google Chrome so I finally decided to check for more updates. Since I prefer using apt-get, I ran the update then upgrade commands from terminal. During the installation of these updates, I was suddenly greeted with this message:

> Configuration file `/etc/gnome/defaults.list'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** defaults.list (Y/I/N/O/D/Z) [default=N] ? 


First, I have no idea how I "modified" the defaults list since it is a fresh install. That said, I don't know if I should replace or keep the current version. 

Does anyone know what this is about? Is it safe to replace? What are the possible consequences for replacing this file?

---

### Post by zvacet on 2011-12-16
I think it is best to install **package maintainer's version,**but maybe someone know better.

---

