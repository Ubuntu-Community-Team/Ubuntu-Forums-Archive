---
title: "Patching kernel"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by k_i_d on 2009-11-30
Can somebody explain how patching should be done.
Fast step-by-step tutorial would be helpfull for a lot of us.

I just install Ubuntu after a long break with Linux. My last distro was Slackware :] But to the point. I need to patch kernel to use mesh point WiFi. But using a comand:
```
bzcat ../patch-2.6.31.6.bz2| patch -p1
```gives me respond:
```
File to patch:
```with every file to be patched. I don't think that is normal - so looking for help from you.

---

### Post by albandy on 2009-11-30
from what directory are you appliying the patch?

---

### Post by k_i_d on 2009-12-02
patch_file is in /usr/src. But the command is execute from /usr/src/linux-headers2.6.31-15-generic.

---

### Post by albandy on 2009-12-03
try p0 instead of p1

---

