---
title: "help installing usb 2.0 controller"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by mendo on 2010-02-13
i have installed ubuntu server on an old pc and use it as a file server.  it only had usb 1.1 capabilities, so i installed a usb 2.0 pci card.  i use the usb to periodically backup important files to an external hd.  the usb 2.0 card shows up in terminal when i type 'lspci':

mendo@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:03.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:03.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:03.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:04.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)


when i plug the external hd into the new usb ports, i get nothing.  i am fairly new to ubuntu and have no idea where to start with troubleshooting this.  any help?

thanks!

---

### Post by mendo on 2010-02-14
plllllllleeeeaaaaase, somebody give me a hint.  i have know idea where to start and need help.

---

