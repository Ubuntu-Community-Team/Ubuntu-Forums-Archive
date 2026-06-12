---
title: "Problem with some external ATA controllers and DMA"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by mlwmohawk on 2006-08-21
Well, after spending a good deal of time chasing this down, and first supposing it was a bad hard disk, it is, in fact a bug in the Linux kernel.

[  669.969604] hdg: dma_timer_expiry: dma status == 0x21
[  679.959494] hdg: DMA timeout error
[  679.959522] hdg: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[  679.959532] ide: failed opcode was: unknown
[  684.958416] hdg: status timeout: status=0xd0 { Busy }
[  684.958422] ide: failed opcode was: unknown
[  684.958457] hdg: drive not ready for command
[  685.058319] ide3: reset: success
[  705.200926] hdg: dma_timer_expiry: dma status == 0x21
[  715.190818] hdg: DMA timeout error
[  715.190843] hdg: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[  715.190853] ide: failed opcode was: unknown


If I use the badblocks program on either of these drives (hde or hdg), I have no problem. When I run badblocks on both of them at the same time, I get DMA timeout errors.

I have tested this with a couple different silicon image based ATA cards as well as an old Promise ATA card.

Does anyone else see this?

---

