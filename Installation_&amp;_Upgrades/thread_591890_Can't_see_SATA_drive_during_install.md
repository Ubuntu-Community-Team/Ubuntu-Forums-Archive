---
title: "Can't see SATA drive during install"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Jorenko on 2007-10-25
I'm trying to install gutsy on a new machine I just built, but the system can't see my SATA drive. Here's my specs:

MSI K9N4 SLI-F AM2 NVIDIA nForce 500 SLI MCP ATX AMD Motherboard
MSI NX8600GTS-T2D256E-OC GeForce 8600GTS 256MB 128-bit
AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Socket AM2 65W Black Edition
Transcend JETRAM 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800
Seagate Barracuda 7200.10 ST3320620AS 320GB 7200 RPM SATA 3.0Gb/s Hard Drive
LITE-ON 20X DVD±R DVD Burner

lspci output
```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

```

I can confirm that the BIOS can see the drive. It beeped at me a lot when I had the optical drive and the hdd on adjacent sata ports, but I've corrected that and still no love from gutsy. Any suggestions, anyone?

Thanks.

---

### Post by Jorenko on 2007-10-27
Well, I guess the drive was just DOA. I tried it with a windows install disk and also in another computer, with the same results. RMA here I come.

---

