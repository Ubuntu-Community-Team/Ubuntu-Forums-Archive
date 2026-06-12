---
title: "How to install 3D accelerator"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by adithya2 on 2013-10-04
I have ATI Raedon graphics card and I want to install 3D accelerator to improve the graphics.
Any suggestions in this regards would be helpful.

---

### Post by Mark Phelps on 2013-10-05
There's no such thing as a Radeon "3D accelerator".  There ARE the restricted Linux drivers from AMD which do provide some 3D acceleration -- but you should see them listed in Additional Drivers.

We first need to find out what version of Ubuntu you are running, and then, the make and model of your Radeon card.  For the latter, open up a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA" -- and post that back here.  It could be that your Radeon card is too old for current accelerated drivers.

---

### Post by adithya2 on 2013-10-05
Ubuntu Version: 11.10
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series]
07:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)



```

---

### Post by raja.genupula on 2013-10-05
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

There you can have the download of your driver.

---

