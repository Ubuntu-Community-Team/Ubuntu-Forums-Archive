---
title: "Installation of 12.04 beta 2 on EEE PC 701 4GB SSD"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by GH68 on 2012-04-20
I am trying to install the beta 2 version of Ubuntu 12.04 on my EEE PC 701, which has an SSD disk of only 4.0 GB. The installation application complains about the disk size and for older versions, even beta 1 of 12.04, I have seen several people describing a workaround that includes modifying the value of min_disk_size in usr/lib/ubiquity/plugins/ubi-prepare.py from min_disk_size = size * 2 to something like min_disk_size = size * 1.4. However, for the beta 2 version, I do not find a definition of min_disk_size in usr/lib/ubiquity/plugins/ubi-prepare.py. 

Is there another variable to be set in that file or eleswhere or does anyone know any workaround? 

My intention is to install and then remove several of the packages such as Libreoffice to hopefully have a working setup.

Many thanks!

---

