---
title: "How to uninstall WINE"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by gbrito on 2008-05-23
Hi, I'm new to UBUNTU, I have installed Ubuntu 8.04 and install the Wine package on it, but the MS Visio doesn't work and I need to uninstall the wine package...

I try to uninstall it using dpkg command using the following command:

dpkg -r 1.0~rc1~winehq0~ubuntu~8.04-1

Ubuntu response with the following message...

dpkg - warning: ignoring request to remove 1.0~rc1~winehq0~ubuntu~8.04-1 which isn't installed.

I will appreciate your help..

Best Regards...

Gerardo Brito

---

### Post by wolfen69 on 2008-05-23
the easy way would be to just go to system>admin>synaptic package manager, search for wine, and completely remove.

---

### Post by strick242 on 2008-05-23
in terminal, type:
sudo apt-get remove wine

---

