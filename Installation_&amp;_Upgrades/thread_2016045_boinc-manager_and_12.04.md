---
title: "boinc-manager and 12.04"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by gilesaj on 2012-07-04
I upgraded my 64 bit Ubuntu from 11.10 to 12.04 today.  I installed boinc-manger from apt-get and attached to a project.  I downloaded some work and had an error as it needed some ia32-libs.  I tried to load the libraries sudo apt-get install ia32-libs libstdc++6 libstdc++5 freeglut3 but it stopped on ia32-libs with a message that ia32-libs is not available.

I am fairly new to linux how do I get those libraries so I can process work in BOINC ??

Cheers

If this is too hard I can uninstall and go back to 11.10 but that is just putting off the ineviatable as there are many projects in BOINC that only have 32 bit applications, but they run in 64 bit BOINC with the libraries.

---

### Post by QIII on 2012-07-04
Try to install ia32-libs on its own and post back what you get in the terminal.

---

### Post by oldos2er on 2012-07-04
Try installing **ia32-libs-multiarch**

---

