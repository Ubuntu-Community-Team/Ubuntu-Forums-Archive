---
title: "Scanner fails after 8.04 upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by datacard on 2008-05-06
I use Ubuntu on a Dell Inspiron 530. My Epson 4180 scanner worked OK with Gutsy Gibbon and Gimp xsane, but doesn't work after an upgrade to Hardy Heron. The diagnostic says can't communicate with scanner.

I tried "sane-find-scanner | grep 0x04b8" and that returned
"found USB scanner vendor 0x04b8
product-0x0118 at libusb:008:003"

Something needs a "chmod 0666", but what?

Does anyone know how to fix the problem?

Thanks,
Cecil
McKinney, Texas

---

