---
title: "Feisty Fawn on ASUS P5S533"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by marcozambi on 2007-06-21
Hi!

I am an happy and satisfied Ubuntu 7.04 user.
Some days ago I tried to install Feisty Fawn on may (winxp workin') PC.
I booted (an rebooted often) with 7.04 live cd. Sysyem goes up flawlessly.

But after install, the system refuses to boot up from HHDD, and hangs on boot for a little while. Then, it comes up with this prompt "(initramfs)", accepting few commands.
I think it could be a problem originating from disk driver. On console I can read this last message:
"[28.6557401] EIP: [<e0871625>] sis_init_one+x75/0x3c0 [pata_sis] SS:ESP 0068:dfed

ALERT! /dev/disk/by-uuid/c2b153db-6b17-4ae5-b018-7eb06cd0020e does not exist. Dropping to a shell!

Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu3) built-in shell (ash)
"

I cannot understand why I can boot flawlessly (and access this HHDD) from livecd, and now seems that the kernel cannot find the very same HHDD on bootup.

My system have an ASUS P4S533 with SIS 645DX chipset, a normal IDE -  20 Gb disk,  512 Mb RAM.

Il boot da CD Live 32 bit va benissimo, e ho installato senza errori nè problemi occupando l'intero disco.

Any idea?

---

