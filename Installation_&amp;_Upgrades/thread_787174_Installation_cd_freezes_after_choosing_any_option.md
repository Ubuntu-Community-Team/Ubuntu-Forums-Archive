---
title: "Installation cd freezes after choosing any option"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by xbill82 on 2008-05-08
Hello everybody on the Forum,
I have a 8.04iso I have successfully checked with md5sum and successfully burnt into a cd and which successfully booted on my VAIO VGN-c2s laptop.
The installation program starts and allows me to choose the language, so I do it but when I chose any of the options it shows me (try ubuntu, install it, check the cd, check the memory, blah blah blah) it stucks on any option you chooose.
It's weird because it doesn't seem a windows-like blue screen hook up... because the pc starts reading on the cd and that's it, it does nothing more.
It just keep on reading the cd during hours and it doesn't react to anything you do except from the ctrl+alt+del combination which actually reboots the pc.
This makes me think that the pc isn't really stuck.
Is this normal? How much should I be waiting before the installation starts after choosing the corresponding option?

Thank you for your help!

Luca;)

---

### Post by Pumalite on 2008-05-08
Post your specs. You might need the Alternate CD.

---

### Post by xbill82 on 2008-05-12
I tried it on my Sony VAIO VGN-C2s and several other laptops based on the same chipset. I recently tried it on my AMD Athlon 1300 Mhz and same thing.
My laptop's lspci is

```

vaioluca xbill # lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Thanks for the help!

Luca;)

---

### Post by Pumalite on 2008-05-12
Install with the Alternate CD.

---

