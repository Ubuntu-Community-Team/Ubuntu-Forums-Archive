---
title: "problem getting access after fresh load/configure ubuntu 14.04.1-desktop"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by Richard_Adams on 2015-02-19
I loaded ubuntu14.04.1-desktop using a usb stick configured with Universal-USB-Installer-1.9.5.9. The boot process won't allow me to run off of the usb stick. I configured the system (Dell Dimension 9200) without any apparent problems, go to re-boot, the login prompt comes up - but won't accept a login. I've tried several variations of configure options - to no avail.

It would seem the system is configured - the boot/login screen comes up - but can't access the system beyond the login.

I'm hoping someone may have some ideas.

Thank you!

---

### Post by Richard_Adams on 2015-02-20
I'm not sure exactly what solved this problem, but I downloaded boot-repair-disk-64bit from [http://http://sourceforge.net/projects/boot-repair/](http://http://sourceforge.net/projects/boot-repair/) - then used the universal-USB-Installer-1.9.5.9 to load it onto a USB stick. I followed the instructions from boot-repair home site to repair the boot sector. From there I was able to re-boot ubuntu system off of the disk, complete the configuration from within the workstation screen and everything (generally) seems ok.

---

