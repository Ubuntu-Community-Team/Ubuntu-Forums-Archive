---
title: "modprobe i2c-piix4 freeze"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by Axel Guerrero on 2006-10-02
Hello all,

I have an ancient 233mmx (an AOpen ap5tc with 430tx chipset) on which I would like to try Ubuntu (I have a cd for 5.04).  Prior to Ubuntu, this machine had RH6.2 kernel 2.2.19.
In both the live cd and the actual install cd, the computer freezes while trying to modprobe i2c-piix4.  I can skip this freeze by chmod -x pci.rc (the boot process will skip it with an error) and manually start the other pci devices (most importantly, eth0).

Is there anything that I can do to fix this problem? Do I actually need this i2c-piix4?  Is Ubuntu too modern of a distro for this equipment?

Mind you, I am aware that both kde and/or gnome would be a little sluggish on such CPU.  I installed the "server" option and plan on using it as a little development mysql/java tomcat server.

---

