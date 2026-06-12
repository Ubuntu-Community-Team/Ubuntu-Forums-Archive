---
title: "Remove unneeded packages from Xubuntu"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by MatBi on 2006-06-20
Hi,
I've installed xubuntu on a machine with a small hdd, and i'd like to remove all the packages i don't need, like abiword*, openoffice* and tons more. 
When i try to remove any of them with apt-get remove, it asks to remove also the xubuntu-desktop package, and this is bad, i think.
Is there any way to keep xubuntu-desktop and remove the rest?
Thanks,
MatBi

---

### Post by 5-HT on 2006-06-20
xubuntu-desktop is simply a metapackage that depends on all the packages Xubuntu devs felt should be included to have a nice XFCE desktop experience.

You can safely delete xubuntu-desktop and will have to if you want to remove some packages that it depends on.

However, it is recommended to reinstall xubuntu-desktop prior to upgrading to a new release of Xubuntu just to help the upgrade go smoothly. Additionally,  new packages may be included in later releases of Xubuntu and xubuntu-desktop will ensure you get all of Xubuntu's default/recommended packages).

HTH

---

### Post by MatBi on 2006-06-20
Thanks for the quick and comprehensive answer!

---

