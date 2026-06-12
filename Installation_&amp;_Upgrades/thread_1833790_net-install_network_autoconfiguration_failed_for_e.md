---
title: "net-install: network autoconfiguration failed for e1000e"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by ringonian on 2011-08-26
I put the mini.iso on a stick and I'm having problems getting past the network autoconfig:

grub.cfg boot options:
  boot=casper
  iso-scan/filename=/ubuntu-11.04-netinstall-i386.iso #renamed from mini.iso
  noeject
  noprompt
  splash

Dropping to the an ash console, i don't have many choices in commands but here are some of the steps i've performed:

```

$ lspci | grep Ether
02:00.0 Ethernet controller:  Intel Corporation 82573L Gigabit Ethernet Controller

$ lspci | grep e1000e
[    1.300341] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.300406] e1000e: Copyright(c) 1999 - 2011 Intel Corporation
[    1.300497] e1000e 0000:02:00.0: Disabling ASPM  L1
[    1.300568] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.300651] e1000e 0000:02:00.0: setting latency timer to 64
[    1.300850] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.301239] e1000e 0000:02:00.0: Disabling ASPM L0s
[    1.428526] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) [mac address]
[    1.428603] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.428738] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: 005301-003
[   26.064370] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[   26.120176] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[   27.416168] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[   27.416168] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[   29.002635] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control:x/Tx
[   29.002643] e1000e 0000:02:00.0: eth0: 10/100 speed: disabling TSO

$lsmod | grep e1000e
e1000e      138627    0

$ifconfig
-/bin/sh: ifconfig: not found

$dhclient
-/bin/sh: dhclient: not found

$dhcpcd
-/bin/sh: dhcpcd: not found

$ping 127.0.0.1
127.0.0.1 is alive!

$ping localhost
ping: bad address 'localhost'

$rmmod e1000e
-/bin/sh: rmmod: not found

```

I even modprobed e1000 and e100 and then retried hw detection in the install screen with similar results.  Does anyone have a clue where to go next?

---

