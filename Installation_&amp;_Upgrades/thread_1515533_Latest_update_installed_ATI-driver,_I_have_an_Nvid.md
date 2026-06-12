---
title: "Latest update installed ATI-driver, I have an Nvidia card - bug report"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by ÄlveKatt on 2010-06-22
Latest update from the update manager (Ubuntu 10.04) installed an ATI-driver, and I have an Nvidia card. It was very annoying, 3d applications refused to start and sound was only working barely. It wasn't a Kernel update, but upon checking I did find it included an ATI driver. (/var/log/dpkg.log)

So I fixed it all by removing the ATI driver and reinstalling the drivers from Nvidias homepage. But why, oh, why, did the update manager think I needed an ATI driver for my Geforce GTS 250?

---

### Post by davidogg on 2010-07-26
> **ÄlveKatt said:**
> Latest update from the update manager (Ubuntu 10.04) installed an ATI-driver, and I have an Nvidia card. It was very annoying, 3d applications refused to start and sound was only working barely. It wasn't a Kernel update, but upon checking I did find it included an ATI driver. (/var/log/dpkg.log)

So I fixed it all by removing the ATI driver and reinstalling the drivers from Nvidias homepage. But why, oh, why, did the update manager think I needed an ATI driver for my Geforce GTS 250?

wierd. Onboard maybe?

---

