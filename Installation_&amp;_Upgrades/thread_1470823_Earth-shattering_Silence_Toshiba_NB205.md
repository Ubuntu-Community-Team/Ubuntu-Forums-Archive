---
title: "Earth-shattering Silence: Toshiba NB205"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2010-05-03
I KNOW the sound doesn't work on the NB205, which is a crying shame. In spite of the known sound problem, I did a 10.04 install to an SD card, which went fine. WiFi worked right away, etc. But, of course, no sound.

I tried the OpenSound approach, but didn't like the results. There was some sound, but no volume control. I decided it was too out-of-synch with the standard 10.04 for my tastes, so did a fresh re-install. So, now I'm soundless again.

There should be a real fix for this, no? But I've searched here (this forum) and there (everywhere else) to no avail.

Anyone got this working properly? Thanks.

---

### Post by silviutp on 2010-05-14
I have the same problem :( ...

Another problem is a very very long boot time. Do you experience that ?

I also installed on a SD card but is very slow, so I did another installation on hdd.

---

### Post by davidmohammed on 2010-05-14
can you dump the contents of lspci here - need to confirm what audio you have installed.

---

### Post by neoanderthal on 2010-05-23
> **davidmohammed said:**
> can you dump the contents of lspci here - need to confirm what audio you have installed.

lspci output for Toshiba NB 205:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

---

