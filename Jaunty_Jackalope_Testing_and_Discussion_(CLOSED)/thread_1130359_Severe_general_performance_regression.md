---
title: "Severe general performance regression"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sambarluc on 2009-04-19
Hi everybody,
I just installed Jaunty on my Thinkpad T41, but I am experiencing a strong performance loss in all tasks except booting, which is indeed much faster than before. In general, everything seems to work (apart from some problems with with Atheros 5k driver, which I see is rather common around the community). Anyway, everything has become painfully slow, and Firefox is the worst.
Anybody else experiencing something like this?

---

### Post by paradigm2 on 2009-04-19
> **sambarluc said:**
> Hi everybody,
I just installed Jaunty on my Thinkpad T41, but I am experiencing a strong performance loss in all tasks except booting, which is indeed much faster than before. In general, everything seems to work (apart from some problems with with Atheros 5k driver, which I see is rather common around the community). Anyway, everything has become painfully slow, and Firefox is the worst.
Anybody else experiencing something like this?

What are you getting for cpu and memory usage (as well as total of each installed)?

What do hardware have you?

'lspci'

-- some of the intel based graphic cards are particularly having performance issues.

---

### Post by gnomeuser on 2009-04-19
How are you measuring this performance loss?

---

### Post by sambarluc on 2009-04-20
The performance loss is general and evident. With the system monitor, I see that it's due to CPU overloaded even with simple tasks like switching from a window to another.

Here is my lspci:
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
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by psyke83 on 2009-04-20
Does your ATI card use the open source driver or fglrx?

If you're using the open-source driver, EXA may be the culprit. Try some tweaks to see if it helps.

Edit your xorg.conf:
```
$ gksudo gedit /etc/X11/xorg.conf
```

Make your "Device" section look like the following (and delete any customizations you've made):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"		"exa"
	Option		"AccelDFS"		"true"
	Option		"EXAOptimizeMigration"	"true"
	Option		"MigrationHeuristic"	"greedy"
EndSection
```

Restart X and see if general performance is better.

---

