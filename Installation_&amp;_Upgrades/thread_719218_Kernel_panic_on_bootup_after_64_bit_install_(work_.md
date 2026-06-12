---
title: "Kernel panic on bootup after 64 bit install (work around)"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Mazrick on 2008-03-08
Kernel panic on bootup after install (work around)

I tried to install Ubuntu 7.10 64 bit on my machine and reliably ran into panics, first for acpi, and then for CPU and PCI hardware etc.

Each of these error lines, resulted in panics
Error 1:
  acpi load error, followed by -
  Kernel panic - not syncing: Aiee, killing interrupt handler

Error 2: (after using noacpi param in grub kernel line)
  CPU 0: Machine Check Exception 4 Bank ...

Error 3: (this error was mixed intermittently with the error above)
  PCI: Cannot allocate resource region 0 of device 0 ...
  Kernel Panic - not syncing: attempting to kill init!

Moral of the story: The 32 bit distro performs without a single problem. Go with the 32 bit Ubuntu CD !

Hardware:
  AMD 64 - Sempron 3400+
  1G RAM
  NVIDIA 6800GT

Notes:
  Yes, I verified the CD integrity.
  Yes, the RAM check came back flawlessly.
  I'm writing this as a note for others that have my issues, in hopes that they will find this solution more quickly than I.

---

