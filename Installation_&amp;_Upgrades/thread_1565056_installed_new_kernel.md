---
title: "installed new kernel"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by dasgenie on 2010-08-31
installed new kernel but no option found to boot from older kernel at startup .

---

### Post by andrewthomas on 2010-08-31
You could edit /etc/default grub so GRUB_HIDDEN_TIMEOUT=0 is commented

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

---

### Post by dasgenie on 2010-08-31
it worked ......... thanks :)

---

