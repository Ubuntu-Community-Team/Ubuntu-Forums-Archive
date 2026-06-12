---
title: "driver for motherboard gigabyte EX58-UD4 sound problems"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by psihokiller4 on 2010-05-22
system Ubuntu 9.10
well I can't find any drivers for motherboard
gigabyte EX58-UD4


in game external lands I'm having sound problems 1. sound works normally after a while sound stops working at all and if I at that time turn off "enable sound effects" it automatic freezes my PC and I have to restart my PC after that

---

### Post by psihokiller4 on 2010-05-28
so no one found anything or what:confused:
so I should change the motherboard



is it like this to all gigabytes motherboards???

---

### Post by Mark Phelps on 2010-05-31
What you've run into is the main shortcoming of Linux OSs in general -- lack of drivers for new hardware.

Manufacturers write drivers for products; Canonical (and others) write drivers for devices.  Most manufacturers do NOT supply Linux drivers.

Which means that you have to do an "lspci" or "lsusb", find out what DEVICES you need drivers for -- and post THAT information in this forum.

---

### Post by psihokiller4 on 2010-06-01
military@dusan:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 12)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 12)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 12)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 12)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 VGA compatible controller: ATI Technologies Inc RV790 [Radeon HD 4800 Series]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
07:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
07:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
09:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
military@dusan:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                 
Bus 007 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel                                                                                 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by psihokiller4 on 2010-06-03
ok I tried to copy paste this on google and tried to get some drivers but I failed so far


how could I find drivers now
or better say packages for this devices????????

---

