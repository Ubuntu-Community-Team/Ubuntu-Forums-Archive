---
title: "Installation hangs and display becomes corrupted 12.10 64-bit"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by Ozymandias_117 on 2012-12-14
Hi, I am attempting to install the x86-64 version of Ubuntu 12.10 on my desktop, but approximately 3/4 of the way through the install, it hangs and my display becomes corrupted.  I have left it alone for 2 additional hours just to make sure that it isn't continuing installing in the background, and I have tried with the grab updates/3rd party toggles on and off.  When I first boot up, everything works perfectly from the liveCD until I try to run the installer.

Hardware:
Gigabyte EP45T-UD3P Motherboard
Intel Core 2 Quad Q9400 CPU
ATI Radeon HD 5770 GPU

lspci:
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

lspci | grep VGA:```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series]
```

From searching the forums I see lots of possible solutions for similar problems AFTER the install, but I can't seem to get the installer to work.

Edit: Forgot to mention I have already tried with nomodeset as well

---

### Post by Ozymandias_117 on 2012-12-16
Only found fix was to just use 12.04.

---

