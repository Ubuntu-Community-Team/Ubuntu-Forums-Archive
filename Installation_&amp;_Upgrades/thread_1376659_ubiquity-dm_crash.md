---
title: "ubiquity-dm crash"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by tn812 on 2010-01-09
Hi, at LiveCD installation start, I run into an "ubiquity-dm crashed with XStartupError in run()".  

I wonder if this is a serious crash?  I'm reinstalling ubuntu because of startup issues.  Should I go on with the installation?

---

### Post by k64 on 2010-01-09
> **tn812 said:**
> Hi, at LiveCD installation start, I run into an "ubiquity-dm crashed with XStartupError in run()".  

I wonder if this is a serious crash?  I'm reinstalling ubuntu because of startup issues.  Should I go on with the installation?

Ubiquity crashes are very serious, because Ubiquity is the Ubuntu installer! And ubiquity-dm is the desktop icon for the install. And XStartupError is an error within X.org that probably is triggering the Ubiquity crash.

By any luck, you probably have a faulty LiveCD. Try running the install by rebooting and see if that helps. If not, then you have to [burn the CD again]("http://mirrors.kernel.org/ubuntu-releases/9.10/ubuntu-9.10-desktop-i386.iso").

---

