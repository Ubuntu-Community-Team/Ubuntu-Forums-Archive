---
title: "Intel Pro 1000 PT Quad Port Card"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by nekret on 2014-04-05
I'm working on a new install of Ubuntu 13.10 server on a (mostly) new set of hardware and I'm having a tough time getting the Intel Pro 1000 PT Quad port network card to show up (even in lscpi). I can plug a network cable into one of the ports on the card and I get link, the card was taken out of a working setup to be installed in this machine. Any help is appreciated!

motherboard: Gigabyte GA-Z87X-HD3

lspci output:
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
```

---

### Post by nekret on 2014-04-05
Also forgot to mention I've tried setting noapic nolapic acpi=off and nomodeset in /etc/default/grub on the GRUB_CMDLINE_LINUX_DEFAULT variable.

---

