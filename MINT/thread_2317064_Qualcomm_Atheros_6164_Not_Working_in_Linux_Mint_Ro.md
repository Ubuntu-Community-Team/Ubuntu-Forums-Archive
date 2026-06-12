---
title: "Qualcomm Atheros 6164 Not Working in Linux Mint Rosa"
date: 2016-03-13
forum: MINT
---

### Post by dryicefox on 2016-03-13
I feel as if I have tried everything and am this close to not using linux mint \\ .
I really want it to work because I feel it runs much smoother.

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 50:7b:9d:71:63:47
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.0.18 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:33 ioport:1000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff
[COLOR=#ff0000]  *-network UNCLAIMED
       description: Network controller
       product: QCA6164 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0800000-f09fffff
[/COLOR]

```

running 64 bit

lspci
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R6 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port
00:03.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter (rev 20)

```

Sorry if this is a huge initial thread. I'm trying to cut the crap since I have been to so many other threads and they seem to ask for all the same info.

---

### Post by jeremy31 on 2016-03-13
Linux Mint has it's own forum @ forums.linuxmint.com
If ```
uname -a
``` shows a 3.19, 3.16, or 3.13 kernel do
```
wget https://www.dropbox.com/s/nmgb5li6sd6i7ij/backath10k-dkms_2.0_all.deb
sudo dpkg -i backath10k-dkms_2.0_all.deb
```

---

### Post by dryicefox on 2016-03-13
Thanks! Hopefully this gets to everyone that needs it! Also I am not able to connect to my internet its on auto channel.

Cannot use channel 12+ for my 2.4 ghz connection, only 1-11
For my 5 ghz connection it is 36 40 44 48 14 163 167 161 165

Can someone explain this?

My entire wireless connection table also disappeared about 5 minutes in. So it stopped working?
FIXED BY REBOOTING :3 oldest advice in the world heeded

---

### Post by howefield on 2016-03-13
Thread moved to the "*MINT*" forum.

---

### Post by dryicefox on 2016-07-02
Some gits for people who need the deb both Tarballed and unTarred

Tar: [https://www.dropbox.com/s/x0eo38xo555umxt/backath10k.deb.tgz?dl=0](https://www.dropbox.com/s/x0eo38xo555umxt/backath10k.deb.tgz?dl=0)

UnTar: [https://www.dropbox.com/s/gw6hne14xi2l13e/backath10k-dkms_2.0_all.deb?dl=0](https://www.dropbox.com/s/gw6hne14xi2l13e/backath10k-dkms_2.0_all.deb?dl=0)

---

### Post by jeremy31 on 2016-07-10
If you post those in other places please post a note that it is not to be used in Linux Mint 18 as the kernel already supports the device and all it needs is firmware from [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb)

And reboot for it to work.  I deleted it from my dropbox as people were using it in Ubuntu 16.04 and it caused additional issues when troubleshooting

---

