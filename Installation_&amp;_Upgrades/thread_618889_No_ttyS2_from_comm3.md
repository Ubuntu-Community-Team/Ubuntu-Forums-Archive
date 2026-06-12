---
title: "No ttyS2 from comm3"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by nageldh11 on 2007-11-20
Information may not have been clear in my original post;

I just installed Ubuntu 7.10 on a Dell 8200, Xp in other partition.

My Dell 8200 has internal serial port UART Com1 (no devices)

There is a PCI board added which is a fax modem set for Com3


Ubuntu discovered the Com1 port find and it is /dev/ttyS0

Problem is Ubuntu found the fax modem but did not create a Com3 with /dev/ttyS2

I tried the "sudo wvdialconf" it sees no Com3

Could I disable Com1 internal and set my PCI board to Com1?

Ideas

Thanks

---

### Post by nageldh11 on 2007-11-22
Please delete this response.

---

