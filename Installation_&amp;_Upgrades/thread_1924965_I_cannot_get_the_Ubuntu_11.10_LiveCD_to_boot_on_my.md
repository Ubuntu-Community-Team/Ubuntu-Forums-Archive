---
title: "I cannot get the Ubuntu 11.10 LiveCD to boot on my HP Pavilion dv6"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by cravengemetzel on 2012-02-13
I have tried everything; with no kernel boot parameters, it boots a black screen (as if the screen on my laptop was off) . With "nomodeset" and "acpi=off" it will boot an orange blinking hyphen . With "radeon.modeset=0" and "rdblacklist=radeon" it will boot to command line; X is unable to start . Ironically, I have had no problems installing Arch Linux, granted that it also booted a black screen but "nomodeset" did the trick for initial boot . My Arch Linux system now runs fine with the following drivers: xf86-video-ati, xf86-video-fbdev, xf86-video-vesa .

```
[root@nightshade craven]# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9641
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 VGA compatible controller: ATI Technologies Inc Whistler [AMD Radeon HD 6600M Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```

```
[root@nightshade craven]# uname -a
Linux nightshade 3.2.5-1-ARCH #1 SMP PREEMPT Tue Feb 7 08:34:36 CET 2012 x86_64 AMD A8-3510MX APU with Radeon(tm) HD Graphics AuthenticAMD GNU/Linux

```

Any suggestions ? If you require more information on my system, please let me know .

---

