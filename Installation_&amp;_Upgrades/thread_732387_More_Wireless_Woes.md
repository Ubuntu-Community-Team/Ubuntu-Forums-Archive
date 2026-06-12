---
title: "More Wireless Woes"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by m_cubed on 2008-03-22
h'okay so here's the problem:
I'm trying to dual boot Vista and Ubuntu 8.04
I used to run Fiesty Fawn on this same laptop, so I'm somewhat familiar with Ubuntu.  The reason I deleted the Ubuntu partition and stuck it out with Vista is because my wireless card never worked and that's the main way I connect to the internet

-lspci tells me that my card is a 
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) card

i've installed bcm43xx-fwcutter_006-4_i386.deb, ndisgtk_0.6-0ubuntu1_all.deb, and ndiswrapper-utils_1.8-0ubuntu2_i386.deb and ran them... to no avail

I used bcmwl5.inf with ndisgtk and it tells me that this is an invalid file (the hardware is not present according to the gtk screen)

What .inf file should I use? Where do i go from here? :confused:

btw I used wubi to install this installation... i didn't want to fight with partitioning AGAIN

---

### Post by Pumalite on 2008-03-22
Did you install 8.04?

---

### Post by m_cubed on 2008-03-22
yes it is installed and running fine, but I have no internet while in Ubuntu...

---

### Post by Pumalite on 2008-03-22
Well, my laptops are Apple, but I have a couple of links that you can review:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

---

### Post by Powerman2442 on 2008-03-22
I used a program I found in one of these forum posts. I've looked for 15 minutes now and can't find it. If you want it feel free to PM. In the meantime, if I find it I will let you know where.

---

### Post by m_cubed on 2008-03-23
Yea so the bcm43xx driver method didn't work... Now I'm going to try to use the ndiswrapper on the XP drivers and see where that gets me.

By the way while trying the bcm43xx method in the first link, it told me that bcm43xx drivers were depricated... maybe that's why it didn't work?

---

### Post by m_cubed on 2008-03-23
So when i tried to install with the windows drivers everything installed fine, but when I was finished, the wireless card won't turn on or work... ](*,)

If it will help, I'm running a Compaq Presario C500 w/ 1 Gig of RAM, Dual Core 1.73 GHz processors, with an 80 Gig hard drive...

This is what I get for buying a $500 laptop :(

---

### Post by dstew on 2008-03-23
> So when i tried to install with the windows drivers everything installed fine, but when I was finished, the wireless card won't turn on or worPost the output of ```
ndiswrapper -l
```

---

### Post by Pumalite on 2008-03-23
[http://ubuntuforums.org/showthread.php?t=594368](http://ubuntuforums.org/showthread.php?t=594368)

---

### Post by m_cubed on 2008-03-23
> **dstew said:**
> Post the output of ```
ndiswrapper -l
```

```
serenity@serenity-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

```

If it helps here's the output of 
```
 lspci 
```
```
serenity@serenity-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 


```



UPDATE:
I tried the instructions in that last forum to no avail... the wireless card still won't turn on... though I did find out that bcm43xx has been blacklisted all along... maybe that's why it didn't work the first time?

---

### Post by cetol on 2008-03-23
what is the output of ```
dmesg
```?

---

### Post by m_cubed on 2008-03-23
> **cetol said:**
> what is the output of ```
dmesg
```?


You're a genius man... but what exactly does dmesg do?
Here's the important section of the output...

```

[   40.873699] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   40.896421] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   40.896451] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   40.932664] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   40.932703] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   41.107604] b43-phy0: Broadcom 4311 WLAN found
[   41.173639] phy0: Selected rate control algorithm 'simple'
[   41.808446] lp: driver loaded but no devices found
[   41.883962] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   41.973289] usbcore: registered new interface driver ndiswrapper
[   42.455737] EXT3 FS on loop0, internal journal
[   46.046626] Adding 195304k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:51 across:67576880k
[   46.462923] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.942797] No dock devices found.
[   48.728744] apm: BIOS not found.
[   48.938490] ppdev: user-space parallel port driver
[   50.501910] eth0: link down
[   50.609836] input: b43-phy0 as /devices/virtual/input/input8
[   50.653976] Bluetooth: Core ver 2.11
[   50.654516] NET: Registered protocol family 31
[   50.654521] Bluetooth: HCI device and connection manager initialized
[   50.654530] Bluetooth: HCI socket layer initialized
[   50.682781] Bluetooth: L2CAP ver 2.9
[   50.682791] Bluetooth: L2CAP socket layer initialized
[   50.746363] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   50.746372] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   50.758515] Bluetooth: RFCOMM socket layer initialized
[   50.758534] Bluetooth: RFCOMM TTY layer initialized
[   50.758536] Bluetooth: RFCOMM ver 1.8
[   52.509190] input: b43-phy0 as /devices/virtual/input/input9
[   52.581730] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   52.581747] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   53.632754] [drm] Initialized drm 1.1.0 20060810
[   53.634936] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   53.634946] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   53.635023] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   64.108221] NET: Registered protocol family 10
[   64.108816] lo: Disabled Privacy Extensions
[   64.109956] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.189001] input: b43-phy0 as /devices/virtual/input/input10
[   64.284780] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   64.284788] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   71.669218] CPU0 attaching NULL sched-domain.
[   71.669225] CPU1 attaching NULL sched-domain.
[   71.688917] CPU0 attaching sched-domain:
[   71.688923]  domain 0: span 03
[   71.688925]   groups: 01 02
[   71.688928] CPU1 attaching sched-domain:
[   71.688930]  domain 0: span 03
[   71.688932]   groups: 02 01
[   81.308106] input: b43-phy0 as /devices/virtual/input/input11
[   81.397767] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   81.397776] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).

```

Now exactly what do I need to download while in windows to fix this?

---

### Post by cetol on 2008-03-23
This may be obvious but it looks like eth0 is down. I'd try ```
ifup eth0
``` BTW dmesg shows the kernel messages Also it still shows the b43 module is still loading. Add it to /etc/modprobe.d/blacklist

---

### Post by m_cubed on 2008-03-23
should I try to follow the instructions on
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old) ?
it seems to be telling me to try to install the b43 firmware which replaces the deprecated bcm43xx drivers...

---

### Post by cetol on 2008-03-23
I personally have not had very good luck using the firmware drivers for broadcom. IF you can get them to work, my experience is that they do so at about 1/2 the bandwidth. I downloaded the windows drivers from HP (I have a compaq laptop) and started the install in windows, except when it came to the part where the installer asks where to extract to instead of the "C" drive I used a usb pen drive. That way when it came time to provide the driver to ndiswrapper I just copied the drivers from the usb drive to my home folder.

---

### Post by cetol on 2008-03-23
Also this thread has some great info in it

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

---

### Post by pprjack on 2008-04-27
This is just the sort of thing that discourages me from wholehearedly adopting Linux as my OS of choice. This wireless card worked for me "out of the box" on Gutsy. Now I have upgraded to the new "HARDy" only to discover the true meaning of the name. Why should I have go through this pain just to use my computer? 
Going back to Gutsy, bad taste in mouth!

---

