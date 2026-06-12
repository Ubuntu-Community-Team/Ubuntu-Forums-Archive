---
title: "Error when loading pata_pdc2027x"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by red-lichtie on 2012-07-03
After 7 years of service I decided to upgrade my old server (kernel 2.4.27).

Now the 2nd disk controller won't work properly, the IO rate is disasterous.

It is a Promise Ultra100 TX2 (PDC20268) and the interrupt is being disabled by the kernel when the driver ( pata_pdc2027x ) is inserted.

I've tried the nonpae kernel, different PCI slot, new BIOS for card and main board, turing all sorts of BIOS options on and off and nothing seems to help.

So after 4 days (and a couple of nights) of trying all sorts I don't know what else to try.

The mainboard is a ECS K7S5A.

I disabled the module from being loaded at boot to try it on its own and I get this in the syslog (its what I also get during normal boot too):
```
Jul  3 08:21:21 bigserver kernel: [  142.258341] pata_pdc2027x 0000:00:11.0: version 1.0
Jul  3 08:21:21 bigserver kernel: [  142.258754] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Jul  3 08:21:21 bigserver kernel: [  142.258762] PCI: setting IRQ 5 as level-triggered
Jul  3 08:21:21 bigserver kernel: [  142.258773] pata_pdc2027x 0000:00:11.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Jul  3 08:21:21 bigserver kernel: [  142.358124] pata_pdc2027x 0000:00:11.0: PLL input clock 16580 kHz
Jul  3 08:21:21 bigserver kernel: [  142.402584] scsi2 : pata_pdc2027x
Jul  3 08:21:21 bigserver kernel: [  142.406319] scsi3 : pata_pdc2027x
Jul  3 08:21:21 bigserver kernel: [  142.406529] ata3: PATA max UDMA/100 mmio m16384@0xcfffc000 cmd 0xcfffd7c0 irq 5
Jul  3 08:21:21 bigserver kernel: [  142.406537] ata4: PATA max UDMA/100 mmio m16384@0xcfffc000 cmd 0xcfffd5c0 irq 5
Jul  3 08:21:21 bigserver kernel: [  142.925147] irq 5: nobody cared (try booting with the "irqpoll" option)
Jul  3 08:21:21 bigserver kernel: [  142.925278] Pid: 0, comm: swapper/0 Not tainted 3.2.0-26-generic #41-Ubuntu
Jul  3 08:21:21 bigserver kernel: [  142.925284] Call Trace:
Jul  3 08:21:21 bigserver kernel: [  142.925308]  [<c155ebe7>] ? printk+0x2d/0x2f
Jul  3 08:21:21 bigserver kernel: [  142.925325]  [<c10b1449>] __report_bad_irq+0x29/0xd0
Jul  3 08:21:21 bigserver kernel: [  142.925333]  [<c10b16a4>] note_interrupt+0x104/0x150
Jul  3 08:21:21 bigserver kernel: [  142.925341]  [<c10af56e>] handle_irq_event_percpu+0x9e/0x200
Jul  3 08:21:21 bigserver kernel: [  142.925354]  [<c1027548>] ? default_spin_lock_flags+0x8/0x10
Jul  3 08:21:21 bigserver kernel: [  142.925362]  [<c1573bbd>] ? _raw_spin_lock_irqsave+0x2d/0x40
Jul  3 08:21:21 bigserver kernel: [  142.925369]  [<c10af70b>] handle_irq_event+0x3b/0x60
Jul  3 08:21:21 bigserver kernel: [  142.925380]  [<c1005c9f>] ? enable_8259A_irq+0xf/0x20
Jul  3 08:21:21 bigserver kernel: [  142.925389]  [<c10b1aa0>] ? handle_nested_irq+0xb0/0xb0
Jul  3 08:21:21 bigserver kernel: [  142.925395]  [<c10b1afe>] handle_level_irq+0x5e/0xa0
Jul  3 08:21:21 bigserver kernel: [  142.925400]  <IRQ>  [<c157b2b2>] ? do_IRQ+0x42/0xc0
Jul  3 08:21:21 bigserver kernel: [  142.925420]  [<c1058cb0>] ? usleep_range+0x40/0x40
Jul  3 08:21:21 bigserver kernel: [  142.925428]  [<c1051fc0>] ? local_bh_enable_ip+0x90/0x90
Jul  3 08:21:21 bigserver kernel: [  142.925434]  [<c157b1f0>] ? common_interrupt+0x30/0x38
Jul  3 08:21:21 bigserver kernel: [  142.925441]  [<c1051fc0>] ? local_bh_enable_ip+0x90/0x90
Jul  3 08:21:21 bigserver kernel: [  142.925447]  [<c1052005>] ? __do_softirq+0x45/0x1a0
Jul  3 08:21:21 bigserver kernel: [  142.925454]  [<c1051fc0>] ? local_bh_enable_ip+0x90/0x90
Jul  3 08:21:21 bigserver kernel: [  142.925458]  <IRQ>  [<c1052386>] ? irq_exit+0x76/0xa0
Jul  3 08:21:21 bigserver kernel: [  142.925468]  [<c157b2bb>] ? do_IRQ+0x4b/0xc0
Jul  3 08:21:21 bigserver kernel: [  142.925475]  [<c157b1f0>] ? common_interrupt+0x30/0x38
Jul  3 08:21:21 bigserver kernel: [  142.925483]  [<c10268da>] ? native_safe_halt+0xa/0x10
Jul  3 08:21:21 bigserver kernel: [  142.925494]  [<c100999a>] ? default_idle.part.4+0x4a/0x190
Jul  3 08:21:21 bigserver kernel: [  142.925501]  [<c1009aff>] ? default_idle+0x1f/0x40
Jul  3 08:21:21 bigserver kernel: [  142.925508]  [<c1001818>] ? cpu_idle+0xa8/0xe0
Jul  3 08:21:21 bigserver kernel: [  142.925523]  [<c1543535>] ? rest_init+0x5d/0x68
Jul  3 08:21:21 bigserver kernel: [  142.925534]  [<c1830771>] ? start_kernel+0x34d/0x353
Jul  3 08:21:21 bigserver kernel: [  142.925541]  [<c18303b5>] ? pass_bootoption.constprop.2+0xe2/0xe2
Jul  3 08:21:21 bigserver kernel: [  142.925548]  [<c18300a9>] ? i386_start_kernel+0xa9/0xaf
Jul  3 08:21:21 bigserver kernel: [  142.925552] handlers:
Jul  3 08:21:21 bigserver kernel: [  142.925596] [<c13b9190>] ata_bmdma_interrupt
Jul  3 08:21:21 bigserver kernel: [  142.925666] Disabling IRQ #5
Jul  3 08:21:21 bigserver kernel: [  143.024130] ata3.00: ATA-7: SAMSUNG SP1634N, UZ100-03, max UDMA/100
Jul  3 08:21:21 bigserver kernel: [  143.024143] ata3.00: 312581808 sectors, multi 16: LBA48 
Jul  3 08:21:22 bigserver kernel: [  143.124106] ata3.00: configured for UDMA/100
Jul  3 08:21:22 bigserver kernel: [  143.124491] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP1634N  UZ10 PQ: 0 ANSI: 5
Jul  3 08:21:22 bigserver kernel: [  143.128596] sd 2:0:0:0: [sdc] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jul  3 08:21:22 bigserver kernel: [  143.128747] sd 2:0:0:0: [sdc] Write Protect is off
Jul  3 08:21:22 bigserver kernel: [  143.128756] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jul  3 08:21:22 bigserver kernel: [  143.128848] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 08:21:22 bigserver kernel: [  143.129555] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jul  3 08:21:22 bigserver kernel: [  143.224348]  sdc:
Jul  3 08:21:22 bigserver kernel: [  143.224945] sd 2:0:0:0: [sdc] Attached SCSI disk
Jul  3 08:21:22 bigserver kernel: [  143.324476] ata4.00: ATA-7: SAMSUNG SP1614N, TM100-30, max UDMA/100
Jul  3 08:21:22 bigserver kernel: [  143.324489] ata4.00: 312581808 sectors, multi 16: LBA48 
Jul  3 08:21:22 bigserver kernel: [  143.424239] ata4.00: configured for UDMA/100
Jul  3 08:21:22 bigserver kernel: [  143.424580] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG SP1614N  TM10 PQ: 0 ANSI: 5
Jul  3 08:21:22 bigserver kernel: [  143.425139] sd 3:0:0:0: [sdd] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jul  3 08:21:22 bigserver kernel: [  143.425271] sd 3:0:0:0: [sdd] Write Protect is off
Jul  3 08:21:22 bigserver kernel: [  143.425280] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Jul  3 08:21:22 bigserver kernel: [  143.425335] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 08:21:22 bigserver kernel: [  143.426090] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jul  3 08:21:22 bigserver kernel: [  143.524418]  sdd:
Jul  3 08:21:22 bigserver kernel: [  143.525031] sd 3:0:0:0: [sdd] Attached SCSI disk

```

On the old (ancient?) kernel it worked without a hitch:
```
Jun 30 09:58:27 server kernel: PDC20268: IDE controller at PCI slot 00:0d.0
Jun 30 09:58:27 server kernel: PDC20268: chipset revision 2
Jun 30 09:58:27 server kernel: PDC20268: not 100%% native mode: will probe irqs later
Jun 30 09:58:27 server kernel: PDC20268: ROM enabled at 0xcffe0000

```

Can anyone help me with this?

Thanks!

---

