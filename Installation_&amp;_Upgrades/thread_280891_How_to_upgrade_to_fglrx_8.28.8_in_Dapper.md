---
title: "How to upgrade to fglrx 8.28.8 in Dapper?"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by DC@DR on 2006-10-20
Hi guys,

Since I really need a new pairmode feature in fglrx v8.28.8 that current verison 8.25.8 doesn't support so well, how could I safely upgrade to the latest version of fglrx driver since the package is not available for Dapper (only in Edgy)? I mean I got v8.25.8 installed, with 3D accelerated, if I download the binary package from ATI website and install, will it break anything? Please help me with this, I really need it, many thanks :)

EDIT: OK, by googling, I found this nice packages: [http://seveas.imbrandon.com/dists/dapper-seveas/drivers/](http://seveas.imbrandon.com/dists/dapper-seveas/drivers/). I will try to install this and report the result here. :)

---

### Post by pay on 2006-10-20
I like this guide (method 2) [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) 
To make it work for 8.28.8 instead of 8.29.6 download the 8.28.8 package;)

---

### Post by DC@DR on 2006-10-20
OK, I got it installed correctly by installing the packages in my first post, but the key point here is that to set DISABLE_MODULES="fglrx" in /etc/default/linux-restricted-modules-common. Otherwise, it will not work correctly.Thanks **pay** for the link, I will give it a try if there's a need to upgrade to version 8.29.6 :)

---

