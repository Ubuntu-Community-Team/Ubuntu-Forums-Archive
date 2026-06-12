---
title: "usb cd burner"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by mwql on 2005-05-31
Installing external cd burner is a big question mark for me. Ubuntu recognises drive as a cd-rom only, what must be done to install it??

 O:)

---

### Post by thrift on 2005-05-31
What application is mistaking the burner for a cdrom?  If the entire system doesn't understand it's a burner, the problem is most likely with HAL.  If the Nautilus cd burner isn't picking it up, I would submit a bug report.  In the meantime you should be able to manually burn CDs from the command line with cdrecord and mkisofs as you can specify exactly what device to use as your cdburner.

---

