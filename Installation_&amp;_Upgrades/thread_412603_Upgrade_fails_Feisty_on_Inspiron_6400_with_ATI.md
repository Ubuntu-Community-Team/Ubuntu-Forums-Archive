---
title: "Upgrade fails: Feisty on Inspiron 6400 with ATI"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by FraserCampbell on 2007-04-18
I upgraded my kubuntu 6.10 installation to kubuntu 7.04 and on reboot X was not functional. X was failing with a signal 11, here are last few lines from /var/log/Xorg.0.log:

  Backtrace:
  0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
  1: [0xffffe420]
  2: /usr/bin/X(InitOutput+0x9aa) [0x80a5b9a]
  3: /usr/bin/X(main+0x27b) [0x807456b]
  4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d7febc]
  5: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

  Fatal server error:
  Caught signal 11.  Server aborting

I edited /etc/X11/xorg.conf and changed Driver from vesa to fglrx and now X starts fine.  I'm not sure why the upgrade process didn't chose the correct driver for me (assuming fglrx is correct).  I pretty sure that my laptop was actually installed with Ubuntu 6.06 originally, it was upgraded to 6.10 and finally now it is at 7.04 (not sure if the older original version contributed to this issue).

Since this laptop is very, very common I'd think a lot of people will run into this:

  Dell Inspiron 6400
  Intel Core Duo (T2400)
  ATI X1300 (aka M52)
  Broadcom BCM4401-B0 NIC
  Intel 3945ABG Wireless

Wireless, networking and sound all work fine, video/X11 was the only problem I've found so far.

---

