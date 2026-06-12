---
title: "Radeon HD 6320 Unity3D warning message at upgrade to 12.10"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by tkrisz on 2012-10-26
Hello!
I have an AMD Radeon HD 6320 in my laptop.  
I started to upgrade from 12.04 to 12.10 and got the  [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D]("https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D") warning message.
I think this hw is not too old and not too new.
Could you help me find out what's the real reason?
Note, that months ago i was not satisfied with the graphic card's performance, but i don't remember what i did exactly if i did something, i just remember i planned to do the upgrade to 12.10, since it was not improved really.
lspci:
> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)


---

### Post by collisionystm on 2012-10-26
Did you try to install the drivers?

If you open a terminal, type

sudo apt-get install fglrx-updates

When finished, reboot.

---

### Post by tkrisz on 2012-10-26
Thx. That package was not installed.

---

### Post by collisionystm on 2012-10-26
> **tkrisz said:**
> Thx. That package was not installed.

Its the Proprietary AMD driver. You should be good to go.

---

