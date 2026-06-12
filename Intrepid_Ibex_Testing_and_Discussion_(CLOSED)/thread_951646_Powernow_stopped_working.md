---
title: "Powernow stopped working"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by synthaxx on 2008-10-18
Just ran my latest batch of intrepid updates, including the 2.6.27-7 kernel, and now powernow stopped working and locked my cpu to its lowest possible speed. It's enabled in the bios.

When i do a dmesg|grep power i get:
```
[  324.387055] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (2 cpu cores) (version 2.20.00)
[  324.390678] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x8
[  324.390693] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xa
[  324.390699] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xc
[  324.390708] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe
[  324.390713] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[  324.390719] powernow-k8: failing init, change pending bit set
[  324.390832] powernow-k8: failing init, change pending bit set
[  484.201265] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (2 cpu cores) (version 2.20.00)

```

Repeating 3 times.

Restarting /etc/init.d/powernowd gives me an error that frequency scaling is not supported.

I tried sudo modprobe powernow-k8 after removing and reinstalling powernow and i get: 
```
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): No such device
```

catting /proc/cpuinfo confirms that it's stuck at 1 ghz.

Going back to 2.6.27-5 didn't help.

Anyone got any ideas about how to at least get it back to 2.4 ghz?

/edit

After reinstalling 2.6.27-5 and powernowd i have frequency control back in in that kernel, but still none in the 27-7.

---

### Post by kingtiger01 on 2008-10-19
Same issue here -7

8.10(Intrepid) 
AMD X2 5600+
Abit A8N SLI
ACPI and Quiet and Cool are enabled in the Bios.

---

