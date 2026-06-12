---
title: "last update broke wifi+touchpad"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by Mtmayr on 2013-10-05
The last update (to kernel 3.2.0-54) broke my wifi and my touchpad on my old laptop: Acer Travelmate 291 LMI.
Last working kernel is:
Linux nemo 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux

Best wishes
Mtmayr

Hardware List:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
```

---

### Post by varunendra on 2013-10-07
Welcome to the forums Mtmayr !

Please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
nm-tool
dmesg | egrep 'wlan|iwl|firm'
```
..for wifi.

For touchpad, only the output of -
```
xinput
``` for now.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

