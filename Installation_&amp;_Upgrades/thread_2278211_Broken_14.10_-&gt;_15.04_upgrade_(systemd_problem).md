---
title: "Broken 14.10 -&gt; 15.04 upgrade (systemd problem?)"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by edantes2 on 2015-05-14
I tried to upgrade a 14.10 intallation to 15.04 using the official Ubuntu software update.  After reboot, selected default Ubuntu from the grub menu, system boots immediately to "emergency mode".  The error message is

[FAILED] Failed to start Load/Save Random Seed
See "systemctl status systemd-random-seed.service" for details

Short of reinstalling  15.04 from scratch, is there an easy fix in the configs?

Merci d'avance!

---

### Post by ian-weisser on 2015-05-16
Please show us the complete output of the following command:
```
systemctl status systemd-random-seed.service
```

---

