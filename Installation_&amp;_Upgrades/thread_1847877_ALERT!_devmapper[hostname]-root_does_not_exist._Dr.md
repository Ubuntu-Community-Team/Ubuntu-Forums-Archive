---
title: "ALERT! /dev/mapper/[hostname]-root does not exist. Dropping to a shell!"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by platz on 2011-09-21
I just did a fresh 10.04 PPC server install on some hardware I've used in the past for the same purpose (PowerMac10,1). This time I'm getting the following on the initial boot:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait for long enough?)
  - Check root= (did the system wait for the right device?)
- Missing mdules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/[hostname]-root does not exist. Dropping to a shell!
```The [hostname] in the alert is the actual hostname I determined during the installation.

---

