---
title: "problems using pci card"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by yugotpinky on 2006-09-27
i've set up edubuntu and it works fine except...

i have an all-in-wonder rage pro card in a pci slot. i also have an onboard graphics card Intel 82815.

Issue is this: Linux runs fine on the onboard - although there's a bit of visual noise - but that may be monitor/card related. When I boot up using the PCI card as primary in the BIOS, Linux boots using the graphical interface until the login screen should appear. At that point, screen goes black.

Any thoughts?

---

### Post by meng on 2006-09-27
"Goes black"? Is there a prompt? If there is, type:
sudo dpkg-reconfigure xserver-xorg
and choose ati driver for graphics (and you can probably hit enter for the default on all other options).

DO NOT DOUBLE POST!

---

