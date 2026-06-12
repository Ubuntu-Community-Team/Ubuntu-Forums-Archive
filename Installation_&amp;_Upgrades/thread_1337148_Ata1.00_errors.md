---
title: "Ata1.00 errors"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by RFXCasey on 2009-11-25
Ok so I have this Compaq Presario sr1420nx. Every time I try to install Ubuntu on it I get this.


Code:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [61.306417] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 61.306483] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 61.306599] ata1.00: status { DRDY }
[ 91.444103] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 91.444163] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 91.444219] ata1.00: status { DRDY }

Trying different install options and nothing works. I have also tried several hard drives and still nothing works. The funny thing is that if I hook up a hard drive with Windows on it, the machine will boot and work fine. Tried formatting a hard drive with partition magic but it just locks up when searching for the drive. Any idea what causes this?

---

