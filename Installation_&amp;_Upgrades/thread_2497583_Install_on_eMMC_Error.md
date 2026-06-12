---
title: "Install on eMMC Error"
date: 2024-05-10
forum: Installation &amp; Upgrades
---

### Post by Panda_Stonetree on 2024-05-10
I have a IGEL UD3 M350C. Trying to install 24.04 onto its eMMC. Currently I have it installed via an external drive but I'd like to put it on the eMMC. This device does not have any other internal drive options.
I'm running into the below error, and can't access the eMMC. Any advice or suggestions would be helpful.

eMMC: SanDisk SDINBDG4-8G [COLOR=#333333][FONT=Arial]eMMC 8GB iNAND 7250 eMMC 5.1 WD/SD[/FONT][/COLOR]

```
$ sudo dmesg | grep mmc
[    1.033232] genirq: Flags mismatch irq 7. 00000088 (mmc0) vs. 00002088 (pinctrl_amd)
[    1.033518] mmc0: Failed to request IRQ 7: -16
```

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Root Complex
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 PCIe GPP Bridge [6:0]
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus B
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series] (rev 92)
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller
02:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
02:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Raven2 USB 3.1
02:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor
02:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller
02:00.7 Non-VGA unclassified device: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/Renoir Non-Sensor Fusion Hub KMDF driver
03:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)



```

---

### Post by aegnor on 2024-05-23
I run into the same problem after upgrading a mini pc from Ubuntu 23.10 to 24.04. With the new kernel (6.8.0-31-generic), the system fails to boot not finding the SSD. With the old kernel (6.6.3-060603-generic) it still works. It seems that the new kernel is not working with the storage controller I have:

```

tvpc ~ # lshw -class storage -class disk
  *-sata
       description: SATA controller
       product: FCH SATA Controller [AHCI mode]
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 61
       width: 32 bits
       clock: 33MHz
       capabilities: sata pm pciexpress msi ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:50 memory:fcd00000-fcd007ff

tvpc ~ # lspci | grep SATA
05:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)

```

I was unable to find anything more about this except this forum post.

---

### Post by aegnor on 2024-06-03
Today a new kernel was released which fixed it for me. The system boots and works as before (I did a upgrade from 23.10 to 24.04). The new kernel version is 6.8.0-35-generic.

---

