---
title: "Custom Ubuntu Install"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by kmac on 2010-10-06
I am looking for a way to "snapshot" my current installation (with predetermined desktop shortcuts, theme, installed packages, etc.) to install onto clients' computers that bears a resemblance to the company I work for. This snapshot would be compiled into an iso to be loaded onto machines.

Suggestions?

---

### Post by Jahid65 on 2010-10-06
If you want full copy of your current installation you can use remastersys(applicable for 9.10 & 10.04). This tool helps you to copy your whole system & make it a bootable Iso. Download this [http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download](http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/remastersys_2.0.17-1_all.deb/download) deb package & install it. Then open a terminal and type:
```
sudo remastersys dist
```

This will make an ISO without your home folder. If you want to add your home folder then type this:
```
sudo remastersys backup
```
This will take about 20-25 minutes. You can find the ISO in File System> Remastersys folder.

**Caution: You should install ubiquity package because it handles the installer option. **

---

