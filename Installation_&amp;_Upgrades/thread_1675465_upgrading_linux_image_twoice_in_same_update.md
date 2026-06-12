---
title: "upgrading linux image twoice in same update"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by abdulrehman.ansari on 2011-01-25
hi,
i have installed Ubuntu desktop 10.04.1 just few hours back, and now when i am updating my OS, i have notice that Ubuntu download linux-image-2.6.32-24-generic first (31.5MB) and then immediately after that it is downloading linux-image-2.6.32-27-generic (31.7MB).
why it require two linux images? if linux 2.6.32-27 is latest one, then why linux 2.6.32-24 is downloaded, it could saved internet bandwidth and installation time.

thanks in advance.

---

### Post by wilee-nilee on 2011-01-25
> **abdulrehman.ansari said:**
> hi,
i have installed Ubuntu desktop 10.04.1 just few hours back, and now when i am updating my OS, i have notice that Ubuntu download linux-image-2.6.32-24-generic first (31.5MB) and then immediately after that it is downloading linux-image-2.6.32-27-generic (31.7MB).
why it require two linux images? if linux 2.6.32-27 is latest one, then why linux 2.6.32-24 is downloaded, it could saved internet bandwidth and installation time.

thanks in advance.

There are parts of the -24 kernel that are needed to install the -27, probably or at the least a generic portion.

---

