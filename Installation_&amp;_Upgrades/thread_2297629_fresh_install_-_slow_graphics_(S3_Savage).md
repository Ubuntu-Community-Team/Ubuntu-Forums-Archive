---
title: "fresh install - slow graphics (S3 Savage)"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by elsni on 2015-10-05
Hi,

I installed recent lubuntu 15.04 on an old Thinkpad t23 with 1gig RAM. Graphics is unusable slow, the chip is an S3 SuperSavage IX/C SDR (rev 05)
I already created an xorg.conf, but savage was already set for the driver. What can I do next?

Thanks for any advice!

Machine details:

```
00:00.0 Host bridge: Intel Corporation 82830M/MG/MP Host Bridge (rev 04)
        Subsystem: IBM ThinkPad A/T/X Series
        Kernel driver in use: agpgart-intel
00:01.0 PCI bridge: Intel Corporation 82830M/MP AGP Bridge (rev 04)
00:1d.0 USB controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Kernel driver in use: uhci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
        Kernel driver in use: lpc_ich
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: IBM ThinkPad A30/A30p/T23
        Kernel driver in use: snd_intel8x0
01:00.0 VGA compatible controller: S3 Graphics Ltd. SuperSavage IX/C SDR (rev 05)
        Subsystem: IBM ThinkPad T23
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
        Subsystem: IBM ThinkPad T23
        Kernel driver in use: yenta_cardbus
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
        Subsystem: IBM ThinkPad T23
        Kernel driver in use: yenta_cardbus
02:02.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Texas Instruments Device 9069
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
        Subsystem: IBM ThinkPad A/T/X Series
        Kernel driver in use: e100

```

---

### Post by tgalati4 on 2015-10-05
You can draw your graphics quicker with sidewalk chalk.  The T23 is an old machine and S3 graphics were never known for speed.  With only 1 GB of RAM, you will be hitting swap often when browsing and that will slow things down.  I would try 14.04 MATE and see how that runs.

---

