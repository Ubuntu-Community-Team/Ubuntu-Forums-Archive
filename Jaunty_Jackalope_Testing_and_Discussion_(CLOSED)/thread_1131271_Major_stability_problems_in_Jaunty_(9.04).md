---
title: "Major stability problems in Jaunty (9.04)?"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Lowell Alleman on 2009-04-20
Has anybody else been seeing random crashes and lockups using (k)ubuntu Jaunty?  I upgrade from Hardy to Intrepid to Jaunty within the last month.  Intrepid had some nasty KDE problem for me, but Jaunty seems great, except that it seems really flaky...

Here are some of the things I've seen so far:
[LIST]
[*]I've run into many hard lockups.  (No X response, no ping reply, no response from Num/scroll lock keys).  I've had this happen within minutes after booting. Seems to always happen when I am moving the mouse.
[*]I've had a few times where X makes my LCD fade to white; which I've never seen on this laptop before.  (I used to get this on my old DELL (r128 ).. but I haven't had this problem in years...).  This is pretty much a hard-lockup too.
[*]I've had a couple of weird X lockups where the mouse works, and I can connect via SSH but whatever I tried, I can't kill/stop the Xorg process.  I think that Xorg uses very high CPU utilization during this time.  The "reboot" command wouldn't cause the system to completely shutdown, I've had to hold down the power button...
[/LIST]

I've found that booting to by old kernel (2.6.27-11-generic) seems much more stable, but also a bit slower.

I would gladly report a bug, but I really don't have any details to report.  A generic crash with no log messages isn't really helpful.  But even with the older kernel I've still run into some crashes.  With seem to be X-related.

I've installed and enabled the watchdog service on my system (iTCO_wdt) but it doesn't actually reboot during a hard-lockup.

Any ideas or similar experiences?

Here is some info about my hardware.  I'm running an IBM T42, 1.7Ghz with 1535MB of memory.  My Video card is a Radeon 9600 M10.

output from lspci:
```

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
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

---

