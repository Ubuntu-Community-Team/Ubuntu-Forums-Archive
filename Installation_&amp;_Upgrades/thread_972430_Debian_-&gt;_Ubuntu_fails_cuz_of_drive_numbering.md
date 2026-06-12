---
title: "Debian -&gt; Ubuntu fails cuz of drive numbering?"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Gralgrathor on 2008-11-05
Hi.

I have this box with 5 disks in it. It was until 3 days ago running Debian. Then I decided to install Ubuntu, using the same disk as a system-disk that I used under debian ("guided partitioning, use entire drive").

That same disk is designated by BIOS as the first place to boot from.

The installation process is completed, and Ubuntu restarts the machine. Then some text appears indicating that the system cannot find the disk to boot from.

I re-install debian (Testing/beta2), no worries, boots like a charm. I repeat the Ubuntu install process, formatting the entire system drive, and all I get is

```
ALERT! /dev/disk/by-uuid/[long string] does not exist. Dropping to a shell
```

Certainly there must be something I can do about this?

Thanks!

---

