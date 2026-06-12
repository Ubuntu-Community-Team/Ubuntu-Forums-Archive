---
title: "newer kernel updates AFTER 2.6.32-17 seem to be having boot problems"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by bmullan on 2010-07-26
I've been having a problem on my AMD based machine, 4cpu, gigabyte ga-ma78gm-s2h Mobo, 8GB mem, two 2 terabyte Sata HDs.

One thing I've found is that _any_ kernel **after 2.6.32-17** has a randomness at boot time whether the system will completely boot or not.

For instance just today I downloaded and installed **2.6.32-24**

It fails to boot (I've tried cold boot, warm boot).
Running its repair also fails to completely boot.

My experience is that if I keep trying it "may" eventually boot but
I believe there was some change after 2.6.32-17-generic that's causing the problem.

Because as with 2.6.32.23... which also fails to complete bootup many times... eventually *my guess is* that 2.6.32.24 [I]will also boot "sometimes".
[/I]
But why does **2.6.32.17** *_always_* boot for me?   Something changed and its not my setup.

---

### Post by lemming465 on 2010-08-15
At a guess something deep in the bowels of the ACPI & device probing mutated on you.
If you try newer kernels (e.g. from the mainline PPA or from meerkat) do they work any better?

---

