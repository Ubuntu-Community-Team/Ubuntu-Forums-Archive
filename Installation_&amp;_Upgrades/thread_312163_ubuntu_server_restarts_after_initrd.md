---
title: "ubuntu server restarts after initrd"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by beaucage.peter on 2006-12-04
Hello,

I have a newly-installed Ubuntu server 6.06 LTS (Dell laptop, Pentium-M 233, 128mb ram, 4GB IDE HDD) that boots past BIOS, past the GRUB selection, begins to load the kernel, then runs the initrd, hesitates, and very quickly scrolls "savedefault" and "boot" before going back to BIOS (restart) and repeating the same process.  

This same process happens regardless of whether I choose normal or rescue options in GRUB.

Thanks,

Peter Beaucage

---

### Post by CyberX on 2006-12-04
Hi.
If "Pentium-M 233" means Pentium MMX, then the server kernel doesn't run on it (it was compiled for Pentium Pro, Pentium II and above, see [this thread]("http://ubuntuforums.org/showthread.php?t=300390") and there also other threads in Server Forums related to this issue).

---

