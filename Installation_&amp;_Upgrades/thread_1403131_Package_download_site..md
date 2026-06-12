---
title: "Package download site."
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by pejohnson on 2010-02-09
I have an installation of Ubuntu 9.04 on a standalone workstation.  I need to download all of the packages for the normal installation and updates.

Does anyone know where I can pull the complete package sets rather than individual packages rather than one at a time?

---

### Post by Cheezespread on 2010-02-09
The list here gives you the complete package set for Jaunty . 

[http://packages.ubuntu.com/jaunty/allpackages](http://packages.ubuntu.com/jaunty/allpackages)

_For Jaunty updates and backports_

[http://packages.ubuntu.com/jaunty-updates/allpackages](http://packages.ubuntu.com/jaunty-updates/allpackages)
[http://packages.ubuntu.com/jaunty-backports/allpackages](http://packages.ubuntu.com/jaunty-backports/allpackages)


I believe ```
apt-get -d 
```option would dowload the packages for you if you specify the name .

 /var/apt/cache/archives usually contain the .deb  packages that get downloaded when you install apps . Have a look there , as I am not sure of this .

---

