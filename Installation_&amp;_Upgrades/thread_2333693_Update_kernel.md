---
title: "Update kernel"
date: 2016-08-12
forum: Installation &amp; Upgrades
---

### Post by Seth-666 on 2016-08-12
**NooB question**

Ubuntu 14.04.05 LTS 

If i update the kernel 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:07:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux - 

to 
```
The following NEW packages will be installed:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
The following packages will be upgraded:
  linux-generic-lts-xenial linux-headers-generic-lts-xenial
  linux-image-generic-lts-xenial

```

The last kernel will transform my OS 14 to the last 16 right?

---

### Post by howefield on 2016-08-12
Are you asking if upgrading only the kernel, will that take you from the last LTS release 14.04.5 to the current 16.04.1 - then no, it won't. You will be running 14.04.5 with the xenial kernel.

If you mean something else, could you clarify ?

---

### Post by Seth-666 on 2016-08-12
you understand what i wanted to say, one more thing, and if i do this update is possible to have problems with some old apps right ?

---

### Post by howefield on 2016-08-12
> **Seth-666 said:**
> you understand what i wanted to say, one more thing, and if i do this update is possible to have problems with some old apps right ?

The packages listed above are unlikely to cause you issues with other "old apps" whatever they might be, but if they do then you can boot into the previously working kernel, ie, 4.4.0-31-generic.

---

