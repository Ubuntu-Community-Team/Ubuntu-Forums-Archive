---
title: "Trouble running XP guest in virtualbox"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by whiffy badger on 2008-08-25
I'm trying to get XP to run as a guest in virtualbox with hardy heron as the host.  When I attempt to start XP I get this error message:

[HTML]
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/HTML]

 I'm currently using the 2.6.24-19-generic kernel and I'm a noob so any help would be appreciated! :)

---

### Post by de0xyrib0se on 2008-08-25
Download VirtualBox from the Sun website, its a .deb self installer no need to do anything custom and it would solve your problem. Also make sure you uninstall the repo version you have installed right now.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

