---
title: "boot hangs if mem remap enabled"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by dr_jb on 2008-06-22
When I enable memory remap in the BIOS, ubuntu hangs during boot.  It boots fine if memory remap is disabled but with less memory.  It appears to hang on this line:
"ACPI: PCI Interrupt 0000:04:01.0[A] -> GS! 22 (level, low) -> IRQ 22"

I've tried other solutions listed in the forums (e.g. blacklist intel_agp, boot params mem=6144MB agp=off acpi=off) but none of them seem to work.

OS: Hardy Heron 8.04 desktop
MB: Asus P5B

---

