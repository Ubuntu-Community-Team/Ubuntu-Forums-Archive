---
title: "Problem installing Broadcom Ethernet 5755"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by Schleproque on 2006-12-20
Good Day,

I am trying to install 6.06 on a HP xw4400 and here is my problem. The blasted ethernet controller is not recognized during installation. I can't use 6.10 for various business reason but 6.10 does recognize the ethernet card. 

This is what I get from lspci

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 039e (rev a1)
0000:3f:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167b (rev 02)

My guess is that tg3 is not up to date but trying to build I haven't been able to build a new one from the download from Broadcom.

Any ideas?

Thanks,
Rodney

---

### Post by ingo on 2006-12-22
a quick google came up with this:

[http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php)

---

