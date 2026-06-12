---
title: "Lots of unknown devices, is that a problem?"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by jespdj on 2006-09-13
I have a brand new PC:

Intel Core 2 Duo E6600
Asus P5B Deluxe motherboard (with Intel P965 chipset)
Asus video card with ATI X1600XT, 256 MB video memory
2 GB RAM
320 GB Seagate SATA-2 harddisk
Sony dual layer DVD writer (IDE/ATAPI)

I'm running Windows XP Home Edition and Ubuntu 6.06.1 AMD64 on it. I have two problems with Ubuntu: (1) Networking does not work, (2) the clock runs much too fast. I don't know why networking doesn't work (it does recognise the adapter eth0, there seems to be a problem with DHCP?). According to other posts I found, the clock problem is a kernel bug, but I can't update my kernel if I can't use Internet, so I want to solve the network problem first.

Ok, but what I want to ask here is this: if I look at the list of devices with lspci, I see there are lots of unknown devices:
```

0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 02)
0000:00:1c.5 PCI bridge: Intel Corporation: Unknown device 2849 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2810 (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2820 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2825 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c0
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 71e0
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)
0000:03:00.0 IDE interface: Unknown device 197b:2363 (rev 02)
0000:05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```
Are all those unknown devices a problem? USB devices (mouse, keyboard, USB stick) seem to work fine even though the USB devices show up as unknown devices.

Do I need to update device drivers? If so, how do I do this?

---

### Post by orb9220 on 2006-09-13
No those are devices that do not have an identifier string in the devices firmware.

Just like in windows when you view properties of a device driver  and under some info tabs are blank because the manufact are lazy and leave the info out.

I wouldn't worry about it I think everyone has unknown on thier system,

---

### Post by jespdj on 2006-09-13
Well, I searched a bit further and found this: [Linux PCI ID Repository](http://pciids.sourceforge.net/).

That's a place where the pci.ids file is maintained. I downloaded the latest pci.ids file and replaced it in all places where I could find it on my system:
```

jesper@jesper-desktop:~$ sudo find / -name pci.ids
/var/lib/misc/pci.ids
/usr/share/hwdata/pci.ids
/usr/share/lshw/pci.ids
/usr/share/misc/pci.ids

```
And now I don't have any unknown devices anymore:
```

0000:00:00.0 Host bridge: Intel Corporation P965/G965 Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation P965/G965 PCI Express Root Port (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
0000:00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
0000:00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
0000:01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
0000:03:00.0 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
0000:05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```
Note: I added the ID for the Marvell Yukon 88E8056 PCI-E Ethernet Controller myself. Unfortunately that doesn't make it work :( ... [my thread about this problem](http://ubuntuforums.org/showthread.php?t=256867).

---

