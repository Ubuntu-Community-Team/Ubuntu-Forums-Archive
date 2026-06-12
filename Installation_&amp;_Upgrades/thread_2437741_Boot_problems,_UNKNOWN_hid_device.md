---
title: "Boot problems, UNKNOWN hid device"
date: 2020-02-28
forum: Installation &amp; Upgrades
---

### Post by henkewikstrom on 2020-02-28
During boot the following error occurs most of the times. It have worked fine for some months, but after an update the problems started. Success in booting 1 of 10 times approximately.

My computer is a HP Spectre x360, i57200u from 2017. Ubuntu desktop 18.04.04 LTS, installed on computer (not virtualization). Dual boot with Windows 10.

Would appreciated help.

Kernel output as follows:

 1180176 x86/nn: Checking user space page tables

    1187948 x86/nn: Checked W X mappings: passed, no W X pages found.

    1188505 Run init as init process Loading, please wait...

    starting version 237

    1271245 ] usb 1-5: neu high-speed USB device number 2 using xhci hcd

    1286660 ]

    1429223 ] usb 1-5: Neu USB device found, idVendor=064e, idProduct=3401, bcADeuice= 0.11

    1430383

    1431496 usb 1-5: SeriaL Number: HF2066-P98B-OVO7-REVO101

    1508600 nume numeo: 4/e/e default/read/poll queues

    1510188 nuneon1: p1 p2 p3 p4 p5 p6 p? p8

    1559426 usb 1-7: new full-speed USB device number 3 using xhci_hcd

    1709102 ] usb 1-7: config 1 interface 1 altsetting 0 endpoint Ox3 has wMaxPacketSize 0, skippin

    1710146 usb 1-2: config 1 interface 1 altsetting o endpoint Ox83 has wMaxPacketSize 8, skipping

    1711864 ]

    1796035 clocksource: tsc: mask: Oxffffffffffffffff max_cycles: Ox27177c1c581, max_idle_ns: 44 0795280022 ns

    1281701 hidrau: rau HID events driver (c) Jiri Kosina 1290759 ] nume nune: pci function 00e0:6a:00.0 intel_ish_ipc 0000:00:13.0: enabling deuice (0000 -> 00e2)

    1429811 ] usb 1-5: New USB device strings: Mfr=1, Product=2, Serial Number=3 1430943 ] usb 1-5: Manufacturer: SuYin usb 1-5: Product: HP TrueVision FHD RGB-IR

    1211261 ] usb 1-7: Neu USB device found, idVendor=8087, idProduct-Oazb, bcdDevice= 0.10 1795402 ] tsc: Refined TSC clocksource calibration: 2711.989 MHZ SerialNumber=0 usb 1-7: Neu USB device strings: Mfr=0. Product=0,

    1797385 clocksource: Switched to clocksource tsc

    2088295 ish-hid (33AECD58-B679-4ES4-9BD9-A04D34FOC226): thid-ishl: enum_devices_done OK, num_ hid_devices=1 Begin: Loading essential drivers ... done.

    Begin: Running Begin: Mounting root file system ... Begin: Running scripts/local-top... done.

    Begin: Running/scripts/local-premount ...[ 2107692 hid-generic 001F:8087:0AC2.0001: hidrauo:

    <UNKNOWN> HID u2.00 Device Hid-ishtp 8087:0AC2] on

    2110794 hid-generic 001F:8087:OACZ.0002: hidraw1: <UNKNOWN> HID u2.00 Device Chid-ishtp 8087:

    scripts/init-premount ... done.

 OACZ) on

---

### Post by dragonfly41 on 2020-02-28
A guess .. something related to USB 3.0 device ??

[https://askubuntu.com/questions/729558/how-do-i-get-usb-3-0-driver-working-or-check-that-it-is-already-working](https://askubuntu.com/questions/729558/how-do-i-get-usb-3-0-driver-working-or-check-that-it-is-already-working)

---

