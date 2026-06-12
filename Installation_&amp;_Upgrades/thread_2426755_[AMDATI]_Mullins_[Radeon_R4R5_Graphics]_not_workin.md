---
title: "[AMD/ATI] Mullins [Radeon R4/R5 Graphics] not working after upgrade"
date: 2019-09-13
forum: Installation &amp; Upgrades
---

### Post by lance bermudez on 2019-09-13
No display if i hook up my tv to the computer with HDMI cable but I can remote ssh into the computer.

linux driver i use is 
xserver-xorg-video-amdgpu
xserver-xorg-video-radeon

# journalctl -b -p3
is attached in document[ATTACH]284016[/ATTACH]

$ lspci
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

$ glxgears
```

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  6 (X_GLXIsDirect)
  Serial number of failed request:  42
  Current serial number in output stream:  41

```

---

