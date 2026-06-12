---
title: "Disk IO performance degrades horribly after upgrade to 10.10"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by david_frey on 2010-10-18
I upgraded my old Kubuntu installation to 10.10 Maverick Meercat and I am now experiencing a really annoying problem.  I boot my computer and everything seems fine for a while, but eventually my disk performance drops to horrible levels.  It's not gradual.  It's fine one second and then abysmal the next.

If I do "cp file1 file2" and then kill the cp process after 10s, there are only a couple of MB copied.

When I run dmesg after the performance degradation, I see this:
```

[12879.434115] irq 22: nobody cared (try booting with the "irqpoll" option)
[12879.434121] Pid: 0, comm: swapper Tainted: P            2.6.35-22-generic #34-Ubuntu
[12879.434124] Call Trace:
[12879.434126]  <IRQ>  [<ffffffff810cba5b>] __report_bad_irq+0x2b/0xa0
[12879.434137]  [<ffffffff810cbc5c>] note_interrupt+0x18c/0x1d0
[12879.434141]  [<ffffffff810cc45d>] handle_fasteoi_irq+0xdd/0x110
[12879.434145]  [<ffffffff8100cb12>] handle_irq+0x22/0x30
[12879.434149]  [<ffffffff81590bac>] do_IRQ+0x6c/0xf0
[12879.434152]  [<ffffffff81589793>] ret_from_intr+0x0/0x11
[12879.434154]  <EOI>  [<ffffffff81012c8f>] ? mwait_idle+0x6f/0xd0
[12879.434162]  [<ffffffff8158d1da>] ? atomic_notifier_call_chain+0x1a/0x20
[12879.434165]  [<ffffffff81008da3>] cpu_idle+0xb3/0x110
[12879.434170]  [<ffffffff8158332c>] start_secondary+0x100/0x102
[12879.434172] handlers:
[12879.434174] [<ffffffff813e2080>] (ata_bmdma_interrupt+0x0/0x240)
[12879.434179] [<ffffffff813e2080>] (ata_bmdma_interrupt+0x0/0x240)
[12879.434187] Disabling IRQ #22
[12886.080011] ata3: lost interrupt (Status 0x51)
[12886.080025] ata3.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6 frozen
[12886.080029] ata3.00: BMDMA stat 0x26, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
[12886.080032] ata3: SError: { UnrecovData HostInt 10B8B BadCRC }
[12886.080036] ata3.00: failed command: READ DMA
[12886.080042] ata3.00: cmd c8/00:00:53:64:fa/00:00:00:00:00/ea tag 0 dma 131072 in
[12886.080043]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x74 (host bus error)
[12886.080046] ata3.00: status: { DRDY }
[12886.080052] ata3: hard resetting link
[12886.590045] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[12886.731309] ata3.00: configured for UDMA/133
[12886.731364] ata3.00: device reported invalid CHS sector 0
[12886.731370] ata3: EH complete

```


I tried adding the irqpoll option by editing /etc/default/grub and setting:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"

I then ran update-grub.  This didn't seem to help at all.

Any ideas?

---

### Post by amauk on 2010-10-19
The fact that you're getting BadCRC errors indicates that the data being read from/written to drive is being corrupted en-route

This is almost certainly a hardware issue
I'd first try replacing the SATA cable

---

### Post by david_frey on 2010-10-21
I unplugged and then plugged in my SATA cables and the problem hasn't come back in the last few days.  Hopefully, it's gone for good.

---

### Post by forger on 2010-11-02
I had the same error: [https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/664066](https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/664066)
I'll try to do the same with the sata wires, thanks!

---

