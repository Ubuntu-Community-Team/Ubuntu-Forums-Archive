---
title: "Quick question about checking version."
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by PickleSuit on 2011-04-29
I specifically installed Ubuntu 10.10 64 bit to have it recognize more than 3-4 GB of ram and I upgraded to 11.04, it should have upgraded to the 64 bit version correct? Is there a way I can check to make sure?

---

### Post by Tank Jr on 2011-04-29
It should upgrade to the same architecture version.
Try ```
uname -a
```
at the terminal. If the version is a 64 bit ubuntu, it should come up with x86_64 or something similar.

---

### Post by PickleSuit on 2011-04-29
Thanks. That was what I was looking for.

---

