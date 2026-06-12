---
title: "error message ubuntu 10.04"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lela19 on 2010-04-02
Please help!

I can't start ubuntu 10.04. Can't get passed the logo screen. Error message...
filesystem has errors SIFM

fsck from util-linux-ng. 2.17.2
/dev/sda/contains a file system with errors, chck forced.
/dev/sda1:e2fsck cancelled
mountall:fsck/[365] terminated with status 36
mountall:filesystem has errors:/
init:plymouth main process (344) killed by SEGV signal

---

### Post by dcstar on 2010-04-03
> **lela19 said:**
> Please help!

I can't start ubuntu 10.04. Can't get passed the logo screen. Error message...
filesystem has errors SIFM

fsck from util-linux-ng. 2.17.2
/dev/sda/contains a file system with errors, chck forced.
/dev/sda1:e2fsck cancelled
mountall:fsck/[365] terminated with status 36
mountall:filesystem has errors:/
init:plymouth main process (344) killed by SEGV signal

Boot off the Live CD and do a manual fsck on it.

---

