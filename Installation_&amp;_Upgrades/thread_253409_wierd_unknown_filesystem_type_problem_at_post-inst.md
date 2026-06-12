---
title: "wierd unknown filesystem type problem at post-install"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by superprad on 2006-09-08
Hi:
I successfully installed ubuntu on my laptop. Butthis is what it shows on the partition table:

partioion filesystem size used unused flags
/dev/hda1 ext3 101.35MB 44.97MB 56.98MB boot
/dev/hda2 unknown 74.43GB --- --- lvm

The hda2 filesystem says unknown type and does'nt show used/unused spaces. Also this would be a problem if I want to resize the partition later as 
when I open gparted and right click on the hda2 it only gives me either delete or format options and no resize as it thinks this is some errorneous partition...

how do I fix this filesystem type from "unknown" to a valid type such as "ext3" or something. I dont want o reinstall the whole thing again.

---

