---
title: "Installing on NVidia RAID with Striping"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by drheeder on 2005-08-05
I am trying to install Ubuntu on my desktop, which is an AMD 64 bit with an ASUS K8N-E motherboard, with nforce3. My two harddrives are RAID Striped. The problem is when installing, Ubuntu sees them as two seperate drives as apposed to one, since I don't think it has installed any raid drivers before. So, since I can't recompile my kernel (this is a fresh install), how can I install Ubuntu on this machine. I didn't see any raid drivers for nvidia nforce in the startup options.

Dirk

---

### Post by kosmic on 2005-08-05
[QUOTE=drheeder]I am trying to install Ubuntu on my desktop, which is an AMD 64 bit with an ASUS K8N-E motherboard, with nforce3. My two harddrives are RAID Striped. The problem is when installing, Ubuntu sees them as two seperate drives as apposed to one, since I don't think it has installed any raid drivers before. So, since I can't recompile my kernel (this is a fresh install), how can I install Ubuntu on this machine. I didn't see any raid drivers for nvidia nforce in the startup options.

Dirk[/QUOTE]

IT is not possible to install to RAID devices with Hoary, only if the RAID device is a hardware RAID, if you RAID devices Needs drivers them you can't install to RAID...Solution wait for Breezy or install normaly in one of the discs and then convert them to RAID :)

---

