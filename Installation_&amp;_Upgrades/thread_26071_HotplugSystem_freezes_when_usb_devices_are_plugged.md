---
title: "Hotplug/System freezes when usb devices are plugged"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by ridvan on 2005-04-11
Both during the installation initialization and after installation
the system freezes if you ever plug an usb device.

I have experienced the problem first during installation initialization,
then as I turned on an usb printer.

The system neither boots nor works with an usb peripheral.

Any ideas?

---

### Post by alastair on 2005-04-11
Boot normally (no USB).

Open a shell and :

sudo tail -f /var/log/syslog

Then plug in a USB device (tell us what) and see what happens (kernel messages). If you can, post them.

It might be an idea to post the syslog (from boot until hang).

---

### Post by ridvan on 2005-09-07
I have done it but could not see any response/message, because hoary hangs up immediately.
The output of lspci is as follows
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:09.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

---

