---
title: "CPU #1 not responding - cannot use it"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by ttolstead on 2008-04-27
[solved] Does anyone have any solution for the following problem with an Athlon 64x2 5000+ (Dell 531s, 2048mb ram):

CPU #1 not responding - cannot use it

Dmesg snip:

[   49.748924] ACPI: Core revision 20070126
[   49.748971] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   49.752784] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[   49.752799] SMP alternatives: switching to SMP code
[   49.753118] Booting processor 1/1 eip 3000
[   69.070379] Not responding.
[   69.070383] Inquiring remote APIC #1...
[   69.070384] ... APIC #1 ID: 1000000
[   69.070485] ... APIC #1 VERSION: 80050010
[   69.070586] ... APIC #1 SPIV: ff
[   69.070687] CPU #1 not responding - cannot use it.
[   69.070699] Total of 1 processors activated (5228.70 BogoMIPS).
[   69.070928] ENABLING IO-APIC IRQs

I am running Kubuntu 8.04 kernel 2.6.24-16-generic

The system runs ok in other aspects, but does not use the second core.  The hardware is fine, it runs Vista as well as can be expected.  I would like to reformat and install Kubuntu as the only OS, but without dual core support it does not seem like a good idea.

---

### Post by ttolstead on 2008-04-27
In further researching this problem, I have come across the same situation in several other distributions.  Could it be that this is either 1) a misunderstanding of how things should be working, or 2) a kernel problem.  Any thoughts?

I have a similar machine running under Gutsy without any problems.

---

### Post by ttolstead on 2008-04-28
By experimenting with the i386 AMD 64 bit live disks, I was able to determine that both cores are used by the AMD 64 bit version.  I found this to be a little confusing as this is different from the Gutsy requirements.  In Gutsy, I installed the Generic version of the kernel and all was ok. In Hardy both versions report as generic.  It appeared that the i386 version found it, but it would not use it.  I have done a permanent install of the AMD 64 version and all is well now.

---

