---
title: "upgrade problem"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by jonrog63 on 2008-05-27
I am trying to resolve a problematic upgrade that left me with no desktop I have tried dpkg --configure -a and am told that errors have been encountered in while processing:
linux-image-2.6.24-16-generic
linux-ubuntu-modules-2.6.24-16-generic
linux-image-generic
linux-restricted-modules-generic
linux-generic

this takes me way beyond the manual and I wonder if I should just give up and try to reinstall?

any comments gratefully received

---

### Post by iaculallad on 2008-05-27
> **jonrog63 said:**
> I am trying to resolve a problematic upgrade that left me with no desktop I have tried dpkg --configure -a and am told that errors have been encountered in while processing:
linux-image-2.6.24-16-generic
linux-ubuntu-modules-2.6.24-16-generic
linux-image-generic
linux-restricted-modules-generic
linux-generic

this takes me way beyond the manual and I wonder if I should just give up and try to reinstall?

any comments gratefully received

If you could drop on your terminal, issue this command.

Code:

```
sudo apt-get install util-linux
```

---

