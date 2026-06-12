---
title: "Problems booting into 16.04 after dual boot"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by eric127 on 2016-06-02
I am dual booting Windows 10 and 16.04 on my dell xps. My windows side boots properly every time. Sometimes the ubuntu side will boot perfectly fine but occasionally when I attempt to boot it gives me just a black screen with output that states "Error parsing PCC subspaces from PCCT". Does anyone know what this means?

---

### Post by oldfred on 2016-06-02
This was a Lenovo, and the suggestion was to update UEFI/BIOS.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528684)

Do you have latest UEFI from Dell?

 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Dell with Ubuntu 14.04 pre-installed & question on special drivers (Sputnik)
[http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops](http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

### Post by eric127 on 2016-06-03
It cant boot in UEFI mode. It is in legacy boot mode.

---

### Post by oldfred on 2016-06-03
Generally better to install Ubuntu in same boot mode as Windows.
UEFI and BIOS/Legacy/CSM are not compatible. 
Once you start booting in one mode, you cannot switch or from grub menu can only dual boot systems in same boot mode.

Several other threads on similar Dells.
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Dell with Ubuntu 14.04 pre-installed & question on special drivers (Sputnik)
[http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops](http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

