---
title: "LiveCD works ok but won't boot after install"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by Israphel on 2013-05-08
I own an Asus u46e bal7 and it's a pain in the ass with Linux. Most of the distros just don't work at all.

I can boot Ubuntu 13.04 ok but it won't start after reboot (aperently video problems). If I restart N times, sometimes it works. It always work in **nomodeset**

Here my hard:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
```

Thanks!

---

### Post by 2F4U on 2013-05-09
Are you saying you can boot into Ubuntu without problems when doing a cold start and you only have problems when you are rebooting? If it works consistently with nomodeset, why don't you add that permanently to the grub configuration?

---

### Post by Israphel on 2013-05-09
No no, livecd or liveusb works fine but installed version doesn't boot correctly.

And you can't live with nomodeset, cause you can't neither set a higher resolution nor enable video effects/hardware acceleration.

---

