---
title: "Preseed early_command insertion of debconf commands?"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by bhodi on 2007-08-06
I'm trying to make a single preseed file work on different machines. The problem is that the hdd device path differs:
```
d-i partman-auto/disk string /dev/cciss/c0d0

```
on one machine it is the above, and on the other it is /dev/cda.

I'd like to be able to change this on the fly, and from what I can tell the best bet is during early_command, before it scans the hard disks. I've found I can use lspci to determine which machine we are on without scanning the disks, but I can't seem to find a way to edit the debconf from the command line during early_command.

Is there a way to use db_set, db_input or another method during early_command to facilitate this?

---

