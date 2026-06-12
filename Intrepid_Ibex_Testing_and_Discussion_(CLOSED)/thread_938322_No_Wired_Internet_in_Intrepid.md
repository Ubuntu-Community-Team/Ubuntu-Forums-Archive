---
title: "No Wired Internet in Intrepid"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by u-slayer on 2008-10-04
I'm trying to install Intrepid onto my laptop. I can see the wireless network, but I can't see or connect to the wired network in the house. My laptop is a Toshiba Satellite M105-S3004.

```
$cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by Sef on 2008-10-04
Moved to Ibex forum.

---

### Post by nanog on 2008-10-04
if you have an ich8 or ich9 chipset your e1000e driver has been disabled due to this bug:  

[http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

lspci | grep 8256[67]

will tell you if you have this card

the solution is to install a new kernel:

[http://ubuntuforums.org/showpost.php?p=5907023&postcount=64](http://ubuntuforums.org/showpost.php?p=5907023&postcount=64)


I think you network interface should look like this by default:

```

~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by inportb on 2008-10-04
> **nanog said:**
> I think you network interface should look like this by default: <snip>

Not really... it hasn't been so since Gutsy. NetworkManager is able to manage your network devices automatically. The default config file now seems to be just:

```
auto lo
iface lo inet loopback
```

---

### Post by zoomy942 on 2008-10-04
so mine looks like this

```
 zimmerman@ubuntu-tablet:~$ lspci | grep 8256[67]
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
zimmerman@ubuntu-tablet:~$ 

```

i ask because my ethernet isnt working

---

### Post by Mr Fredrick on 2008-10-04
I also cannot see or connect to my wired network.

I am using the 2.6.27-4 kernel.

If I run nm-applet I get:

```
** (nm-applet:7649): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7649): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

and if I run lspci -knn I get:

```
peter@peter-laptop:~$ lspci -knn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1)
	Kernel modules: nvidiafb
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Kernel driver in use: tg3
	Kernel modules: tg3
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
```

From the above it appears that I shouldn't be affected by the Intel e1000e driver bug.

Mr Fred

---

### Post by u-slayer on 2008-10-04
> **nanog said:**
> if you have an ich8 or ich9 chipset your e1000e driver has been disabled due to this bug:  

[http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

lspci | grep 8256[67]

will tell you if you have this card


lspci | grep 8256[67] does not return anything

I looked through my lspci manually and I found an entry:

```

Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```

So I would assume that I do not have the e1000e driver you speak of.

---

### Post by inportb on 2008-10-04
That's a faulty assumption, because some drivers support more than one piece of hardware. It would be better to assume that your hardware *does* depend on the e1000e driver, and that it would be unsafe to remove it off the blacklist.

There's a temporary fix from Intel, it appears:
[http://lkml.org/lkml/2008/10/1/368](http://lkml.org/lkml/2008/10/1/368)

---

### Post by andylinux on 2008-10-28
I'm having the same problem.  I just upgraded from hardy to intrepid RC and have no networking at all,  No wired or wireless.

If I add these lines to my /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet dhcp

and then restart my network,
/etc/init.d/networking restart

I get a wired ip address.  

Seems like this is a bug with network manager.

Everything works fine if I boot the live CD
I have a Broadcom BCM5752 Gigabit Ethernet and Interl 3945 ABG wireless.

---

