---
title: "Ubuntu 18.04 install failing to recognize Realtek 8822BE"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by eastsidedev on 2018-05-16
I have a new ASUS VivoBook 15 ASUS Laptop X570UD

It has one SSD with Windows 10 Home pre-installed on it

It also has a 1TB hard drive that I am trying to install Ubuntu 18.04 on

The wireless hardware is working fine on Windows, Windows tells me that the WiFI hardware is:

```
Realtek 8822BE Wireless LAN 802.11ac PCI-E NIC

PCI Slot 9 (PCI bus 3, device 0, function 0)


```

When I installed Ubuntu 18.04 on the laptop, it did not recognize the WiFi hardware. It does recognize the wired LAN.

When I do:

```
spci -knn | grep Net -A3; rfkill list
```

I get:

```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
    Subsystem: AzureWave Device [1a3b:2950]
    Kernel modules: r8822be
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

When I do:

```
lshw -C network
```

I get:
```

  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 18:31:bf:42:f0:fc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.24 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:127 ioport:d000(size=256) memory:ef204000-ef204fff memory:ef200000-ef203fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:c000(size=256) memory:ef100000-ef10ffff
```

When I do:

```
lspci
```

I get:

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1e.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO SPI Controller #0 (rev 21)
00:1e.6 SD Host controller: Intel Corporation Sunrise Point-LP Secure Digital IO Controller (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b822


```

Any ideas? I got this new laptop, specifically so I can dump Windows. I do full stack development, and would like to dump Windows, but I don't know if it's such a good idea, if I need to be an Ubuntu system engineer, just do I can use it as a development environment.

---

### Post by dino99 on 2018-05-16
Similar requests:
[https://askubuntu.com/questions/1002957/rlt-8822be-wireless-problems](https://askubuntu.com/questions/1002957/rlt-8822be-wireless-problems)
[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
[https://tianb03.blogspot.co.uk/2017/07/ubuntu-1604-realtek-rtl8822be-wifi.html](https://tianb03.blogspot.co.uk/2017/07/ubuntu-1604-realtek-rtl8822be-wifi.html)

Looks like that driver is still worked on for kernels: [https://lkml.org/lkml/2018/4/9/896](https://lkml.org/lkml/2018/4/9/896)
So that means you mainly need the latest kernel to get it working (hopefully)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  (test 4.17-rc5)

---

