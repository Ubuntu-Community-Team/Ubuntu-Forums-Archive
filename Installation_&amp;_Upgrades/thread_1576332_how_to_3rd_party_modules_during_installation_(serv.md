---
title: "how to 3rd party modules during installation (server)"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by ojconcentrate on 2010-09-17
Hello all,

i've been playing with some intel server board and they provide a type of fakeraid which is called Embedded Server Raid Technology 2. Since intel officially support RHEL and SLES on their servers, they provide drivers/modules for this fake raid (which supports raid 0, 1, 5 and 10). I have installed RHEL before on these severs and redhat's installer has the ability to load additional modules (via a boot command linux dd).

While intel doesn't provide the modules for other operating systems, they provide a library where people can build their own module for their kernel.

I managed to build this module called 'megasr' (for now i've built it for kernel 2.6.32-24-generic which is my testbed at the moment but i would eventually build it for box i386 and amd64 for both server and desktop versions) and load it on a system which is installed on a single drive and was able to load it successfully and see the raid 5 as a single volume and access it (partition, format and copy data to it) and all its funcions (work in degraded mode, rebuild, etc) work fine but my main goal is to actually install such volume as my main boot volume (similar to how its possible with RHEL or SLES).

Is this possible? load additional modules during the installation that will be present after the installation is finished?

many thanks

---

### Post by ojconcentrate on 2010-09-18
anyone?

any suggestion is much appreciated

---

