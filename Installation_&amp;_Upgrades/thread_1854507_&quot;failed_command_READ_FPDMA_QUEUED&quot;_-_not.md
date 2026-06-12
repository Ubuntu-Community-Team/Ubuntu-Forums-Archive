---
title: "&quot;failed command: READ FPDMA QUEUED&quot; - not able to install Ubuntu"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by _ari on 2011-10-04
Backtrack and Debian - dual boot on my computer.
Debian giving me just an error on startup **"failed command: READ FPDMA QUEUED"** and Backtrack now freezing i wanted to install Ubuntu 10.10 on my machine (HP 625).
During installation i get **"No CDRom Drive was detected"** so i decided to install ubuntu with an usb drive.

With Unetbootin i just got "This drive is not bootable", so i tried Universal Usb Installer (pendrive) under Windows and now i was able to boot from usb, but: 

-) **[SIZE=1]_Booting Ubuntu directly from usb:_[/SIZE]** I get the Error again "failed command: READ FPDMA QUEUED [...] EH Complete"
Seems to be this error: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)
After a while i get to the ubuntu loading screen (with the 5 dots blinking away), but from there on: nothing... they are blinking and blinking and blinking and.... i think you got the idea
-) [SIZE=1]_**When picking "Install on hard drive":**_[/SIZE] Exactly the same: Same Error, same blinking -> nothing happens

*_Booting from CD and adding "cdrom-detect/try-usb=true" before "quiet" also was useless._*

Maybe it is a **broken hard drive?** -> but then i should still be able to boot from cd!
Funny thing is: _Knoppix Live CD (Version: 6.4.3) works like a charm_, so maybe it **has something to do with a kernel update or something?**

[SIZE=1]**_I am really desperate and this error couldn't have come at a worse time, so plz help me fast!!!_**[/SIZE]

*I also tried Ubuntu 10.04 getting "unable to find a medium containing a live file system", Debian Squeeze 64bit netinstall gives me "failed command: READ FDPMA QUEUED", then it seems to work but it freezes when trying to detect hardware.*

Plz help fast

Greetings, _ari

---

### Post by Redsandro on 2011-10-10
I have the same problem as you and this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)

It seems to be around for 5 releases of Ubuntu now, and I really need to get this fixed soon. But the bug is not even assigned to someone, so I'm like

[img]http://images.memegenerator.net/instances/400x/9867053.jpg[/img]

I am using **Ubuntu 11.10** with kernel **3.0.0-11** on my **Zotac Fusion** mainboard with **AMD A50M Fusion** chipset. The **Samsung Spinpoint F4EG 2TB** is the troubled drive.

Syslog:

```
Oct 9 16:34:33 Redsandro kernel: [71485.413301] ata2.00: exception Emask 0x10 SAct 0x1 SErr 0x280100 action 0x6 frozen
Oct 9 16:34:33 Redsandro kernel: [71485.413310] ata2.00: irq_stat 0x08000000, interface fatal error
Oct 9 16:34:33 Redsandro kernel: [71485.413316] ata2: SError: { UnrecovData 10B8B BadCRC }
Oct 9 16:34:33 Redsandro kernel: [71485.413322] ata2.00: failed command: READ FPDMA QUEUED
Oct 9 16:34:33 Redsandro kernel: [71485.413332] ata2.00: cmd 60/80:00:80:ec:05/00:00:93:00:00/40 tag 0 ncq 65536 in
Oct 9 16:34:33 Redsandro kernel: [71485.413335] res 40/00:04:80:ec:05/00:00:93:00:00/40 Emask 0x10 (ATA bus error)
Oct 9 16:34:33 Redsandro kernel: [71485.413339] ata2.00: status: { DRDY }
Oct 9 16:34:33 Redsandro kernel: [71485.413349] ata2: hard resetting link
Oct 9 16:34:33 Redsandro kernel: [71485.960075] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 9 16:34:33 Redsandro kernel: [71485.972453] ata2.00: configured for UDMA/33
Oct 9 16:34:33 Redsandro kernel: [71485.990105] ata2: EH complete
```a million times.

---

