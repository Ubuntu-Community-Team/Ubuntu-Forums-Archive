---
title: "Problems with Intel Graphics card"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by ryanwalex on 2011-01-09
I having problems with my intel graphics card. Boxee and XBMC don't work as well as I can not use extra visual effects on the desktop. I have ubuntu 10.10.

I can't find a good way to install the driver. I will have to switch back to windows if I can't solve this. 

Computer Config:
[SIZE=2]HP Pavilion 06 DB229A[/SIZE]
[SIZE=2]Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
1.5gb ram
using vizio TV as monitor
[/SIZE][SIZE=2]2.53 gigahertz Intel Pentium 4[/SIZE]
[SIZE=2]
[/SIZE]lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

### Post by coffeecat on 2011-01-09
Not entirely satisfactory because you may get system freezing, but see here:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by jcolyn on 2011-01-09
Why not do what I did with my HP with Intel 8xxx graphics card. Install a new Nvidia pci card with 512MB video ram and disable the onboard card..

---

### Post by ryanwalex on 2011-01-09
> **jcolyn said:**
> Why not do what I did with my HP with Intel 8xxx graphics card. Install a new Nvidia pci card with 512MB video ram and disable the onboard card..

Why spend the money when I can switch back to Windows and it will work properly? I am mostly using Ubuntu as I want it to load quickly.

---

### Post by ryanwalex on 2011-01-09
> **coffeecat said:**
> Not entirely satisfactory because you may get system freezing, but see here:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Thank you, but this did not seem to work. I got a blank screen when I rebooted. I tried rebooting several times with the same result. I think it means it was not processing the video card correctly with this fix.

---

### Post by ronnielsen1 on 2011-01-09
> Why not do what I did with my HP with Intel 8xxx graphics card. Install a new Nvidia pci card with 512MB video ram and disable the onboard card..

Yeah, if the bios that Dell chose to use LETS you disable onboard video. Mine doesn't

> Why spend the money when I can switch back to Windows and it will work properly? I am mostly using Ubuntu as I want it to load quickly.

If you learned linux, you would know the reason for this

---

### Post by ryanwalex on 2011-01-13
My lspci lists my VGA Intel graphics card. Does this mean it is installed with the correct driver?

---

