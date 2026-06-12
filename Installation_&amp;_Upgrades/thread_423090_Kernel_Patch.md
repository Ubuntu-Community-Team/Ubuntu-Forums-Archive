---
title: "Kernel Patch"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by OOzypal on 2007-04-25
I am trying to patch my wireless card driver and follows the instructions which is as

```
$make patch_kernel
```

I then got this error. What does it mean?

```
WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Kernel Makefile not found at '/lib/modules/2.6.20-15-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1
```

---

### Post by OOzypal on 2007-04-25
Dears 
I got passed this point. Now, I get this error

```
$  sudo make patch_kernel 
Checking kernel compatibility in:
        /lib/modules/2.6.20-15-generic/source//
 * Kernel requires compatibility version:
   - Requires class_dev -> dev API compat
   - Requires to_net_dev API compat
   - Requires device_rename compat
compatible/ already exists. You must remove it before continuing.
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

```

---

