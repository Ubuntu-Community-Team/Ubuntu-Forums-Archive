---
title: "Ubuntu server netinstall on UCS Cisco"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by Quadchris on 2011-02-02
Hy all,

I'm using in our company the UCS Cisco blades systems. These servers had the M81KR card which used the enic driver. This driver is included into the normal kernel in 10.04 and 10.10 but it is not included into the ubuntu-installer.

After digging into the initrd.gz file on netboot the driver is not included but it is included into the initrd provided by squeeze debian-installer.

Why this driver is not present and is there a roadmap or a plan for having it into the initrd of ubuntu-installer ?

Thanks by advance for your reply.

---

