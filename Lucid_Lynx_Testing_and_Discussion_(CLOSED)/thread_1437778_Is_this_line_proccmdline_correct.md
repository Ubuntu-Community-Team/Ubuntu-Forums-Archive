---
title: "Is this line: proc/cmdline correct?"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-03-24
rick@rick-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-17-generic root=UUID=1fa6b366-0d18-442c-91cb-506460b1b9ab ro splash quiet splash

##I am wondering about the (ro splash quiet splash) at end of line.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)

Linux rick-laptop 2.6.32-17-generic #26-Ubuntu SMP Sat Mar 20 02:23:45  UTC 2010 x86_64 GNU/Linux

---

### Post by Omoronovo on 2010-03-24
Yes, the second splash is extraneous, but is just ignored as it's already specified in the line previously.

---

