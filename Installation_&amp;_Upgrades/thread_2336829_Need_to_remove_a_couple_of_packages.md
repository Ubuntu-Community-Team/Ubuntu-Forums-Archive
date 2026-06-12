---
title: "Need to remove a couple of packages"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by DrRus on 2016-09-11
I need to remove the following packages:

libidl-2-0:i386 (0.8.14-4)
libidl-2-0:amd64 (0.8.14-4)

What would be the best way to go about it?

Thanks

---

### Post by ian-weisser on 2016-09-11
Try:
```
apt remove libidl-2-0
```

If it fails, please post the complete output here. The error messages, and their context, are very helpful

---

### Post by DrRus on 2016-09-12
Worked like a charm, thanks Ian

---

