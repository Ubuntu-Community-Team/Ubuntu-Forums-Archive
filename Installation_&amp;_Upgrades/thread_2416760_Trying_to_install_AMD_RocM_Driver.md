---
title: "Trying to install AMD RocM Driver"
date: 2019-04-15
forum: Installation &amp; Upgrades
---

### Post by bobrow2006 on 2019-04-15
On my Laptop I am trying to experiment with Blender so as my Laptop has an APU I decided to try and use it in blender rendering (on cycles) but I ran into a problem it didn't show up under OpenCL. I did some research and found Blender isn't compatible with OpenCL 1.1 (provided by mesa from [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu)) so I then decided to try install the RocM Driver. Anyway every time I try to install it (the rock-dkms or the upstream driver) it just after a reboot shows mesa again w/ OpenCL 1.1
I have attached the glxinfo and clinfo output
Specs:
HP Envy 15 ah100na
AMD A10-8700P w/ Radeon R6 Graphics (Carrizo)
8GB RAM
Ubuntu 18.04

[ATTACH]283033[/ATTACH]
[ATTACH]283034[/ATTACH]

---

