---
title: "multimedia keys and multicard reader not working"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by tpb03 on 2007-11-05
I have recently installed 7.10 gutsy gibbon to my Toshiba Satellite M70-169 and I cannot get my multimedia keys to work or my multicard reader to work.

I have tried to mount the multicard reader by adding the following lines to my rc.local file.

BUSID=`lspci | sed -e '/Texas Instruments.*FlashMedia/!D; s/ .*//;'`
setpci -s 06:04.3 4c.b=0x02

and the last few lines of a lspci test are

06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

I have tried the keytouch program for my multimedia keys, but I cannot get them working either. Has anyone got any tips or suggstions?
Thanks

---

