---
title: "Card reader in a loop since 2.6.20-14 upgrade"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by rwb on 2007-04-09
Hi has anyone else had this problem?

Hardware is a hp nc6120 laptop with the Ti multi card reader

installed Fiesty 7.04 beta and great with the 2.6.20.12 Kernel every thing worked including the card reader (SD only)

then came the update to 2.6.20-14!!!!!!
First came the SLOOOOOOOOW boot up - fixed thanks to this forum:) 
but now when i insert the sd card i get this:.........

Apr  9 15:54:58 rwb-laptop kernel: [  190.920000] tifm_7xx1: sd card detected in socket 3
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000] mmcblk0: mmc3:aaaa SD01G 992000KiB 
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000]  mmcblk0: p1
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 4 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.112000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 13 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.116000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 9 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983609
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983610
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983611
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983612
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983613
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983614
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983615
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983616


ad infinitum!!!!!!!
until you remove the card any ideas?

---

