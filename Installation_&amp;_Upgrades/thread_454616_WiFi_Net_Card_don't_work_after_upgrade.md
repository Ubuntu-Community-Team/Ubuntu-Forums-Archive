---
title: "WiFi Net Card don't work after upgrade"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by grgs on 2007-05-25
Hello,
I have a problem with wifi network card after upgrade kubuntu to Feisty 7.04.
The Model TabletLaptop  is HP tc4400.

when i run iwconfig from console  is none interface is wireless.
Before upgrade my system everything works fine.
Any idea?

---

### Post by jglen490 on 2007-05-25
Whatever driver and configuration you had before was overwritten by the Feisty install.  Your best bet is to search on the forums here for your wifi chip (Broadcom, Atheros, etc.) and Feisty.  there may be some solutions already available.

---

### Post by grgs on 2007-05-25
I don't know what chipset i have, but when i run lspci -v i take the following results about wifi card.

[   19.344000] ieee80211_crypt: registered algorithm 'NULL'
[   19.384000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.384000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.472000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.472000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.472000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.472000] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   19.472000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.636000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.636000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

---

### Post by grgs on 2007-05-25
I found the solution.

I was run
[B]
sudo apt-get install linux-restricted-modules-generic[/B]

When installed the modules, and after rebooted my system everything works fine.;)

Thank you

---

### Post by AnonymousFan9 on 2007-05-26
Hey, thanks for posting your solution. I had the same problem and I've been trying to fix it for several days now, when all I had to do was install the generic restricted modules :oops:

---

