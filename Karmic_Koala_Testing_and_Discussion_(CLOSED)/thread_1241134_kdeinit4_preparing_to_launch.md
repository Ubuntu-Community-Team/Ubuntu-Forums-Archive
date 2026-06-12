---
title: "kdeinit4: preparing to launch"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-15
Hi!

Kubuntu Karmic up to date is in use.

Sometimes I get on this or that Konsole such message (shown below). If it's an indicator of some defect, how to cure? If it isn't - how to eliminate?

```
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
<unknown program name>(4172)/ KStartupInfo::createNewStartupId: creating:  "anli;1250364976;386852;4172_TIME0" : "unnamed app"
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-anli" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
<unknown program name>(4172)/ KStartupInfo::createNewStartupId: creating:  "anli;1250365022;858215;4172_TIME0" : "unnamed app"
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-anli" is owned by uid 1000 instead of uid 0.
```

---

### Post by ilna on 2009-08-15
Aha-aha... It seems I **must** use kdesudo instead of sudo to start any KDE application.

---

