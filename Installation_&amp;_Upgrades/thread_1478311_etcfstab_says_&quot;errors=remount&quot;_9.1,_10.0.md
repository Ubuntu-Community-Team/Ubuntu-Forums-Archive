---
title: "/etc/fstab says &quot;errors=remount&quot; 9.1, 10.04"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by krt on 2010-05-09
In two installations of Ubuntu 9.1 and one of 10.04 (3 different computers), when I look at /etc/fstab, all three have a statement that indicates "errors=remount" for the root partition (I have separate root and home partitions).

I don't see any particular problems with system operation, but how does one fix the errors? Running fsck -n (so it will only list errors and not mess up system) shows several errors.

All three systems are dual boot with Windows XP previously installed.

I have checked the fstab deal right after one of the n'th boot file checks, and it still indicates the "errors=remount" deal (not errors=remount-ro).

Thank you,

krt

---

