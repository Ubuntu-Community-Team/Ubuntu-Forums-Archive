---
title: "Backing up the updates"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by acankat on 2007-02-07
is there a way to backup all updates and reinstall them over a fresh installed ubuntu? There are about 180 mbs of update for edgy and I really dont want to redownload same upgrades every time I install a new computer.

integrating the upgrades and user compiled kernels into the installation cd would also be great.

---

### Post by eniel on 2007-02-07
he trick I used in Dapper to do this is as follows:
go to /var/cache/apt/archives
copy the package files (*.deb) to a safe place
install ubuntu
copy the packages to /var/cache/apt/archives in your new installation.
if you install a package the package manager looks first in the archives and uses that package in stead of downloading it (if it's up to date)
If you want to clone your installation by installing all the packages from one machine on an other one take a look at
[http://www.debianadmin.com/clone-your-ubuntu-installation.html](http://www.debianadmin.com/clone-your-ubuntu-installation.html)

---

### Post by acankat on 2007-02-08
thanks! =D>

---

