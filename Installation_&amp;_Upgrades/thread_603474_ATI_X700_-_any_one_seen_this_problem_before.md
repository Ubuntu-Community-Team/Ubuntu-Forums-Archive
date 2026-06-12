---
title: "ATI X700 - any one seen this problem before"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Peter09 on 2007-11-05
Hi,
I have a semi functional X700 in Gutsy. I have just noticed this error in the log file....

drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so

Anyone else got this?, is it a known problem and more importantly is there an easy work around

---

### Post by kellemes on 2007-11-05
[http://ubuntuforums.org/showthread.php?t=569654]("http://ubuntuforums.org/showthread.php?t=569654")

This message only means AIGLX is not supported by the driver.. Instead you need to use/install XGL for your card to get going..
**Or** install the newest ati-driver (fglrx) that is said to support AIGLX, you need to search the forum for a howto.

---

