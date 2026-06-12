---
title: "ndisgtk problems"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-06-23
Hello,
Tried Karmic, did my usual ndisgtk installation, installed the drivers by using the wireless .inf file, and it says "hardware could not be found" (or something to that extent) but after I click the okay button it says that it has installed, yet the wireless functionality doesn't actually work.

I'm using an Fujitsu-Siemens Amilo li1818 laptop by the way, also I didn't post this into the generic wireless section because seeing as this works under Jaunty and all previous versions, and the fact that I'm trying Karmic now, I thought this would be the most suitable forum to post this topic in.

Many thanks to anyone who has any clues about this etc,

Lee Jarratt

---

### Post by go7Ul1ai on 2009-06-25
Anyone?

---

### Post by taavikko on 2009-06-25
Would be easier to tell if you'd supplied us the information of the wireless hardware in question. Fujitsu {insert model here} is a little too generic ;)

If using broadcom chipset have you tried using
bcmwl-kernel-source ? 

As devel goes onward, fewer chips require the windows driver??

---

### Post by go7Ul1ai on 2009-06-25
Okay it's the sis163u wireless card (well at least the driver I use is the sis163u.ing one, which I got from my drivers cd) , i'm using an intel integrated chipset.

---

### Post by descendent87 on 2009-06-25
Girlfriends got a Fujitsu Amilo li2727 (don't know if it's the same wireless, hers is atheros ar242x or something like that) and only way to get it working was by following [this guide](http://ubuntuforums.org/showthread.php?t=986288)
If you type "lspci" in a terminal it will tell you all the parts in the laptop, if it's an atheros ar242x wireless card then try that guide

---

### Post by go7Ul1ai on 2009-06-25
This is what I get:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

Lee

---

### Post by taavikko on 2009-06-25
lspci doesn't show your wireless card...
Does 
"lsusb" show anything? Or "lshw -C network"

Haven't come across to any SiS hardware so really cannot be any assistance in that. And don't really know if linux wireless tree carry those drivers...

---

### Post by go7Ul1ai on 2009-06-25
> **taavikko said:**
> lspci doesn't show your wireless card...
Does 
"lsusb" show anything? Or "lshw -C network"

Haven't come across to any SiS hardware so really cannot be any assistance in that. And don't really know if linux wireless tree carry those drivers...

Thanks for your help, and any in the future,

here is the results for "lsusb":

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Compute
```

And the results for "lshw -C network"

```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:6e:18:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0

```

Note I'm doing this using Jaunty, as I can't use Karmic for wireless at the moment.

Lee

---

