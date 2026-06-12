---
title: "AMDGPU-PRO-PIN Error mesage"
date: 2021-07-22
forum: Installation &amp; Upgrades
---

### Post by maravingian on 2021-07-22
Hi All,

I recently installed my replacement graphic card - AMD RX580. Driver successfully installed using AMD GPU PRO. MESA Drivers updated ok, WINE updated ok.

I did notice trhe following message this morning though when i updated Ubuntu; 

+The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libffi7 libffi7:i386 libomxil-bellagio-bin
  libomxil-bellagio0 libva2:i386 libvdpau1:i386 mesa-vdpau-drivers:i386
  vdpau-driver-all:i386
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up amdgpu-pro-pin (21.20-1271047) ...
ERROR: This package can only be installed on Ubuntu 20.04.
dpkg: error processing package amdgpu-pro-pin (--configure):
 installed amdgpu-pro-pin package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 amdgpu-pro-pin
E: Sub-process /usr/bin/dpkg returned an error code (1)


ERROR: This package can only be installed on Ubuntu 20.04 - does anyone know if this package has now been updated for 21.04 yet?

---

### Post by maravingian on 2021-07-25
bump

---

### Post by mikewhatever on 2021-07-25
[Amdgpu-pro version 21.20]("https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-580") is not available for Ubuntu 21.04. The driver is proprietary, so if and when AMD decides to update, they'll post an announcement. For now, your best bet to get that driver seems to be 20.04.2

---

### Post by maravingian on 2021-07-28
Thanks Mike. I`ll keep an eye out :)

---

