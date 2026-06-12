---
title: "ubuntu 8.04 64bit desktop not finding SATA 750gb hdd"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by Kyosys on 2008-09-06
So I just got my new PC set up, partitionated my new 750GB HDD under windows to give it 10 GB, installed and ran windows fine, but then when trying to install ubuntu afterwards, it didn't show my HDD in the partition manager during the installation. In fact, it showed absolutely nothing (because there is nothing else)

It's a 750GB samsung SATA2 HD753LJ on a Asus M3N78-EMH mainboard.

Help is appreciated.

---

### Post by arch0njw on 2008-09-07
Do you have AHCI enabled in your BIOS?  I just had this problem after a kernel updates; turning it on "magically" solved the problem.

---

