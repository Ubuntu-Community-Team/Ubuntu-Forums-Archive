---
title: "Booting kernel 2.6.32-2 as a Virtualbox guest."
date: 2009-11-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wildweathel on 2009-11-05
There was a problem with installing Virtualbox on the latest kernel that seems to have been resolved.  What about the converse, booting the latest Lucid kernel under Virtualbox?  I first noticed this under OSE 3.0.8, but I'm now using closed 3.0.10 with the same problem.

I unfortunately don't have hardware virtualization (silly Intel T5500 being one of the handful of Merom chips without it...), so this is running **without VT-x/AMD-V**.  

The kernel locks up in a busy-wait.

```

<snip>
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] console [ttyS0] enabled
[    0.000000] Fast TSC calibration failed
ected 1655.673 MHz processor.
[    0.044450] Calibrating delay loop (skipped), value calculated using timer frequency.. 3311.34 BogoMIPS (lpj=6622692)
ble entries: 512
Events: unsupported p6 CPU model 15 no PMU driver, software events only.
[    0.094443] Checking 'hlt' instruction... OK.
[   18.268027] SMP alternatives: switching to UP code
<nothing after a minute of full CPU utilization>

```

(complete loglevel=7 messages attached)

2.6.31-14 booted fine

```

<snip>
[    0.028372] Mount-cache hash table entries: 512
Counters: unsupported p6 CPU model 15 no PMU driver, software counters only.
[    0.062385] Checking 'hlt' instruction... OK.
[    0.107287] SMP alternatives: switching to UP code
[    0.588002] Freeing SMP alternatives: 19k freed
[    0.592810] ACPI: Core revision 20090521
[    0.609995] ACPI: setting ELCR to 0200 (from 0e00)
[    0.668002] weird, boot CPU (#0) not listed by the BIOS.
[    0.668089] SMP motherboard not detected.
mer: 6215919 (6149289)
[    0.675101] SMP disabled
[    0.741033] Brought up 1 CPUs
[    0.742125] Total of 1 processors activated (4415.16 BogoMIPS).
[    0.775069] Booting paravirtualized kernel on bare hardware
<snip>

```(boot messages attached)

It looks like somethings wrong with ACPI, halt, or SMP.  I'll see if disabling those helps.

Would someone else try to boot .32-2 on Virtualbox?

---

### Post by xebian on 2009-11-05
no problem here. VB 3.0.10

---

### Post by wildweathel on 2009-11-05
Alright, thanks.  I'm going to try a fresh install then, maybe something corrupted the kernel.  Are you using VT-x/AMD-V?  (Mouseover the chip icon in the bottom border of the Virtualbox window.)  Maybe this only affects the dynamic recompiler.

---

### Post by JCoster on 2009-11-06
Yep I can't boot either...  Going to hang in there booting .31 and wait until an update comes out which will hopefully sort it, but if a fresh install works let us know.

---

### Post by xebian on 2009-11-07
> **wildweathel said:**
> Alright, thanks.  I'm going to try a fresh install then, maybe something corrupted the kernel.  Are you using VT-x/AMD-V?  (Mouseover the chip icon in the bottom border of the Virtualbox window.)  Maybe this only affects the dynamic recompiler.

Have to because my guest are 64-bit.

---

### Post by jmmL on 2009-11-12
I'm also having this problem. Boots with -31, but with ext4 FS errors (I think this might be a separate issue with me using a dynamic virtual disk). Using OSE 3.0.8. Re-installing now with 3.0.10 non-OSE.

---

