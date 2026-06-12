---
title: "Ubuntu 8.04 Installation FAILED: Error message that CPU needs features."
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by network_engineer on 2008-06-21
Hi all,

I am trying to install the Ubuntu 8.04 Server version to a Dell D400 Laptop, running Intel Centrino 1.4 Ghz processor.

The installation process itself *seems* to go fine; takes about 20 minutes; however, when the laptop reboots, I get the following error:

[COLOR="Blue"]Starting up...
This kernel requires the following features not present on the CPU:
0:6[/COLOR]
[COLOR="Blue"]
Unable to boot - please use a kernel appropriate for your CPU.[/COLOR]

I would really appreciate some help on this. :confused:

Thanks a lot.

Kind regards.

---

### Post by Kevbert on 2008-06-21
Please have a look at [this]("http://bugs.gentoo.org/show_bug.cgi?id=220058").  It looks like it's a memory support problem in the Linux kernel and so is not Ubuntu specific.

---

