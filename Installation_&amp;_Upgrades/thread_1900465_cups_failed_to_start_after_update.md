---
title: "cups failed to start after update"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by vangop on 2011-12-26
Hi,
I've ran an update and among other things the cups was updated.
But during the update it failed to start, and it can't be started, thus breaking some of the dependent packets.
```
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cups (1.5.0-8ubuntu6) ...
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 cups
 cups-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Tried to reinstall it already..
The system was restored from a 1month old backup (tar of /, nothing fancy) on 2 different pcs and both of them have this issue. But the PC the backup was originally taken from was updated just fine and the cups is working fine.
In Syslog:
kernel: [25392.216224] init: cups pre-start process (22562) terminated with status 1
Any ideas?

---

### Post by vangop on 2011-12-27
Any ideas?

---

