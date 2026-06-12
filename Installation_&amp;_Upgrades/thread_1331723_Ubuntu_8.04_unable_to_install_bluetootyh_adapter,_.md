---
title: "Ubuntu 8.04 unable to install bluetootyh adapter, best practice suggestions please."
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by rosier on 2009-11-19
Hi newbie to Linux and would like help on a few things. Ive installed Hard Heron- running well and stable. Ive come over 

1. How to install my bluetooth IVT Bluesoil Adapter Dongle?
2. How to install my webcam.


1. IT Bluetooth Adapter- have installed the software but its not picking up the hardware.
[INDENT]Heres some info:
kids@kids-desktop:~$ lsusb
Bus 005 Device 006: ID 05ac:120a Apple Computer, Inc. iPod Nano
Bus 005 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05a9:8519 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  
kids@kids-desktop:~$ 
[/INDENT]Its picking up my webcam, mouse and card reader cant see my bluetooth adapter.
Heres the var log and it does register something when i plug in the adapter.
[INDENT]Nov 20 09:29:00 kids-desktop kernel: [49308.260363] usb 4-2: new full speed USB device using uhci_hcd and address 21
[/INDENT]Ive tried installing it on Fedora- picks it up automatically- no problems.

can anyone help?

2. The same with my webcam- maybe with it listed on the list of USB items it may be easier.

Thanks for any suggestions in advance. Regards John

---

