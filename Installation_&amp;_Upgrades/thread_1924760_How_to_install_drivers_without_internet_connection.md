---
title: "How to install drivers without internet connection"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by sdade on 2012-02-13
Hi there! I am pretty new with Ubuntu and I can´t access the internet bc the ethernet controler and the network controller are unclaimed. So I guess I have to install the appropriate drivers. How can I do this without an internet connection available in Ubuntu?
The computer is a dualboot (Win 7 / Ubuntu Lucid Lynx), the controllers are:
Atheros AG8151 (Ethernet) and Intel Centrino Advanced-N 6205 (Network). They work fine under Win 7.
Thanks for your help!

---

### Post by raja.genupula on 2012-02-13
* open System Settings -> Hardware -> additional drivers 
see is it giving you any list  still have to install .

* open terminal and type lspci and paste the output herr .

All the best.

---

### Post by sdade on 2012-02-17
Hi! So I did "System - Administration - Hardware Drivers" and Ubuntu searched for availabe drives but did not find any. There is no "Settings - Hardware" on my Ubuntu Lynx.

And this is what lspci told me:

lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
02:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
03:00.0 Network controller: Intel Corporation Device 0082 (rev 34)
04:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
05:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)

Thanks a lot for your help! Andreas

---

