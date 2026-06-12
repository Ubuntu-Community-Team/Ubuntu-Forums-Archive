---
title: "unable to start xserver"
date: 2005-02-12
forum: Installation &amp; Upgrades
---

### Post by neurol23 on 2005-02-12
i tried several times to install ubuntu warty, but it always ends in the moment, when it tries to start xserver.
i don't understand, what is the problem, since ubuntu live works without problems

---

### Post by mataz on 2005-02-12
I have the same problem.
My laptop is an Asus l5 AMD64 , geforcefx + nforce.

---

### Post by drasko on 2005-02-13
Configuration of X is not always an easy job... Look in the /var/log/Xlog to see whay it broke... this will give you a hint where to search. Also, try to boot from the live cd and  examine /etc/X11/XF86Config-4 configuration file (maybe you can even copy it to hard disk where ubuntu is installed, replacing the appropriate config file)...

Drasko

---

