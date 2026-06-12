---
title: "Install 10.04 on Toshiba Laptop - Major Problems"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Pudwud on 2010-05-07
I tried to upgrade virtual machine versions of Hardy Heron (8.04) and Karmic Koala (9.10) and install a clean virtual machine version of Lucid Lynx (10.04) on one Toshiba Laptop that I own and ended up with major  problems all three times – won't install/boot.  I also tried to upgrade a Wubi installation of Karmic Koala on another Toshiba Laptop that I own and again had major problems.

I have been using Ubuntu since Breezy Badger (5.10) and have never encountered problems like this.

Is there some kind of incompatibility between the Toshiba architecture and Lucid Lynx?

Thanks.

---

### Post by jediknightbrodie on 2010-05-21
I've been having the same problems on my Toshiba A355 laptop, I can't install any distro of Ubuntu. I always get a CPU hang. Does anyone know a fix for this??

---

### Post by rodrigonull on 2010-05-21
Use this parameter on boot: pci=use_crs

:)

---

### Post by afab on 2010-06-22
> **rodrigonull said:**
> Use this parameter on boot: pci=use_crs

:)
This helped to install but another problem, no graphic shell loaded. It is loading just command line and asking login/password. After enetering l/p command line only and nothing going on. I tried to run gnome but it appears some kind of basic shell - no connection to internet, not possible to update, nothing. How to run full version of ubuntu after entering l/p.

---

### Post by Mark Phelps on 2010-06-22
> **afab said:**
> This helped to install but another problem, no graphic shell loaded. It is loading just command line and asking login/password. After enetering l/p command line only and nothing going on. I tried to run gnome but it appears some kind of basic shell - no connection to internet, not possible to update, nothing. How to run full version of ubuntu after entering l/p.

This thread is about installation problems, not display problems.  Please don't hijack this thread with a fundamentally different problem.

Please start your own thread regarding the display problem.

---

