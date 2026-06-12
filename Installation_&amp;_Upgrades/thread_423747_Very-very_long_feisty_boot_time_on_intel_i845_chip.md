---
title: "Very-very long feisty boot time on intel i845 chipset"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by A-1337 on 2007-04-26
Hello!
I've just upgraded from edgy to feisty. Been very disapointed with its boot time. It used to be short in edgy and now it takes whole 119 seconds.

Most interesting part of /var/log/messages is
```

Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   42.945287] nvidia: module license 'NVIDIA' taints kernel.
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   43.285308] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   43.285800] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   43.643137] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   43.643149] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   43.965307] intel8x0_measure_ac97_clock: measured 56639 usecs
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   43.965314] **intel8x0: clocking to 48000**
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   99.204176] lp0: using parport0 (interrupt-driven).
Apr 26 11:15:30 dmitry-dsk-ubuntu kernel: [   99.251125] fuse init (API version 7.8)

```

That "intel8x0: clocking to 48000" takes more than 50 secs! It roughly doubles time of the entire process. Please, help found the way to do it faster:)
If that excerpt is not complete enough, the entire log of boot process can be found  [here](http://groups.google.com/group/cool-stuff-group/web/feisty-boot-log) .

---

