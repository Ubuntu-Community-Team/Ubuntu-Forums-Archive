---
title: "Quick fix for virtualbox-ose module build on 2.6.32 kernel"
date: 2009-11-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SevenMachines on 2009-11-03
The modules fail to build with
error: dereferencing pointer to incomplete type
in r0drv sections for a few modules. 
Fix by adding the include
#include <linux/sched.h>

to,
/usr/src/vboxdrv-3.0.8/r0drv/linux/the-linux-kernel.h
/usr/src/vboxnetadp-3.0.8/r0drv/linux/the-linux-kernel.h
/usr/src/vboxnetflt-3.0.8/r0drv/linux/the-linux-kernel.h

---

### Post by jfernyhough on 2009-11-03
Hmm... the PUEL version compiled fine, though that is version 3.0.10. Wonder if there's a 3.0.10 OSE available?

---

### Post by SevenMachines on 2009-11-03
yep, 3.0.10 has
* Linux hosts: fixed module compilation against Linux 2.6.32rc4 and later 
its just a quick fix for 2.0.8 is the repositories for now until an update

---

