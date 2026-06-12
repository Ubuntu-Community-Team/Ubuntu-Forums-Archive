---
title: "Karmic shutdown failure on IBM Thinkpad T40"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-05-27
"quiet splash" boot is screwed up on several counts, the USB mouse doesn't work, the USB keyboard doesn't work, screen is half bright, ... most importantly shutdown hangs.

Removing "quiet splash" or booting in "recovery mode", boot is fine, USB devices detected and usable, screen brightness as usual, shuts down nice and quick.

Been chasing this bug on the T40 for a while.  Karmic is running without this problem on my Thinkpad R31, ThinkCentre A30, Compaq Presario.

Launchpad bug #381134.

Cheers, Jerry

---

### Post by lucazade on 2009-06-05
Hi!
Same issue here on my T40.

Linux luca-laptop 2.6.30-8-generic #9-Ubuntu SMP Wed Jun 3 15:23:55 UTC 2009 i686 GNU/Linux

---

### Post by phenest on 2009-06-05
I have that issue on a Dell. Disabling the wireless with the hardware switch allows proper shutdown. If this works, the bug is reported.

Bug: [379976]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379976")

---

### Post by linux6994 on 2009-06-06
I have an IBM T40 also and loading the latest kernel allows my shutdown and startup to work well without using recovery mode.

Linux dad-laptop 2.6.30-8-generic #9-Ubuntu SMP Wed Jun 3 15:23:55 UTC 2009 i686 GNU/Linux

dad@dad-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
dad@dad-laptop:~$

---

### Post by lucazade on 2009-06-06
We have different eth0 and wifi controllers:

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

maybe my issue is related to these cards..

---

