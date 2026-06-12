---
title: "preseed: use sdb for home ONLY if it exists"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by danieldrucker on 2013-02-11
Some of the machines I'm provisioning have a separate /dev/sdb to be used for /home, and some only have a single disk.

Is there a way I can set up preseed so that if /dev/sdb exists, it uses 100% of that for /home, but if it doesn't, it makes a /home partition on /dev/sda?

---

### Post by MAFoElffen on 2013-02-14
> **danieldrucker said:**
> Some of the machines I'm provisioning have a separate /dev/sdb to be used for /home, and some only have a single disk.

Is there a way I can set up preseed so that if /dev/sdb exists, it uses 100% of that for /home, but if it doesn't, it makes a /home partition on /dev/sda?
How I read this:
```

[COLOR="Red"]# Alternatively, you may specify a disk to partition. If the system has only
# one disk the installer will default to using that, but otherwise the device
# name must be given in traditional, non-devfs format (so e.g. /dev/hda or
# /dev/sda, and not e.g. /dev/discs/disc0/disc).
# For example, to use the first SCSI/SATA hard disk:
#d-i partman-auto/disk string /dev/sda
[/COLOR]

```
So if you specify the partman-auto example's expert-home recipe... and put device{/dev/sdb} in a def for a separated home? But I don't know if it will default back to including a mount of home back into the main root partition on sda or create a new separate /home partition on sda... I'm thinking that if /dev/sdb is not there when called from partman-auto, that "that" call will error and default back, causing /home to be in the /root of the partition created in /dev/sda.

You know, I might be curious enough to try that and see what it does... LOL

---

### Post by danieldrucker on 2013-02-14
Way to read the question.

---

