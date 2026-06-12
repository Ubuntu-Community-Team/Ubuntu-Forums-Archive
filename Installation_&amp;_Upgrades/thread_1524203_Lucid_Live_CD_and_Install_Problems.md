---
title: "Lucid Live CD and Install Problems"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by kamlapati on 2010-07-04
Simple summary:
 
Using the live disk, Lucid stays on the boot screen (moving dots) for about twenty minutes, then goes black, and the monitor goes into powerdown mode. Keys and mouse do nothing. It does the same with the boot parameter set to nomodeset.

After an alternate install, apparently successful, the screen goes black and powers down immediately after the boot screen appears and a beep.

Details:

New system install
ASUS M4A89GTD PRO motherboard
Phenom II x4 945
2 x 2GB DDR3
Radeon HD 5570 PCIex16 video card
Western Digital 1TB HDD

LSPCI for the system, now running Fedor 13 (ouch!)

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate 
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) 
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40) 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40) 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40) 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control 
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68d9 
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] 
02:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02) 
02:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02) 
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) 
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 



What else should I try? I have been using Ubuntu since nearly the beginning, but my skills are modest. With my current problems I don't even know how to get to a terminal screen to look at log files.

BTW, I would rather debug using the Live CD, since I have a proceeded with an alternate distro install, and I don't want to wip it out until I have a high chance of a successful install.

I see that other folks here have trouble installing and booting Lucid, but I don't know how to determine which problem I have. None of the posts I've found look the same as mine.


Thanks all for your help!

---

### Post by kamlapati on 2010-07-05
I've been searching around and found this on Launchpad, bug #560306.

I'll try the radeon.modeset=0 parameter on the LiveCD boot options and report back.

---

### Post by kamlapati on 2010-07-06
OK, radeon.modeset=0 didn't work. 

Any other ideas, folks?

---

### Post by kingbirdy on 2010-07-06
perhaps make sure you have a big enough CD/try a flash drive. When I installed I had a big enough CD, but it didn't seem to work. Then I set up a flash drive, and it worked fine. Try that.

---

### Post by Rubi1200 on 2010-07-06
> **kamlapati said:**
> OK, radeon.modeset=0 didn't work. 

Any other ideas, folks?

Maybe try either radeon.modeset=1 or xforcevesa and see if that helps.

---

### Post by kamlapati on 2010-07-07
Rubi, I saw your posts on similar problems. Thanks for the assistance.

I'm temporarily set up with Fedora, and although I really want to get back to Ubuntu, I can't afford to disrupt my workflow, so I'm planning on debugging first with a VM, and then with a dual boot Fedora/Ubuntu configuration.

I'll keep y'all posted.

---

### Post by Rubi1200 on 2010-07-07
You are welcome :)

Keep us posted and don't forget to ask questions if you have other issues.

---

### Post by kamlapati on 2010-07-11
I was able to boot the LiveCD with the options:

     radeon.modeset=0 xforcevesa


Now onwards to a dual boot with my existing Fedora system.

---

