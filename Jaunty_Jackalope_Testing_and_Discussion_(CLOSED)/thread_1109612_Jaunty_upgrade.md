---
title: "Jaunty upgrade"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by combatwombat_nz on 2009-03-28
I just updated a laptop to Jaunty from Hardy (through Intrepid). Upgrade to Intrepid was fine. Jaunty doesn't like the harddisk controller by the looks of it...
From Grub boot, it requires a key press to get moving, then fires numerous errors to screen, whilst actually loading what would be normal.
<snip>
 [ [ 547.956053]("skype:+1547956053?call")] ata1.00: BMDMA stat 0x26
 [ [ 547.956071]("skype:+1547956071?call")] ata1.00: cmd c8/00:08:27:c8:35/00:00:00:00:00/e2 tag 0 dma 4096 in
 [ [ 547.956075]("skype:+1547956075?call")]          res 50/00:00:2e:c8:35/00:00:00:00:00/e2 Emask 0x20 (host bus error)
 [ [ 547.956085]("skype:+1547956085?call")] ata1.00: status: { DRDY }
 [ [ 547.996716]("skype:+1547996716?call")] ata1.00: configured for UDMA/100
 [ [ 547.996736]("skype:+1547996736?call")] ata1: EH complete
 [ [ 548.011033]("skype:+1548011033?call")] sd 0:0:0:0: [sda][ 78140160]("skype:+178140160?call") 512-byte hardware sectors: (40.0 GB/37.2 GiB)
 [ [ 548.017015]("skype:+1548017015?call")] sd 0:0:0:0: [sda] Write Protect is off
 [ [ 548.017024]("skype:+1548017024?call")] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
 [ [ 548.029082]("skype:+1548029082?call")] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 [ [ 548.046815]("skype:+1548046815?call")] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
</snip>
Repeated hundreds of times.

Eventually it gets going into xubuntu, but certainly not fast as it should be, obviously because it's busy constantly logging this error.

Laptop is an Asus Z9000. Old but trusty. 
Any ideas?

Oh, and I tried adding all_generic_ide to the grub entry.

---

