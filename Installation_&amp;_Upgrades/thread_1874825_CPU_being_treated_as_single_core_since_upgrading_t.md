---
title: "CPU being treated as single core since upgrading to Ubuntu 11.10"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by jayhat on 2011-11-03
I've noticed performance issues since upgrading to 11.10, and out of curious I checked /proc/cpuinfo to find this:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Xeon(R) CPU           W3520  @ 2.67GHz
stepping	: 5
cpu MHz		: 2666.352
cache size	: 8192 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
```

That CPU is quad-core, but Ubuntu appears to be treating it as single core. It may have always been treated this way, with the performance regression being related to unity, however I doubt this.

Anyone have this same CPU? 
Is this a known issue?
If not, anyone have any suggestions on where to start looking?

Thanks


Edit: 
It's a stock standard Dell T3500 and I've checked the BIOS settings: 'support multiple cores' is enabled.

---

### Post by jayhat on 2011-11-03
Solved, needed to get grub to force acpi. No idea why this changed recently.

---

