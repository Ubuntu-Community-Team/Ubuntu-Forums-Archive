---
title: "Cannot install Toshiba Satellite L755-S5368"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by yakimabelle on 2012-02-04
Has anyone been able to install Onieric Ocelot or any Ubuntu release on a Toshiba Satellite L755-S5368?
 
Trying to install from CD leads nowhere; although the BIOS is configured to boot from the ODD, the CD spins and then Windows 7 boots from hard drive - the Ubuntu distro on the CD never seems to display or run? This is a 64 bit system - so I tried the 64 bit OS download.
 
Wubi doesn't work either; lots of error messages in the log.
 
Please help; save me from the heartbreak of running Windows.

---

### Post by mastergkage on 2012-02-05
Hi try to install using a live usb, because when i try to burn the iso image in a cd both 32 and 64 bit its not working properly, I have also encounter this problem. It took me 3 days to solve but with the help of the community. please refer to these [http://ubuntuforums.org/showthread.php?t=1915564](http://ubuntuforums.org/showthread.php?t=1915564), same installation and also we have the same laptop model that i have encounter the problem.

---

### Post by yakimabelle on 2012-02-07
Not the same problem. I can boot and install the 32 bit version; but with the 64 bit version it never seems to load. Maybe a boot loader issue?

---

### Post by yakimabelle on 2012-02-11
Solution found.

CD installation worked for 32 bit, not for 64 bit version of 11.10.

Found and installed a firmware update.

Burned another 64 bit CD; that didn't work.

Made a 64 bit USB install; that worked.

---

