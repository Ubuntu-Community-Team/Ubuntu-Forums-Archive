---
title: "Internal Mic.. Works, but very muffled.."
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by IndyGunFreak on 2010-04-17
Well, I finally hit an issue w/ Lucid... My Internal Mic has never worked previously at all.  It now works, but is VERY muffled.  Volume/Mic volume all the way up and I can only hear when I yell or am very loud.  Mic-Jack still seems to work fine, but was hoping to lose the mic(actually, I did lose the mic.. thus why I was trying to get the internal working :))

IGF

```
ken@ken-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
ken@ken-laptop:~$ 

```

---

### Post by psyke83 on 2010-04-18
Open alsamixer from a terminal, and see if there are any controls you can tweak - my card has a "mic boost" control, for example.

---

### Post by mudi on 2010-04-18
On my internal mic, it is actually a mono mic but Ubuntu detects it as a stereo mic.  When both channels are turned all the way up, it doesn't work... but if I turn the right channel volume all the way down it starts working.

This is in Karmic, I haven't tested this particular computer in Lucid yet.

---

### Post by IndyGunFreak on 2010-04-18
> **psyke83 said:**
> Open alsamixer from a terminal, and see if there are any controls you can tweak - my card has a "mic boost" control, for example.

I guess I should have mentioned I checked all that... The problem is, when I raised the levels on the mic, it started getting a TON of static... It was strange, it would go from just barely static(but still muffled), to sounding like like a TV w/o a signal... Oh well, worst comes to worst, I'll pick up another cheap headset/mic...

IGF

---

