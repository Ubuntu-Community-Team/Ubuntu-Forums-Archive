---
title: "kernel panic. Not syncing"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by enriquemasa on 2006-10-10
Hi,
I've just build my new computer and I am trying to install the last ubuntu release, 2.06.1, and I am getting the same error over and over again.

kernel panic. Not syncing: attempted to kill init

The hard drive is new, is a 250 GB Hitachi, Serial ATA.

No idea if the problem is in the kernel, or maybe is a BIOS problem.

Any idea out there????

Thanks

---

### Post by az on 2006-10-10
You get this error after you did the install from the live cd?  If so, it sounds like Grub cannot find the root directory (? not sure).  It may be a bios problem.  You may have to reconfigure grub to look on another device since it is not using the device it thinks it's using...

---

### Post by enriquemasa on 2006-10-10
I haven't tried ubuntu's live cd yet, but I got the same error with Suse 9.3 live cd.

---

