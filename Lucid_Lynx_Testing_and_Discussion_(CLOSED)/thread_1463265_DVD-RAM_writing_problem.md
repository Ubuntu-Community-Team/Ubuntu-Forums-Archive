---
title: "DVD-RAM writing problem"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-04-26
i try to write dvd-ram but it shows read only, filesystem is udf. I tested disk utility too but it shows message:

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sr0: Input/output error

**SOLVED**

---

### Post by jfernyhough on 2010-04-26
1 - does the disc work in another drive?
2 - have you locked the disc (e.g. with a Windows RAM utility)?

---

### Post by forcecore on 2010-04-27
no i have not locked or something but even Disk utility cannot erase it, how to force erase?

---

### Post by forcecore on 2010-04-27
Looks like libudf0 or udftools solved this i installed both.

---

