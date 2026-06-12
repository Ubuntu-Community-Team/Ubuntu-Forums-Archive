---
title: "Ubuntu server 9.10 - no modules installed with PAE kernel by  default (VM setup)"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by kenga on 2009-11-18
Hi,

Got a problem with default 9.10 server install - no isofs module is installed by default in generic VM setup variant. This leads to inability to mount cdrom - mount attempt failing with "iso9660 - unknown filesystem type" error. 

So the one who want to mount cdrom, should install the linux-backports-modules-2.6.31-14-generic-pae package first.

It's very strange variant of default system layout to be considired as an feature.

---

