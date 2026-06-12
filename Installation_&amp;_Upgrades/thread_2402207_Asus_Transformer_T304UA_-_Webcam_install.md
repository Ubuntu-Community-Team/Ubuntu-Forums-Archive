---
title: "Asus Transformer T304UA - Webcam install"
date: 2018-09-27
forum: Installation &amp; Upgrades
---

### Post by mikejoconnor on 2018-09-27
I've just installed ubuntu desktop on a Asus T304UA. Overall it seems to be working well with the exception of either camera. From what I can tell the device uses an HM2051 and OV8856 camera. I believe the front facing is the HM2051, rear facing is OV8856.


lspci -v gives me the following:
```
 00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)   Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
   Flags: bus master, fast devsel, latency 0
   Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02) (prog-if 00 [VGA controller])
   Subsystem: ASUSTeK Computer Inc. HD Graphics 620
   Flags: bus master, fast devsel, latency 0, IRQ 125
   Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
   Memory at d0000000 (64-bit, prefetchable) [size=256M]
   I/O ports at f000 [size=64]
   [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: i915
   Kernel modules: i915
00:05.0 Multimedia controller: Intel Corporation Skylake Imaging Unit (rev 01)
   Subsystem: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit
   Flags: fast devsel, IRQ 255
   Memory at ef000000 (64-bit, non-prefetchable) [disabled] [size=4M]
   Capabilities: <access denied>

00:13.0 Non-VGA unclassified device: Intel Corporation Sunrise Point-LP Integrated Sensor Hub (rev 21)
   Subsystem: Intel Corporation Sunrise Point-LP Integrated Sensor Hub
   Flags: bus master, fast devsel, latency 0, IRQ 20
   Memory at ef54b000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: intel_ish_ipc
   Kernel modules: intel_ish_ipc

00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21) (prog-if 30 [XHCI])
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP USB 3.0 xHCI Controller
   Flags: bus master, medium devsel, latency 0, IRQ 123
   Memory at ef520000 (64-bit, non-prefetchable) [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: xhci_hcd

00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
   Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
   Flags: fast devsel, IRQ 16
   Memory at ef530000 (64-bit, non-prefetchable) [size=32K]
   Capabilities: <access denied>
   Kernel driver in use: proc_thermal
   Kernel modules: processor_thermal_device


00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Thermal subsystem
   Flags: fast devsel, IRQ 18
   Memory at ef54a000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: intel_pch_thermal
   Kernel modules: intel_pch_thermal

00:14.3 Multimedia controller: Intel Corporation Device 9d32 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 1d2d
   Flags: fast devsel, IRQ 255
   Memory at ef510000 (64-bit, non-prefetchable) [disabled] [size=64K]
   Capabilities: <access denied>

00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller
   Flags: bus master, fast devsel, latency 0, IRQ 16
   Memory at ef549000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: intel-lpss
   Kernel modules: intel_lpss_pci

00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller
   Flags: bus master, fast devsel, latency 0, IRQ 17
   Memory at ef548000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: intel-lpss
   Kernel modules: intel_lpss_pci

00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller
   Flags: bus master, fast devsel, latency 0, IRQ 18
   Memory at ef547000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: intel-lpss
   Kernel modules: intel_lpss_pci

00:15.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #3 (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller
   Flags: bus master, fast devsel, latency 0, IRQ 19
   Memory at ef546000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: intel-lpss
   Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP CSME HECI
   Flags: bus master, fast devsel, latency 0, IRQ 132
   Memory at ef545000 (64-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: mei_me
   Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21) (prog-if 01 [AHCI 1.0])
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SATA Controller [AHCI mode]
   Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 124
   Memory at ef540000 (32-bit, non-prefetchable) [size=8K]
   Memory at ef544000 (32-bit, non-prefetchable) [size=256]
   I/O ports at f090 [size=8]
   I/O ports at f080 [size=4]
   I/O ports at f060 [size=32]
   Memory at ef543000 (32-bit, non-prefetchable) [size=2K]
   Capabilities: <access denied>
   Kernel driver in use: ahci
   Kernel modules: ahci

00:1d.0 PCI bridge: Intel Corporation Device 9d1a (rev f1) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0, IRQ 122
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
   Memory behind bridge: ef400000-ef4fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport
   Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP LPC Controller
   Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP PMC
   Flags: fast devsel
   Memory at ef53c000 (32-bit, non-prefetchable) [disabled] [size=16K]

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
   Flags: bus master, fast devsel, latency 32, IRQ 136
   Memory at ef538000 (64-bit, non-prefetchable) [size=16K]
   Memory at ef500000 (64-bit, non-prefetchable) [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: snd_hda_intel
   Kernel modules: snd_hda_intel, snd_soc_skl

00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
   Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SMBus
   Flags: medium devsel, IRQ 255
   Memory at ef542000 (64-bit, non-prefetchable) [size=256]
   I/O ports at f040 [size=32]
   Kernel modules: i2c_i801

01:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
   Subsystem: Intel Corporation Wireless 8260
   Flags: bus master, fast devsel, latency 0, IRQ 133
   Memory at ef400000 (64-bit, non-prefetchable) [size=8K]
   Capabilities: <access denied>
   Kernel driver in use: iwlwifi
   Kernel modules: iwlwifi


```


Any pointers on how to get the camera's working?

---

