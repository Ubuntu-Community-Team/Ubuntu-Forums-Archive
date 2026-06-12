---
title: "Kernel 2.6.27-*-generic"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lanage on 2008-10-12
After I upgraded to any of the 2.6.27 generic kernels, I would experience a problem right after boot. I am using an encrypted disk. I put in the password and then it says:
```
Loading, please wait...
Command failed: No key available with this passphrase.

key slot 0 unlocked.
COmmand successful.
mount: mounting /root/dev on /dev/.static/dev failed: Input/output error
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox...
```

Previously, if I boot from the last good kernel (I'm not sure which version that was) it works. I've been searching for a while, but I can't find a solution. Any help is appreciated...

---

