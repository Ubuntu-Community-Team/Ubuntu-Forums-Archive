---
title: "OOPS during server install"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by MattNuzum on 2005-06-09
I'm creating a custom kick start CD and I'm getting an oops during the "configuring iptables" portion of the install.

Here is my kickstart file: [http://newz.gotdns.com/ks3.1.cfg](http://newz.gotdns.com/ks3.1.cfg)

Here is the oops, can anyone suggest how to prevent this?

```
Unable to handle kernel NULL pointer dereference at virtual address 00000000
 printing eip:
c0112a49
*pde = 00000000
Oops: 0000 [#1]
PREEMPT
Modules linked in: xfs reiserfs jfs ext3 jbd vfat fat af_packet pcnet32 mii nls_cp437 isofs ide_cd cdrom ide_disk ide_generic pdc202xx_new aec62xx alim15x3 amd74xx atiixp cmd64x cs5520 cs5530 cy82c693 generic hpt34x ns87415 opti621 pdc202xx_old rz1000 sc1200 serverworks siimage sis5513 slc90e66 triflex trm290 via82cxxx floppy usb_storage scsi_mod parport_pc parport fbcon font bitblit vga16fb vgastate vesafb cfbcopyarea cfbimgblt cfbfillrect usbserial usbhid usbkbd thermal processor fan uhci_hcd usbcore piix ide_core evdev unix
CPU:    0
EIP:    0060:[<c0112a49>]    Not tainted VLI
EFLAGS: 00010002   (2.6.10-5-386)
EIP is at try_to_wake_up+0x23/0x94
eax: 0000000f   ebx: c03653e0   ecx: c1227dc4   edx: c3e97ed8
esi: 00000000   edi: c3e97ed8   ebp: c3e97ee8   esp: c3e97ed4
ds: 007b   es: 007b   ss: 0068
Process kswapd0 (pid: 120, threadinfo=c3e96000 task=c3e82020)
Stack: 00000000 00000202 00000000 00000000 00000000 c3e97efc c0112ac7 00000000
       0000000f 00000000 c1227dc0 c4c53e43 c0137c70 00000000 000000d0 00000000
       00000000 00000040 00000000 c02ac3a0 00000002 0000000c c02ac3a0 c0138e1f
Call Trace:
 [<c0112ac7>] wake_up_process+0xd/0xf
 [<c4c53e43>] pagebuf_daemon_wakeup+0x14/0x17 [xfs]
 [<c0137c70>] shrink_slab+0x65/0x14c
 [<c0138e1f>] balance_pgdat+0x19e/0x2af
 [<c0138ff1>] kswapd+0xc1/0xc5
 [<c01265be>] autoremove_wake_function+0x0/0x3a
 [<c0102eca>] ret_from_fork+0x6/0x14
 [<c01265be>] autoremove_wake_function+0x0/0x3a
 [<c0138f30>] kswapd+0x0/0xc5
 [<c01011f9>] kernel_thread_helper+0x5/0xb
Code: 00 00 00 8b 5d fc c9 c3 55 89 e5 57 56 8d 7d f0 53 51 51 c7 45 ec 00 00 00 00 8b 75 08 57 56 e8 43 fd ff ff 89 c3 58 8b 45 0c 5a <8b> 16 85 d0 74 47 83 7e 28 00 75 3b 83 fa 02 75 0a ff 4b 0c c7
 <6>note: kswapd0[120] exited with preempt_count 1
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by MattNuzum on 2005-06-09
Interesting...

I booted from an untouched cd with the command line parameter
server ks=http://newz.gotdns.com/ks3.1.cfg
and got another oops. This time, during the "unpacking postfix-tls..." step.

---

### Post by MattNuzum on 2005-06-10
Fixed:
The installer needs more than 64MB RAM (at least when using KickStart).

Increasing to 96MB fixed it.

---

