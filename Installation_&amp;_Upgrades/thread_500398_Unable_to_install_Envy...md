---
title: "Unable to install Envy.."
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by mu:te on 2007-07-13
So I typed in "sudo dpkg -i envy+install.deb" and I got this..

root@mentos:~/Desktop# dpkg -i envy_0.9.6-0ubuntu1_all.deb 
(Reading database ... 88210 files and directories currently installed.)
Preparing to replace envy 0.9.6-0ubuntu1 (using envy_0.9.6-0ubuntu1_all.deb) ...
Unpacking replacement envy ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured

---

### Post by yabbadabbadont on 2007-07-13
Now try running ```
sudo apt-get -f install
``` and see if it helps.

---

