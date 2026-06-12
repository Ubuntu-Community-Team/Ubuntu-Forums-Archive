---
title: "how blacklist nvidia version 185"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by mrcool18t on 2009-11-14
I have a motherboard with GeForce 7050.
It work fine with nvidia accelerated graphics driver version 173 not 185.
During automatic update the driver got upgraded to 185 and was not able get GUI, hence has to reinstall every thing.
How do blacklist the version 185(example/code please), more how can I tell ubuntu to stick to this 173 version and not download any updates for this hardware..

Ubuntu version: 9.10
Thanks in advance.

---

### Post by falconindy on 2009-11-14
The proper way to pin a package is:
```
echo "<package> hold" | sudo dpkg --set-selections
```

Guess that means you'll need to run it for each of:
nvidia-173-modaliases
nvidia-173-kernel-source
nvidia-glx-173

---

### Post by mrcool18t on 2009-11-14
How do i know which package is it, because in hardware driver it shows just the name.

---

