---
title: "Ubuntu 16.4 is freezed at login after connect to internet by wireless"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by sayres561 on 2017-03-12
I am using of **ubuntu 16.04 lts** .after updating, when i login to my ubuntu, immediately when i connect to INTERNET by  wireless my ubuntu is frizzed and even nothing is not registered on  syslog. but  i can login by guest user because I don't access to internet!!

  

  I found that when i disable network-manager.service i can login by user. and when i am in desktop ,by running service network-manager restart ubuntu is frizzed again and i have to restart my computer.

```
manifest@manifest-System:~$ sudo lshw -C network
[sudo] password for manifest: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 06
       serial: bc:ae:c5:75:27:f3
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:36 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1.5
       logical name: wlx00304f8b1f0f
       serial: 00:30:4f:8b:1f:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.4.0-31-generic firmware=N/A ip=192.168.43.137 link=yes multicast=yes wireless=IEEE 802.11bgn


```

can someone  help my? How can I understand where or what is my problem?
I don't have **Ethernet **for testing unfortunately.

---

