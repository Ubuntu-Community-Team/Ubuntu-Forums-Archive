---
title: "Wireless problems with 8.04LTS"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by bobbybrown on 2008-05-26
Has anyone had problems with their wireless connection since upgrading to 8.04? I am using a wirless card which has a Broadcom chipset, worked ok under 7.10 after manual configuration, but now won't work after the upgrade.
I have downloaded the driver update and installed using FW Cutter and in the hardware driver program all looks to be installed ok, however it is still not working.

Any ideas?

Thanks

---

### Post by spraveenitpro on 2008-05-26
**Try the following commands**


wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

sudo apt-get install build-essential


tar xfz madwifi-ng-r2756+ar5007.tar.gz


cd madwifi-ng-r2756+ar5007

sudo modprobe ath_pci

make



sudo make install


sudo modprobe ath_pci


sudo reboot

---

