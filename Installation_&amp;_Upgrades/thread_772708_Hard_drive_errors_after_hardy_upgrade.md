---
title: "Hard drive errors after hardy upgrade"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by lesshaste on 2008-04-28
Correction: DVD errors (not hard drive errors but I don't know how to change the title of the post).

I upgraded from gutsy to hardy using the network upgrade option (synaptic) and it almost entirely killed my system. The first serious problem seems to be caused by the new kernel. When I boot in the hardy kernel (2.6.24) I get a series of DVD drive warnings.  Here all the relevant lines in dmesg 



[   23.125524]     ide0: BM-DMA at 0xf300-0xf307, BIOS settings: hda:pio, hdb:pio
[   24.531732] hda: BENQ DVD DD DW1640, ATAPI CD/DVD-ROM drive
[   24.531767] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   24.532076] hda: UDMA/33 mode selected
[   24.532656] hda: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
[   24.532662] hda: task_in_intr: error=0x04 { AbortedCommand }
[   35.863928] hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[   35.863935] hda: status error: error=0x00 { }
[   35.863940] hda: drive not ready for command
[   35.863944] hda: ATAPI CD-ROM drive, 0kB Cache
[   35.863983] hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }


[...]

The complete dmesg from the broken 2.6.24 kernel is at [http://pastebin.com/f52736624](http://pastebin.com/f52736624)

I can boot using the old 2.6.22 kernel and the problem goes away.  Here are the hda lines using 2.6.22



[   22.017895]     ide0: BM-DMA at 0xf300-0xf307, BIOS settings: hda:pio, hdb:pio
[   22.753087] hda: BENQ DVD DD DW1640, ATAPI CD/DVD-ROM drive
[   23.423756] hda: selected mode 0x42
[   34.265604] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)



Any ideas?  I can provide more hardware information if needed.

Raphael

---

