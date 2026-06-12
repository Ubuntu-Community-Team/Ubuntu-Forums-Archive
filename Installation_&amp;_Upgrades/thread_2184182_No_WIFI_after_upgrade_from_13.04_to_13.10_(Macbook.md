---
title: "No WIFI after upgrade from 13.04 to 13.10 (Macbook pro 8,1)"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by mitchmccray23 on 2013-10-28
After upgrading my Macbook Pro 8,1 from Ubuntu 13.04 to 13.10, I have lost networking capabilities via wifi.  The old connections are saved but i seems there is no wifi option at all.  It reminds me missing drivers. Any help is appreciated.

---

### Post by Zanella on 2013-11-21
This fixed it for me: [http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/)

Running this "sudo dmidecode -s system-product-name" gave me "MacBookPro8,1", hope it helps ;-)

---

