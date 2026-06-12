---
title: "installing ubuntu 11.04 on external hdd"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by devj1988 on 2011-09-12
Hi,

I just bought a transcend 1 TB external usb hdd and want to install ubuntu 11.04 on it.

The problem is that I am using my office laptop which does not have a CD drive. Using "universal USB installer", I can copy the iso to the hdd but after booting, I am not sure whether installing it will affect the internal hdd in the laptop. Since its my office lappy, I do not want the internal hdd to be affected in any way whatsoever. What precautions should I follow in order to install it successfully ?

Regards,
Dev Jyoti

---

### Post by 2F4U on 2011-09-12
I would stay away from the automatic partitioning options and do a manual partitioning (I guess it is called "Something else" in the installer). Be careful to choose the right hard disk and don't install the boot loader to the MBR of your internal hard disk.

---

