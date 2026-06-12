---
title: "Lucid boot hurdle number two."
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CJN on 2010-03-31
Ok so using my MBP 5,3 I couldn't boot normally w/ B1 so after some reading I did the F6 + nomodeset boot which got me a purple screen and dots but it stalled out with these errors:

[     56.411147] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 8, Type 4, Revision 4)
init: ureadahead-other main process (1235) terminated with status 4
init: ureadahead-other main process (1236) terminated with status 4

So, any suggestions so I can go find other more interesting bugs?

---

### Post by zacbarton on 2010-03-31
Beta 1 didnt boot for me either due to my nvidia card not working with nouveau. I got it booting by adding "nomodeset xforcevesa" to the boot command.

---

### Post by cor3huis on 2010-03-31
I feel your pain... BTW A defect is reported already, see
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393)

plz login there, and click "affect me too" link.
Daily build of 20100331 gives also no solace  

It is also could help to make it known wia the correct mail-lists or chat about it on an appropriate IRC channel
---------
Lucid Lynx 10.04  amd64  b43  b43-phy0  beta  beta1  broken  cd  error  install  mac  macbookpro  mbp  phy  pipe  terminated  unable  unreadahead unsupported  usb  wireless

---

