---
title: "Difference between (Ubuntu server + lubuntu-desktop) vs direct lubuntu"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2016-04-27
Hello,

The hardware I am going to use is very fast and has 32G RAM. This is a developer box I am building.

Looks like I can install lubuntu in two different ways.

1. Download lubuntu image and install it directly.

Or

2. Install "Ubuntu server only" image and "apt-get install lubuntu-desktop"

Is the first option more performance-efficient than the second one given that the kernel, etc. is the same? If so, what makes it more efficient? Is it not running some daemons that are part of standard Ubuntu server install?

Thank you in advance for enlightening me.

Regards,
Peter

---

### Post by deadflowr on 2016-04-27
Installing a desktop is always more efficient from the desktop's iso.
From a server iso, you have to download a fairly large iso, and then still download even more while installing from that server iso to get the desktop packages.
Installing from the desktop iso is straight forward. No need to download more, as it is already there.
The benefit of installing from a server iso has little to do with performance, and more to do with the fact that you can install as many packages as you want, and they will all be there on first boot.
Desktop iso's only install what the installer has, and nothing more.

Does that make any sense?

---

### Post by PeterTaps on 2016-04-28
Thank you for your help. What I wanted to understand was if there is any difference in CPU/memory consumption after the install. In other words, is the non-UI core of lubuntu core is leaner on resources compared to ubuntu server?

Regards,
Peter

---

### Post by grahammechanical on 2016-04-28
If you want the "leanest" Linux then only install Linux.

The server edition is a command line OS but it includes applications suitable for server administration. The moment we start an application running it will use system resources on top of those already used by the OS. How much system resources are used will depend upon the application. Those applications that do not have a graphical user interface (GUI) will use less system resources than those applications that do have a GUI.

Actually, there is a difference between Ubuntu/Lubuntu server and Lubuntu core. Furthermore, Lubuntu core is basically Ubuntu core. You will find that Xubuntu core & Lubuntu core ISO images are actually the Ubuntu mini ISO image. They all will install Linux but give options to install the various desktop environments from the bare minimal environment with nothing much more than a virtual terminal application & some system utilities to the more usual desktop environment & applications that are associated with the flavour.

Regards.

---

