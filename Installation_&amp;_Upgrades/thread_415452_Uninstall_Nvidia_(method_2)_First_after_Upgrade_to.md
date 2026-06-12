---
title: "Uninstall Nvidia (method 2) First after Upgrade to 7.04"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by acegolfer on 2007-04-20
If you installed Nvidia beta driver using method 2 in Edgy, the driver may not properly work after upgrading to 7.04. Beryl, Compiz (white screen) don't work.

To get it work, you need to enable Nvidia driver in Restricted drivers manager. Unfortunately, if you already installed the driver manually, the manager says nothing to install. You need to first remove the driver (using method 2).

Then start gdm using nv driver. The restricted drivers manager will auto detect your nvidia video card. Just run the program and enable the Nvidia driver. (IIRC,  restart was required.)

You should be able to use Beryl or Compiz then.

---

