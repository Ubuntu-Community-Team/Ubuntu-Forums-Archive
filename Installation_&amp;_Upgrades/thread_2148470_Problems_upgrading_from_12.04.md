---
title: "Problems upgrading from 12.04"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by iSpud on 2013-05-25
Is been trying to upgrade my machine to 12.10 and then 13.04, but I get a blank screen once I boot up for the first time. I've tried clean installing 13.04, upgrading the kernel from the command line to kernels up to 3.9, booting into failsafe mode, nothing works, this is both with 12.10 and 13.04. Non Debian distros work as I can boot Fedora 18 fine. For now I'm stuck on 12.04. Its frustrating! Mini itx biostar Intel chipset Pentium g2020 processor (64 bit)

---

### Post by 2F4U on 2013-05-25
What is the graphics card and which driver was installed in 12.04?

---

### Post by iSpud on 2013-05-25
The graphics is the integrated ivy bridge chipset from the Pentium G2020. The graphics driver is the stock intel one that comes with 12.04.2 LTS (64bit)

---

### Post by iSpud on 2013-05-25
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
    Subsystem: Biostar Microtech Int'l Corp Device 3108
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
    Subsystem: Biostar Microtech Int'l Corp Device 110d
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Biostar Microtech Int'l Corp Device 3108
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 3108
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 8229
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 3108
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 3108
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 5207
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 3108
    Kernel modules: i2c-i801
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
    Subsystem: Biostar Microtech Int'l Corp Device 5207
    Kernel driver in use: ata_piix
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Biostar Microtech Int'l Corp Device 230a
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
    Subsystem: Biostar Microtech Int'l Corp Device 6300
    Kernel driver in use: xhci_hcd
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
    Subsystem: Biostar Microtech Int'l Corp Device 6300
    Kernel driver in use: xhci_hcd

---

### Post by 2F4U on 2013-05-25
Here is a good step-by-step tutorial on how to diagnose blank/black screen problems:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by iSpud on 2013-05-25
Yeah, I saw that, I was hoping to not have to do that. But it's laid out well, at least. Here I go opening the hood...

---

