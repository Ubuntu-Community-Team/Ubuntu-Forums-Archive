---
title: "source build directory - where?"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by rogerdean on 2005-06-02
hello folks

i'm trying to install the linuxant modem driver package, and am asked -

[COLOR=DarkOliveGreen]Where is the linux source build directory that matches your running kernel?
[/usr/src/linux][/COLOR]

what should i enter here? it's a standard ubuntu install with no messing

many thanks
roger

---

### Post by thrift on 2005-06-02
you probably need to install the linux headers for your kernel, then they will be in the /usr/src/linux-headers-kernelversion directory.  Check /usr/src/ after installing the headers for your kernel to see exactly what that is.

---

