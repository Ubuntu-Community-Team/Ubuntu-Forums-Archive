---
title: "irqpoll"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by metricben on 2006-07-31
Hi, I have upgraded my system with a new M/B, and various other things, so I am now reinstalling dapper drake.  I still have it installed on my old hard drive, but want to reinstall.  I put the livecd into my 2nd boot device, and start my system.  Up came the menu, so as per usual I selected the "Start or Install Ubuntu" option.  After a bit, it reports:
```
Jul 31 08:04:39 ubuntu kernel: [4294684.144000] irq 169: nobody cared (try booting with the "irqpoll" option)
``` I can append "irqpoll" to the boot options, and remove "quiet splash", but I still seem to recieve lots of errors, and it informs me that "irqpoll" gives a performance hit.  It eventually boots into livecd mode, and all is well. 

Would i have to "irqpoll" at every boot, giving me a performance hit?
What is IRQ #169?
Why does "nobody care"???

It looks like there are lots of drive errors, but for all I know, this might be a normal percentage of I/O problems.  Can someone please answer my questions, and suggest any ways of running Dapper Drake at full performance, or reassure me in some other way.

Note: I googled "IRQ #169" and found something about ethernet, would swithching from onboard, to an NIC help me?  I have the same video and sound card as before.

Here are some select unusual bits, and attatched is the whole kernel log:
```
Jul 31 08:04:39 ubuntu kernel: [4294667.296000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw irqpoll --
Jul 31 08:04:39 ubuntu kernel: [4294667.296000] Misrouted IRQ fixup and polling support enabled
Jul 31 08:04:39 ubuntu kernel: [4294667.296000] This may significantly impact system performance
...
Jul 31 08:04:39 ubuntu kernel: [4294678.010000] ICH5: chipset revision 2
Jul 31 08:04:39 ubuntu kernel: [4294678.010000] ICH5: 100%% native mode on irq 169
Jul 31 08:04:39 ubuntu kernel: [4294678.010000]     ide0: BM-DMA at 0xef60-0xef67, BIOS settings: hda:DMA, hdb:DMA
Jul 31 08:04:39 ubuntu kernel: [4294678.010000]     ide1: BM-DMA at 0xef68-0xef6f, BIOS settings: hdc:DMA, hdd:DMA
...
ul 31 08:04:39 ubuntu kernel: [4294680.268000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
Jul 31 08:04:39 ubuntu kernel: [4294680.430000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
...
Jul 31 08:04:39 ubuntu kernel: [4294684.144000] irq 169: nobody cared (try booting with the "irqpoll" option)
...
Jul 31 08:04:39 ubuntu kernel: [4294684.144000] Disabling IRQ #169
Jul 31 08:04:39 ubuntu kernel: [4294684.524000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Jul 31 08:04:39 ubuntu kernel: [4294684.524000] hdc: command error: error=0x52 { EndOfMedia LastFailedSense=0x05 }
Jul 31 08:04:39 ubuntu kernel: [4294684.524000] ide: failed opcode was: unknown

```

---

### Post by metricben on 2006-07-31
ah ive fixed it - someone suggested i upgraded my BIOS, and i can boot livecd  with no errors.

---

