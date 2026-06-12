---
title: "how to install graphic driver on ubuntu 16.04 lts"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by mumax10 on 2017-02-09
hi,I have a video card of radeon hd 7750 can i install the driver card on ubuntu 16.04 lts? if i cant whitch ubuntu will allow me and if i can how??

---

### Post by QIII on 2017-02-09
Due to some dramatic changes in the landscape of AMD drivers, the older fglrx driver cannot be installed in 16.04.

The Ubuntu installer will determine if the open source Radeon driver or the new open source AMDGPU driver can be installed.  For your GPU, the Radeon driver will be used.

Your GPU is currently incompatible with the AMDGPU driver (although it may be supported later), so you cannot force the installation of AMDGPU or AMDGPU-PRO.

The last supported release of Ubuntu for which you can use fglrx is 14.04.1 or earlier.

---

### Post by mumax10 on 2017-02-09
ok ty it's matter if its lts or not?

---

