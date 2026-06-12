---
title: "Problems with resume from suspend"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chuckyp on 2010-02-13
Just wondering if anyone else is experiencing problems with resume from suspend?
When I open my laptop lid the screen won't power back on after suspend. This behavior started with I believe kernel 12 unless there was an intel video update in between. I'll post the output of lspci below. I'm also going to try booting an older kernel and seeing if that helps.

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

---

### Post by chuckyp on 2010-02-13
Okay I stand corrected. It will resume from suspend if I select suspend from the power menu. However, It will not turn the monitor back on after closing the lid. In power options it set to go to suspend when the lid closes. I've watched the lights and it does not enter suspend mode when the lid is put down. Power light stays solid green and monitor powers off. When you open the lid no display and you can't wake it. You have to hard reset. Dell Inspiron 6000.

---

### Post by code850 on 2010-02-13
Same here, suspend and resume works perfect if triggered from logout icon. However, when i close  the  lid system suspend and it resumes after opening the lid but the screen is dead. I have intel 855GM graphics  card.

---

### Post by lonniehenry on 2010-02-13
I have similar problem.  Workaround is ctrl-alt-f1 followed by alt-f7.  that should turn on screen.

---

### Post by code850 on 2010-02-14
Ctrl+Alt+F1 followed by Alt+F7 triggers suspend/hibernate again. Weird.

---

