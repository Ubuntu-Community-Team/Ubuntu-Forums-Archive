---
title: "USB 3.0 --&gt; Not enough bandwidth for new device state."
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by jdee2 on 2016-10-10
I've been working on a project involving Kinect on Ubuntu. I didn't have the necessary hardware apparently. 

Due to the flickering issue I had on my older laptop with the Kinect -  I went out and  bought a newer laptop. But I had to be realistic and get something the  family would need/want. So I got a surface pro 4 and dual booted ubuntu  onto a separate partition. Some trickery due to UEFI shell, but not  horrible.

That’s done and  been struggling with the darn kinect, honestly I was further along with the flickering.

 After some research, turns out that the one USB port is USB 3.0,  which is fine except turns out that USB 3.0  isn’t entirely backward  compatible on Ubuntu and that I am supposed to disable the xHCI driver. I  tried this on ubuntu (not my strongest OS), but even black listing the  driver apparently still loads it up as you can see below.

 [  505.041427] usb 1-1.4: USB disconnect, device number 6
[  505.041544] usb 1-1.4.1: USB disconnect, device number 8
[  505.042720] usb 1-1.4.2: USB disconnect, device number 7
[  505.043102] usb 1-1.4.3: USB disconnect, device number 10
[  510.873643] usb 1-1.4: new high-speed USB device number 11 using xhci_hcd
[  510.962029] usb 1-1.4: New USB device found, idVendor=0409, idProduct=005a
[  510.962043] usb 1-1.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  510.963051] hub 1-1.4:1.0: USB hub found
[  510.963112] hub 1-1.4:1.0: 3 ports detected
[  511.901523] usb 1-1.4.2: new full-speed USB device number 12 using xhci_hcd
[  512.016537] usb 1-1.4.2: New USB device found, idVendor=045e, idProduct=02b0
[  512.016551] usb 1-1.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  512.016558] usb 1-1.4.2: Product: Xbox NUI Motor
[  512.016564] usb 1-1.4.2: Manufacturer: Microsoft
[  513.445159] usb 1-1.4.1: new high-speed USB device number 13 using xhci_hcd
[  513.551162] usb 1-1.4.1: New USB device found, idVendor=045e, idProduct=02ad
[  513.551174] usb 1-1.4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  513.551181] usb 1-1.4.1: Product: Xbox Kinect Audio, © 2011 Microsoft Corporation. All rights reserved.
[  513.551186] usb 1-1.4.1: Manufacturer: Microsoft
[  513.551191] usb 1-1.4.1: SerialNumber: A44887B20066049A
[  515.237089] usb 1-1.4.3: new high-speed USB device number 14 using xhci_hcd
[  515.345430] usb 1-1.4.3: New USB device found, idVendor=045e, idProduct=02ae
[  515.345444] usb 1-1.4.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[  515.345451] usb 1-1.4.3: Product: Xbox NUI Camera
[  515.345457] usb 1-1.4.3: Manufacturer: Microsoft
[  515.345463] usb 1-1.4.3: SerialNumber: A00361900382050A
[  515.346343] usb 1-1.4.3: Not enough bandwidth for new device state.


Due to the Surface Pro 4 latest firmware - I cannot disable xHCI in latest UEFI Bios, so  apparently thats out too. 
I don’t know how to “compile a new kernel” sounds… menacing.

Any Suggestions on how to force USB 2.0 to load rather than USB 3.0 on ubuntu?

---

