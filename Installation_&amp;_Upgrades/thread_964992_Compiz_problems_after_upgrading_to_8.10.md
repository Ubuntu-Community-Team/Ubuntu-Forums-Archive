---
title: "Compiz problems after upgrading to 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by almos.dinnyes on 2008-10-31
Last night I upgraded from 8.04 to 8.10, and compiz doesn't work well any more :(

If I start compiz all window frames (window decoration) disappear.

I tried to reinstall compiz, to reload it, to switch off the window decoration effect, but no success. Only metacity works.

I have an Acer Travelmate 6292 with Intel 965 chipset:
[I]lspci -v

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0, IRQ 6
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3
[/I]

and here is my xorg.conf
[I]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	InputDevice	"Synaptics Touchpad"
EndSection[/I]

What shall I do to make compiz working again?

---

### Post by almos.dinnyes on 2008-11-01
No ideas? I am the only one with this problem?

---

### Post by Kevbert on 2008-11-01
It may be worth trying [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") as it may just be something like a blacklisted driver (or even the wrong driver for your card). I notice you have no driver set in your xorg.conf file, so you must be using the inbuilt driver that comes with Intrepid.

---

### Post by almos.dinnyes on 2008-11-01
Thanks! Here is the result:

 ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

I just made an upgrade from 8.04. If I know well I had the built-in driver before as well. Shall I change it? If so, how?

---

### Post by Kevbert on 2008-11-01
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=8304&highlight=GM965%2FGL960") on the compiz forums.

---

### Post by almos.dinnyes on 2008-11-01
Thanks! I was suggested to upgrade the libgl1-mesa-glx, but I don't know how. If I try to remove Synoptic wants to remove the whole gdm environment. Can you help me?

---

### Post by Kevbert on 2008-11-01
> **almos.dinnyes said:**
> Thanks! I was suggested to upgrade the libgl1-mesa-glx, but I don't know how. If I try to remove Synoptic wants to remove the whole gdm environment. Can you help me?

It's been suggested that you try this in terminal:
```
sudo apt-get -f install libgl1-mesa-glx
```
The '-f install' is a force install and there seems to be some problems and [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/196823") reports on upgrading this file.

---

### Post by almos.dinnyes on 2008-11-01
Thanks! It's solved! :)
[http://forum.compiz-fusion.org/showthread.php?p=67709#post67709](http://forum.compiz-fusion.org/showthread.php?p=67709#post67709)

---

