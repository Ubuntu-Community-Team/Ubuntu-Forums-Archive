---
title: "unable to install epson perfection v500 driver after upgrade to 12.04"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by jazz612 on 2012-05-18
i lost i-scan functionality after clean install of ubuntu studio 12.04. 
i downloaded iscan_2.28.1-3.ltdl7_amd64.deb but it fails to reinstall the driver.  

Image Scan! is a graphical scanner utility for people that do not need all the bells and whistles provided by several of the other utilitiesout there (xsane, QuiteInsane, Kooka).

At the moment it only supports SEIKO EPSON scanners and all-in-ones.

However, the scanner driver it provides can be used by any other SANEstandard compliant scanner utility.

Note that several scanners require a non-free plugin before they canbe used with this software.

---

### Post by maxbur on 2012-06-14
The iscan developers suggest you install the "data package" first:
# dpkg --install iscan-data_$ver-$rel_all.deb

It's a separate download from epson.

---

