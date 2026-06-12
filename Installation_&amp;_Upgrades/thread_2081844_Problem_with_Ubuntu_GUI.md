---
title: "Problem with Ubuntu GUI"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by pwert00 on 2012-11-07
Hi all,

I bought a HP Pavilion G6 with Windows 8 on it about a week and a half ago, and I wanted to try to install ubuntu on the system.  After much trouble, I did get ubuntu on the system and I can boot into it.  However, after I log in there is no GUI and I have not been able to solve this problem.  

When I first installed Ubuntu, the operating system worked fine except the screen would constantly flicker.  When I updated my video card, restarted, and logged in there was no longer a GUI.  All of the folders on the desktop disappeared, there was no sidebar, and there was no top panel thing that has "file, edit, view, battery life, etc.".  There was only a background, and I could open the terminal by typing "ctrl+alt+'t'".  Can anyone help me get this panel back?

Thanks,

Paul

---

### Post by carl4926 on 2012-11-07
Sounds like it's gone in to fall back mode, which would be related to your graphics.

You ought to inform us of what graphics your machine has and what exactly you installed.

---

### Post by pwert00 on 2012-11-08
Thanks, How do I do this?

EDIT: As in, how do I check what graphics I have installed?

---

### Post by carl4926 on 2012-11-08
post the output of

```
lspci -nnk
```

---

### Post by pwert00 on 2012-11-08
K, I'm actually installing Ubuntu on two identical laptops.  One of them reads:

```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]
    Subsystem: Hewlett-Packard Company Device [103c:1849]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7520G] [1002:9990]
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: radeon
    Kernel modules: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Device [1002:9902]
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1414]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:10.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: xhci_hcd
00:10.1 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7804]
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel modules: i2c-piix4
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2 [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3 [1022:1403]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by carl4926 on 2012-11-08
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7520G] [1002:9990]
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: radeon
    Kernel modules: radeon
```

I'm not familiar with this device but radeon is the OS driver.
I suspect you would do better with xubuntu which has less requires for graphics effects

---

### Post by pwert00 on 2012-11-08
Can anyone else help?

Thanks,

Paul

---

