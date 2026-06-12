---
title: "Can't watch 1080p youtube stream, I can under Windows"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jochem on 2010-03-23
I guess this isn't really a bug, and I'm probably using the correct drivers, but I was wondering if there is any way I could improve the performance? 

When playing 1080p flash movies, my CPU load is 100%, and it only shows like 3 frames per second. Under windows, my CPU load is also 100%, but it doesn't nearly skip as many frames.

I'm using the 64 bit version 10.1 flash plugin. Hardware acceleration is checked.

Could someone help me checking if I'm using the correct drivers, or give me tips to improve the flash performance, or video performance in general?

EDIT:
I'm using an acer 1810tz
cpu: ULV SU4100
gpu: intel 4500HMD
chipset: intel GM45

lspci:

jochem@jochem-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
jochem@jochem-laptop:~$

---

### Post by Lollerke on 2010-03-23
Under Linux there's no hardware acceleration in Flash. In the Windows version, Flash uses your graphics card.

---

### Post by jochem on 2010-03-23
> **Lollerke said:**
> Under Linux there's no hardware acceleration in Flash. In the Windows version, Flash uses your graphics card.

Thanks for your reply, so there's no way I could force flash to use my graphics card?

---

### Post by Lollerke on 2010-03-23
Flash can't use your graphics card. It's a Windows only feature.

---

