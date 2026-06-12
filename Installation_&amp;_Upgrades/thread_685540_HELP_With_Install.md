---
title: "HELP With Install"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by dlee2011 on 2008-02-02
I just put Ubuntu Gusty Gibbon on my friend's laptop. The wireless card is restricted and i can't install it because i can't get on the internet. i downloaded it manually, but i have no clue on how to install it... Please Help

---

### Post by jan quark on 2008-02-02
pls post the result of the terminal command

```
lspci
```

this displays the devices and also the exact name of the network device

---

### Post by dlee2011 on 2008-02-02
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Pumalite on 2008-02-02
[http://www.google.com/search?hl=en&q=ubuntu+and+Broadcom+Corporation+BCM4318+%5BAirForce+One+54g%5D+802.11g+Wireless+LAN+Controller+%28rev+02%29&btnG=Google+Search](http://www.google.com/search?hl=en&q=ubuntu+and+Broadcom+Corporation+BCM4318+%5BAirForce+One+54g%5D+802.11g+Wireless+LAN+Controller+%28rev+02%29&btnG=Google+Search)

---

### Post by dlee2011 on 2008-02-02
So i guess im SOL

---

### Post by zvacet on 2008-02-02
Read [this](http://ubuntuforums.org/showthread.php?t=197102).

---

