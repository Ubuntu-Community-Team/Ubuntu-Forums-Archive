---
title: "ATI graphics drivers uninstall"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by StubbDan on 2008-05-15
I just followed the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0")

And I got the errors with "MESA" in, but don't have time to fix it currently.  I was hoping that someone could tell me how to undo what that did and get it back to the default graphics driver - at least compizfusion worked with that.  I was going to set the xorg.conf to its default but I wasn't sure if that would work.

---

### Post by StubbDan on 2008-05-15
I just noticed that I have:

fglrx-kernel-source
Kernel module source for the ATI graphics accelerators

and

xorg-driver-fglrx-dev
Video driver for the ATI graphics accelerators (devel files)

under "installed (local or obsolete)" in synaptic package manager, so I'm guessing that just the aticonfig needs to be undone, and defaulting xorg.conf would do that right?

---

