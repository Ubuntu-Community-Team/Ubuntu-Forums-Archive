---
title: "IRQ 18: nobody cared"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by nopark on 2005-07-30
During install (which was painfully slow, probably due to this same issue), I kept getting this error message over and over again.

I came to the point where I could choose additional packages to install, but I couldn't read a thing because this error message was overwriting the screen every 2 seconds or so. So I just rebooted.

After reboot, the messages are still there and the DE isn't working.

I tried the suggested irqpoll param and that didn't do anything.

I found a bug on the Debian bug tracker that seems similar: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309961](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309961)

I just tried another boot with the 'debug' param, and the syslog can be found in the [pastebin](http://paste.ubuntulinux.nl/831). The lines to notice (I think) are 4-39:
```
Jul 30 18:30:23 localhost kernel: irq 18: nobody cared (try booting with the "irqpoll" option.
Jul 30 18:30:23 localhost kernel:  [__report_bad_irq+49/119] __report_bad_irq+0x31/0x77
Jul 30 18:30:23 localhost kernel:  [note_interrupt+117/155] note_interrupt+0x75/0x9b
Jul 30 18:30:23 localhost kernel:  [__do_IRQ+211/273] __do_IRQ+0xd3/0x111
Jul 30 18:30:23 localhost kernel:  [sync_buffer+0/53] sync_buffer+0x0/0x35
Jul 30 18:30:23 localhost kernel:  [do_IRQ+25/36] do_IRQ+0x19/0x24
Jul 30 18:30:23 localhost kernel:  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Jul 30 18:30:23 localhost kernel:  [sync_buffer+0/53] sync_buffer+0x0/0x35
Jul 30 18:30:23 localhost kernel:  [dma_pool_create+180/279] dma_pool_create+0xb4/0x117
Jul 30 18:30:23 localhost kernel:  [generic_unplug_device+27/42] generic_unplug_device+0x1b/0x2a
Jul 30 18:30:23 localhost kernel:  [blk_backing_dev_unplug+17/19] blk_backing_dev_unplug+0x11/0x13
Jul 30 18:30:23 localhost kernel:  [sync_buffer+43/53] sync_buffer+0x2b/0x35
Jul 30 18:30:23 localhost kernel:  [__wait_on_bit+43/81] __wait_on_bit+0x2b/0x51
Jul 30 18:30:23 localhost kernel:  [sync_buffer+0/53] sync_buffer+0x0/0x35
Jul 30 18:30:23 localhost kernel:  [out_of_line_wait_on_bit+113/121] out_of_line_wait_on_bit+0x71/0x79
Jul 30 18:30:23 localhost kernel:  [wake_bit_function+0/52] wake_bit_function+0x0/0x34
Jul 30 18:30:23 localhost kernel:  [submit_bh+302/336] submit_bh+0x12e/0x150
Jul 30 18:30:23 localhost kernel:  [wake_bit_function+0/52] wake_bit_function+0x0/0x34
Jul 30 18:30:23 localhost kernel:  [__bread_slow+78/100] __bread_slow+0x4e/0x64
Jul 30 18:30:23 localhost kernel:  [__bread+38/44] __bread+0x26/0x2c
Jul 30 18:30:23 localhost kernel:  [pg0+945131185/1070015488] read_inode_bitmap+0x35/0x5c [ext3]
Jul 30 18:30:23 localhost kernel:  [pg0+945131561/1070015488] ext3_free_inode+0x151/0x315 [ext3]
Jul 30 18:30:23 localhost kernel:  [pg0+945147860/1070015488] ext3_mark_inode_dirty+0x27/0x31 [ext3]
Jul 30 18:30:23 localhost kernel:  [pg0+945135493/1070015488] ext3_delete_inode+0x94/0xb1 [ext3]
Jul 30 18:30:23 localhost kernel:  [pg0+945135345/1070015488] ext3_delete_inode+0x0/0xb1 [ext3]
Jul 30 18:30:23 localhost kernel:  [generic_delete_inode+178/285] generic_delete_inode+0xb2/0x11d
Jul 30 18:30:23 localhost kernel:  [iput+100/103] iput+0x64/0x67
Jul 30 18:30:23 localhost kernel:  [sys_unlink+182/251] sys_unlink+0xb6/0xfb
Jul 30 18:30:23 localhost kernel:  [__do_IRQ+239/273] __do_IRQ+0xef/0x111
Jul 30 18:30:23 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Jul 30 18:30:23 localhost kernel: handlers:
Jul 30 18:30:23 localhost kernel: [pg0+944692772/1070015488] (ide_intr+0x0/0x15d [ide_core])
Jul 30 18:30:23 localhost kernel: [pg0+944692772/1070015488] (ide_intr+0x0/0x15d [ide_core])
Jul 30 18:30:23 localhost kernel: [pg0+946771569/1070015488] (usb_hcd_irq+0x0/0x4e [usbcore])
Jul 30 18:30:23 localhost kernel: [pg0+947050933/1070015488] (ata_interrupt+0x0/0x14c [libata])
Jul 30 18:30:23 localhost kernel: Disabling IRQ #18
```

Also, a search on this forum shows a couple other people with this problem as well, but no replies.

---

### Post by amohanty on 2005-07-30
It would be helpful if you posted your system configuration.
I remember seeing this one and hunted down the link to _a_ possible fix:
[http://www.hentges.net/misc/howtos/p4p800_SATA.html](http://www.hentges.net/misc/howtos/p4p800_SATA.html)

I dunno if this will help, but you could try. As I said having your config would be very helpful.

Also try downloading the latest ISO if you dont already have it. 

HTH
AM

---

### Post by nopark on 2005-07-31
[QUOTE=amohanty]It would be helpful if you posted your system configuration.
I remember seeing this one and hunted down the link to _a_ possible fix:
[http://www.hentges.net/misc/howtos/p4p800_SATA.html](http://www.hentges.net/misc/howtos/p4p800_SATA.html)

I dunno if this will help, but you could try. As I said having your config would be very helpful.

Also try downloading the latest ISO if you dont already have it. 

HTH
AM[/QUOTE]
 Thank you very much amohanty! That link was very helpful.

I didn't have to enable compatibility mode, but I had to change "Enhanced Mode Support On" to "S-ATA" form "P-ATA/S-ATA". (For anyone else that comes to this thread with the same problem).

---

