---
title: "Configuring GRUB for two nVIDIA GPUs when no serial port available"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2016-02-12
I am having trouble monitoring the Kernel on an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon64® LE-1620, nVIDIA® nForce® 785 MCP; 4 GiB DDR2-533 main memory) modified for projection duty with a Shuttle® PC6300001 power supply and msi® N610GT-MD1GD3/LP display adapter (810 MHz nVIDIA® GF119, 1 GiB DDR3-1334 video memory).  Graphically, the N610GT will be primary, driving two 1080p loads upon installation (Display 1 via DVI-D, Display 2 via HDMI).

I have deliberately reduced the memory available to the planar nVIDIA® C77 GPU to 64 MiB (leaving 3.9375 GiB available for main), as I need it (along with an older XGA display unit) to substitute for the remote terminal I would normally use; apparently not too many customers of Acer Computer specified the serial-port option in the EL1210, although the DA078L planar is prepared for a serial port (pinout for DE-9 consistent with an EIA-571 hookup adjacent to the DE-15 for the VGA/XGA output).  Although I have some experience setting the graphic boot to Debug with a single GPU in GNU Grand Unified Bootloader, so far my attempts to engage it on the EL1210 have resulted in KSOD's; the install requires tweaking BIOS settings to install Ubuntu® 16.01a2 with the Primary Display in BIOS set to PCIEx (for the GP119) for installation and upgrade, before setting Primary in BIOS to Onboard (for the C77) for what should be normal operation.  Any help debugging procedures would be appreciated.

---

### Post by gordintoronto on 2016-02-12
I assume you meant Ubuntu 16.04 alpha 2. You should be aware that this is a testing environment, not meant for production work. It breaks, you report it, it gets fixed.

Other than that, it's not obvious to me how serial ports relate to video adapters.

On an 8-year-old system you might consider something other than Ubuntu. My choice has been Xubuntu 15.10.

---

### Post by bcschmerker on 2016-02-13
To date, I have not been able to find a fully-optioned Acer® DA078L, viz., one with a functional EIA-571 port (surface-mount UART compatible with National Semiconductor®/Texas Instruments® NS16HC650MA, DE-9 above DE-15 at rear panel) and operational IEEE 1284 header (2x13-pin, uses ribbon cable to connect to a DB-25 somewhere in the case); also, 16.01a2 KSOD's on any attempt to use the planar nVIDIA® C77 as a terminal.  I cannot guarantee that an add-on PCIe UART will function properly to monitor the Kernel from the moment GRUB calls it.

**Update:**  I am investigating what graphics processing units OpenLP® 2.*n*.*m* can drive natively, unassisted by X11, as part of a new contingency for an add-on PCIe 2.0 x1 serial card; the planar C77 is detected offline, with the GF119 able to run up to two displays in X11.  StarTech® has several low-profile serial and serial-parallel interface cards in production; I'm after a model that can run its DE-9's remotely, as the bolted-on DE-subminiature hole is needed for the N610GT's DE-15 subharness.

**Update 2:**  Negative on GPU's native for OpenLP® 2.4.*n*, which depends on X11.  Looks, additionally, as though I'll have to install a half-height PCIe x1 dual serial adapter, pending information on the asynchronous-port hardware intended for the DA078L Boxer.

---

