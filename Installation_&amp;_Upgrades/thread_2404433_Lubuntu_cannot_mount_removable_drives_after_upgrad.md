---
title: "Lubuntu: cannot mount removable drives after upgrade from 18.04 to 18.10"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by cricalixwood on 2018-10-24
I 
Just upgraded from Lubuntu 18.04 to 18.10

When I try to mount ant removable USB-connected drive I get:

rhill@lime4:/etc$ sudo mount -a
ntfs-3g-mount: mount failed: Bad address

I get this with an drive that auto-mounted perfectly happily before the upgrade, and with a brand-new USB memory stick.

What might be the cause/fix please?

Roger

---

### Post by cricalixwood on 2018-10-24
Found it. Uninstalled Sophos anti virus and all sorts of problems including this one went away.

---

