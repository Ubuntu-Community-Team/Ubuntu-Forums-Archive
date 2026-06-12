---
title: "pxelinux.cfg file is blank? 0 kB?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2011-04-28
why is the natty 1104 alternative pxelinux.cfg is blank? 0 kB?

when I deploy natty to my workstation, I get a message that said it cannot locate the configuration file. Then I look at the pxelinux.cfg. It is 0kB. Is this normal?

---

### Post by bbmak on 2011-04-28
> **bbmak said:**
> why is the natty 1104 alternative pxelinux.cfg is blank? 0 kB?

when I deploy natty to my workstation, I get a message that said it cannot locate the configuration file. Then I look at the pxelinux.cfg. It is 0kB. Is this normal?


manually fixed it.
Cant believe that Ubuntu misses it.:confused:

---

### Post by andyh1213 on 2011-05-12
I confirm that it is blank and this causes a problem. The file from 10.10 is blank as well. I copied the default file from 10.04LTS and that worked fine.

---

