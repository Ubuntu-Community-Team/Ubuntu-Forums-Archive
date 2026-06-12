---
title: "Ubuntu 13.04 installation problem via PXE: installer can't find live image."
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by hanhwi on 2013-08-04
Hi, 

I'm trying to setup PXE boot server for automatic ubuntu installation across several machines. I followed this tutorial([https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)); I shared contents of ubuntu 13.04 server image with other machines via HTTP. Clients could load boot loader from the server and execute installer, but installation stopped after partitioning phase due to missing live image. Thus I tried changing ubuntu image location from my own directory containing ubuntu iso contents to ubuntu official archive, and that worked. 

Why could the installer find live image when ubuntu archive was used? Is there any difference between ubuntu image and ubuntu archive?

Using ubuntu archive works for install ubuntu via network, but I want to make my own OS image pool on my PXE boot server for installation. Is there any method to do that?

Thanks

---

