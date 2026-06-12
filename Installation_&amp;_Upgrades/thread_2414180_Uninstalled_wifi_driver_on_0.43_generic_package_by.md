---
title: "Uninstalled wifi driver on 0.43 generic package by mistake"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by dnivrav93 on 2019-03-06
I had wifi adaptor issues on my latest Ubuntu 18.04 linux package-4.15.43-generic
I followed up with a few suggestions online and I uninstalled my wifi driver completely.

I'm currently running on package-4.14-33-generic without any issues. Is there anyway I can reboot/fix the wifi driver issues on .43-generic package from .33-generic package?

Thanks.

---

### Post by kc1di on 2019-03-07
Which wireless card and driver are we talking about?

If you reinstall 4.15.43 it should build the correct module for your wireless card if dkms is installed.

---

