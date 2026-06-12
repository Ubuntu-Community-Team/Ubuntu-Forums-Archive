---
title: "Wireless not functional on upgrade"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by theronmuller on 2011-11-07
I recently upgraded my HP Pavilion dv7 from Ubuntu 11.04 to 11.10, and now the wireless isn't functional. There's no way to control it from the networkmanager applet.

"sudo lshw -C network" returns:```

  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3000000-d300ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 64:31:50:5f:b7:58
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.24.86 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:d1004000-d1004fff memory:d1000000-d1003fff memory:d1010000-d101ffff

```

I've already changed /etc/NetworkManager/NetworkManager.conf to "managed=true", but that didn't do the trick. Wireless was working fine in 11.04, so any advice regarding how I should proceed would be welcome.

---

### Post by ratcheer on 2011-11-07
Please post the Ralink wireless section from the output of "sudo lspci -v".

Tim

---

### Post by theronmuller on 2011-11-08
Ratcheer,
Thanks for your quick response. Here you are:
```
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Hewlett-Packard Company Device 1453
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d3000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-00-43-e5-17-82-2a-e0
	Kernel modules: rt2800pci
```

---

### Post by ratcheer on 2011-11-08
Ok, so the card is detected by the system and the rt2800pci driver is selected for it. However, no module is "in use".

I do not know what is the right thing to do, but my Ralink wireless card does not work well at all with rt2800pci, which is supposed to be the correct driver. I went to the Ralink website and downloaded and installed their recommended driver, and now my wireless works very well. I also blacklisted rt2800pci.

I hope this helps.

Tim

---

### Post by theronmuller on 2011-11-08
Tim,
Thanks for your reply. You got me pointing in the right direction. I had added rt2800pci to /etc/modprobe.d/blacklist.conf 2010-11-13 when I installed Ubuntu 10.04, so with the upgrade whatever was driving my wireless must have been removed and rt2800pci wasn't there as a fallback because it had been blacklisted. Removing that line from /etc/modprobe.d/blacklist.conf has my wireless working fine now.

Thanks again!

---

### Post by ratcheer on 2011-11-08
You are welcome. I am glad rt2800pci works for you. I have never been able to get it to work for me.

Tim

---

### Post by moteprime on 2011-11-09
ratcheer, are you on 11.04, I had luck getting rt3090 to work on 11.10.
Se post #20 in this, now long thread:
[http://ubuntuforums.org/showthread.php?t=1849602&highlight=rt3090&page=2](http://ubuntuforums.org/showthread.php?t=1849602&highlight=rt3090&page=2)

---

### Post by ratcheer on 2011-11-09
> **moteprime said:**
> ratcheer, are you on 11.04, I had luck getting rt3090 to work on 11.10.
Se post #20 in this, now long thread:
[http://ubuntuforums.org/showthread.php?t=1849602&highlight=rt3090&page=2](http://ubuntuforums.org/showthread.php?t=1849602&highlight=rt3090&page=2)

No, I am on 11.10. I have had to use the Ralink rt2860 driver on Natty and Oneiric. It is the Linux-supplied rt2800pci driver that does not work for me.

**Does rt2800pci work for anyone?** I see many, many bugs reported on it not working, but it never seems to get fixed. What is this driver for, anyway?

Tim

---

### Post by moteprime on 2011-11-09
On 11.10 it does not work with RT3090, the driver are there but there's some kind of bug that makes it run at really slow network speed, and also there are conflicts with other driver modules that are loaded. I got it working through the above workaround.
I have reported a bug on it, but it does not seem to get much attention: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659")

---

