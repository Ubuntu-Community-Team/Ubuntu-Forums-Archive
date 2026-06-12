---
title: "Display shows as laptop on a desktop -- Now important"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-19
I have been struggling with getting PC with nVidia graphics running after hardware upgrade.  Monitor is ViewSonic 926.  Ubuntu thinks that I have a laptop.  nVidia drivers will NOT load because they are looking for nvidia-prime.  nividia-prime won't load because PC is not a laptop.  How do I tell nVidia that my monitor is NOT a laptop.

I discovered this mess by trying to run nvidia-settings.

John

---

### Post by cigtoxdoc on 2014-07-19
The console output for installation of nVidia drivers is attached.

---

### Post by cigtoxdoc on 2014-07-19
Those who work in labs know that if you do the experiment enough times, you will sometimes get what appears to be the politically correct answer.  

PC is up and running (Ubuntu 12.04 64-bit) with nouveau drivers giving 1280 x 1024 x 24 on the ViewSonic VA926g monitor.  Display applet shows ViewSonic Coporation 19".  Kernel is 3.13.0-32.  I have attached a copy of the xorg.0 log file for those who want to see what I did.

Thank you to all those who provided help.

John

---

