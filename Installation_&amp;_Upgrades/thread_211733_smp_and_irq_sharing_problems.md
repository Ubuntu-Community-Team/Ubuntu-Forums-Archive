---
title: "smp and irq sharing problems"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by munsell on 2006-07-08
Hello,

I am having what I believe to be an irq sharing problem when using the k7 smp kernel (2.6.15-25-k7).  When I boot up using the SMP kernel and issue the commmand cat /proc/interrupts I get the following information:
```

           CPU0       CPU1
  0:      18433        185    IO-APIC-edge  timer
  1:        113          1    IO-APIC-edge  i8042
  8:          2          1    IO-APIC-edge  rtc
  9:       1426         66   IO-APIC-level  acpi
 12:       5349          2    IO-APIC-edge  i8042
 15:        814          1    IO-APIC-edge  ide1
 50:        782          1   IO-APIC-level  HDA Intel
 58:          0          0   IO-APIC-level  sdhci:slot0
201:       5612          1   IO-APIC-level  libata
217:      10141          1   IO-APIC-level  ohci_hcd:usb1, nvidia
225:          2          0   IO-APIC-level  ehci_hcd:usb2
233:       1100          1   IO-APIC-level  ohci1394, ndiswrapper
NMI:          0          0
LOC:      18019      18079
ERR:          0
MIS:          0

```

When I use the standard Ubuntu 386 kernel and issue the commmand cat /proc/interrupts I get the following information:
```

           CPU0
  0:      18118    IO-APIC-edge  timer
  1:        118    IO-APIC-edge  i8042
  8:          3    IO-APIC-edge  rtc
  9:       1505   IO-APIC-level  acpi
 12:       3881    IO-APIC-edge  i8042
 15:        745    IO-APIC-edge  ide1
 50:        805   IO-APIC-level  HDA Intel
 58:          0   IO-APIC-level  sdhci:slot0
201:       5668   IO-APIC-level  libata
209:       6684   IO-APIC-level  ohci_hcd:usb1
217:       2524   IO-APIC-level  ehci_hcd:usb2, nvidia
225:          2   IO-APIC-level  ohci1394
233:       1057   IO-APIC-level  ndiswrapper
NMI:          0
LOC:      15171
ERR:          0
MIS:          0

```

The things to note are that when I am using the 386 kernel ndiswrapper is not sharing an IRQ (as it is when I use the SMP kernel).  Also, when I am using the SMP kernel I seem to be mssing an IRQ (209).  My  problem is that when ndiswrapper shares an IRQ, I get the following errors:
From /var/log/kern.log
```

kernel: [17180212.732000] irq 233: nobody cared (try booting with the "irqpoll" option)
kernel: [17180212.732000]  [__report_bad_irq+42/144] __report_bad_irq+0x2a/0x90
kernel: [17180212.732000]  [handle_IRQ_event+61/112] handle_IRQ_event+0x3d/0x70
kernel: [17180212.732000]  [note_interrupt+135/224] note_interrupt+0x87/0xe0
kernel: [17180212.732000]  [__do_IRQ+252/272] __do_IRQ+0xfc/0x110
kernel: [17180212.732000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
kernel: [17180212.732000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
kernel: [17180212.732000] handlers:
kernel: [17180212.732000] [pg0+950710368/1069179904] (usb_hcd_irq+0x0/0x70 [usbcore])
kernel: [17180212.732000] [pg0+953498656/1069179904] (ndis_isr+0x0/0xd0 [ndiswrapper])
kernel: [17180212.732000] Disabling IRQ #233

```

With this in mind, my questions are as follows:

1.  Why would the SMP kernel have one less IRQ available?
2.  Is it possible to force something (like ndiswrapper) to not share an IRQ?

Any help is much appreciated.

Thanks!

---

