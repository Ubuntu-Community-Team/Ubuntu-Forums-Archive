---
title: "Intel 5100AGN wifi not compatible w/  11.10 Kernel 3.0.0-12-generic"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by egrpioneer on 2011-10-16
Laptop (HP6730B) wifi adapter sees every wifi network in the neighborhood, but will not associate with my access point. 

Wireless performed perfectly well with very early alpha and beta 11.10. Last week it failed after kernel update, and very latest 11.10 clean install yesterday did not bring about a solution.

I'm sure the Canonical team and Ubuntu community will resolve this issue. 

dmesg | grep "iwlagn"

[   10.908569] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.908572] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   10.908656] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.908665] iwlagn 0000:02:00.0: setting latency timer to 64
[   10.908696] iwlagn 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.930707] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   10.930710] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   10.934220] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.934307] iwlagn 0000:02:00.0: irq 46 for MSI/MSI-X
[   11.316539] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692

---

