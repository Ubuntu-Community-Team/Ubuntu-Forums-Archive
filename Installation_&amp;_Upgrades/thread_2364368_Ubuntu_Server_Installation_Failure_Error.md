---
title: "Ubuntu Server Installation Failure Error"
date: 2017-06-22
forum: Installation &amp; Upgrades
---

### Post by jjulian0794 on 2017-06-22
Hello all,

I've been resurrecting old machines with ubuntu and ubuntu server for a while now, but on my latest project, I've run into an error that I've never come across before.  I'm trying to install ubuntu server 16.04 onto a Compaq Prosignia 740 server with a live disk.  The image I am using is the i386 network installer directly from Ubuntu's website, and I burnt the image to a cd+r using InfraRecorder at 10x write speed.

The disk spools up just fine and drops me at the Ubuntu installation options screen, and when I select Install and hit enter it looks like it's going to run just fine.  However, after about ten seconds, the code below is displayed and the process stops.  Like I said, I've never run into this before, so if anyone could help me understand what is causing the error or even just what the code means I would greatly appreciate it.  I have a feeling that it's a problem with the way I'm writing the disk image, but I could be totally wrong on that.  Thanks!

```
[    5.001836] /initrd.image: incomplete write (4096 != 38755418)
[    5.502843] uhci_hcd 0000:00:14.2: Fouund HC with no IRQ. Check BIOS/PCI 0000:00:14.2 setup!
[    5.503200] uhci_hcd 0000:00:14.2: init 0000:00:14.2 fail, -19
[    5.691517] RAMDISK: EOF while readin compressed data
[    5.691746] uncompression error
[    5.692687] Kernel panid - not syncing: VFS: Unable to mount root on unknown-block(0,0)
[    5.692994] CPU: 0 PID: 1 Comm: swapper/0 Not tainted 4.4.0-62-generic #83-Ubuntu
[    5.693273] Hardware name COMPAQ PROSIGNIA, BIOS
[    5.693461] c1ad7967 a8009a42 00000086 c90e5eec c13abd5f c90e5f34 fffffffa c90e5f04
[    5.693865] c11701e0 fffffffa c90e5f34 fffffffa cb95e000 c90e5f64 c1b92061 c19b6b04
[    5.694270] c90e5f34 c19b6ab0 c19b6a7c 00000000 c90e5f34 fffffffa 00008001 c19b650d
[    5.694669] Call Trace:
[    5.694811] [<c13abd5f>] dump_stack+0x58/0x79 
[    5.695015] [<c11701e0>] panic+0x81/0x1af
[    5.695215] [<c1b92061>] mount_block_root+0x199/0x20e
[    5.695430] [<c1b92210>] mount_root+0x63/0x68
[    5.695617] [<c1b9235a>] prepare_namespace+0x145/0x176
[    5.695834] [<c1b91d8a>] kernel_init_freeable+0x1b1/0x1d4
[    5.696068] [<c17af360>] kernel_init+0x10/0xe0
[    5.696276] [<c1099681>] ? schedule_tail+0x11/0x50
[    5.696334] [<c17b9049>] ret_from_kernel_thread+0x21/0x38
[    5.696334] [<c17af350>] ? rest_init+0x70/0x70
[    5.696334] Kernel Offset: disabled
[    5.696334] ---[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

---

