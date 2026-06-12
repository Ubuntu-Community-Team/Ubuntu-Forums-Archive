---
title: "Philips Freevents X59 &amp; Linux/Unix"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by gian748 on 2010-01-11
Dear all

I hope that the follonwing info&#8217;s cold be usefull for the Philips Freevents owners that need to start linux/Unix systems.

I have a Laptop Philips Freeevents X59, core 2 duo, 1G ram, 100 G HD. 

I needed linux for work reasons.

I became mad because there is NO linux distro that fit this computer except one as we will see.

SUSE: if we browse in the linux forums we can find some peoples that have installed suse10.3. Maybe it has been possible on some previous version of this Philips freevents. On X59 there is NO suse version that does not freeze during installation. The main problem is that they do NOT recognize the the Ethernet Realtek 9138 and the driver in the suse distro simply do not fit.

Ubuntu: there is just one version on the et that has been modified to fit this kind of laptop , at least Freevents X52 or previous versions. This version can be found at : [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm).
The installation goes fine but the computer is slow and a lots of applications do not work properly. But the main problem si the following: when the PC is powered on without internet connection it simply freezes!!!!! To avoid this you have to swich off any web connection before powering off the laptop.

Scientific Linux: it recognizes the Ethernet card but the distro do not like the SATA hard disk and thus it simply refuses to see it and consequently the installation simply freezes.

There is only one distro that goes fine with this kind of laptop:

FreeBDE:

[http://www.freebsd.org/it/](http://www.freebsd.org/it/)
.

There are two interesting BSD-based distros that include the automatic starts of a KDE performing desktop: 

[http://www.desktopbsd.net/index.php](http://www.desktopbsd.net/index.php)

or 

[http://www.pcbsd.org/](http://www.pcbsd.org/).


 the difference between Linux and BSD is the following:

&#8594; [http://en.wikipedia.org/wiki/FreeBSD](http://en.wikipedia.org/wiki/FreeBSD)

&#8594; [http://www.freebsd.org/doc/en/articles/explaining-bsd/comparing-bsd-and-linux.html](http://www.freebsd.org/doc/en/articles/explaining-bsd/comparing-bsd-and-linux.html)
.

FreeBSD installation on Philips Freevents is simply and goes fine without any efforts. The ethernet card and the HD are seen without any problems.The ACPI is well supported and works fine. Wine software runs very well (it is very stable) and a lots of windows applications can be easily installed.

Bye bye

:popcorn:

---

