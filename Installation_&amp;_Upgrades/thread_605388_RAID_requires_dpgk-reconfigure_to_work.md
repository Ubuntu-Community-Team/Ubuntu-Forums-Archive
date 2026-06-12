---
title: "RAID requires dpgk-reconfigure to work"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by bobpaul on 2007-11-07
Since upgrading to Gutsy I've been required to run to do the following to get my raid device operating and mounted every time the PC boots up:

```
$ sudo dpkg-reconfigure mdadm
$ sudo mdadm --assemble --scan
$ sudo mount -a
```

If I attempt to assemble before reconfiguring mdadm, I receive an error that neither /dev/md/0 nor /dev/md0 exist. Any ideas as to what I can do to avoid this extra work?

---

