---
title: "3g sprint modem issues"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mrjohnston on 2010-03-30
I was curious if anyone else here has had issues with Sprint 3g USB modem erroring out frequently and requiring the modem to be unplugged and plugged back in to get a connection.

I ran Karmic with no issues with the modem prior to this, and Windows has no disconnects or errors either.  Have they changed something to cause this?  Is this only me it happens with?  Does anyone else have an idea of why it happens?  (I have tested a fresh install of Lucid and an upgrade from Karmic, 32 bit installs)

---

### Post by Easy Lyle on 2010-03-30
Yes, I do.  I have a local carrier, but same basic USB cell modem.  Used this without problems from 9.04 on, and the Beta 1 update threw me into chaos.  
Now I plug it in, it connects, then instantly bumps me off.  Can't reconnect, but if I unplug it and then plug it back in, then select it, works like a charm.
Don't really know where to report it, so I've been stalking the boards here..  lol

---

### Post by cariboo on 2010-03-30
All bugs are reported at [https://bugs.launchpad.net]("https://bugs.launchpad.net"). I'm not sure though if the problem is because of Network-Manager or udev. Have you checked the output of dmesg, when the device fails?

---

### Post by Easy Lyle on 2010-03-31
> **cariboo907 said:**
> All bugs are reported at [https://bugs.launchpad.net](https://bugs.launchpad.net). I'm not sure though if the problem is because of Network-Manager or udev. Have you checked the output of dmesg, when the device fails?

Here's what I get after a reboot and just going through the process like I do.

easy@easy-laptop:~$ dmesg | grep -i usb
[    0.430238] usbcore: registered new interface driver usbfs
[    0.430238] usbcore: registered new interface driver hub
[    0.430238] usbcore: registered new device driver usb
[    0.510894] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.510974] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.540022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.540183] usb usb1: configuration #1 chosen from 1 choice
[    0.540213] hub 1-0:1.0: USB hub found
[    0.540377] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.570016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.570085] usb usb2: configuration #1 chosen from 1 choice
[    0.570110] hub 2-0:1.0: USB hub found
[    0.570185] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.570205] uhci_hcd: USB Universal Host Controller Interface driver
[    0.570289] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.570423] usb usb3: configuration #1 chosen from 1 choice
[    0.570448] hub 3-0:1.0: USB hub found
[    0.570559] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.570689] usb usb4: configuration #1 chosen from 1 choice
[    0.570714] hub 4-0:1.0: USB hub found
[    0.570810] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.570925] usb usb5: configuration #1 chosen from 1 choice
[    0.570952] hub 5-0:1.0: USB hub found
[    0.571054] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.571188] usb usb6: configuration #1 chosen from 1 choice
[    0.571216] hub 6-0:1.0: USB hub found
[    0.571309] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.571425] usb usb7: configuration #1 chosen from 1 choice
[    0.571450] hub 7-0:1.0: USB hub found
[    0.850068] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.009222] usb 1-2: configuration #1 chosen from 1 choice
[   11.746617] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input9
[   11.746665] usbcore: registered new interface driver uvcvideo
[   11.746668] USB Video Class driver (v0.1.0)
[  122.942548] hub 2-0:1.0: unable to enumerate USB device on port 4
[  123.922588] usb 6-2: new full speed USB device using uhci_hcd and address 2
[  124.094281] usb 6-2: configuration #1 chosen from 1 choice
[  124.183827] Initializing USB Mass Storage driver...
[  124.187082] usb-storage: probe of 6-2:1.0 failed with error -5
[  124.187103] usbcore: registered new interface driver usb-storage
[  124.187142] USB Mass Storage support registered.
[  124.300069] usb 6-2: USB disconnect, address 2
[  125.822547] usb 6-2: new full speed USB device using uhci_hcd and address 3
[  125.990177] usb 6-2: configuration #1 chosen from 1 choice
[  126.020067] scsi6 : SCSI emulation for USB Mass Storage devices
[  126.030076] usb-storage: device found at 3
[  126.030080] usb-storage: waiting for device to settle before scanning
[  126.053463] usbcore: registered new interface driver usbserial
[  126.053653] USB Serial support registered for generic
[  126.053850] usbcore: registered new interface driver usbserial_generic
[  126.053853] usbserial: USB Serial Driver core
[  126.065599] USB Serial support registered for Sierra USB modem
[  126.065816] sierra 6-2:1.0: Sierra USB modem converter detected
[  126.067185] usb 6-2: Sierra USB modem converter now attached to ttyUSB0
[  126.067229] usb 6-2: Sierra USB modem converter now attached to ttyUSB1
[  126.067278] usb 6-2: Sierra USB modem converter now attached to ttyUSB2
[  126.067318] usb 6-2: Sierra USB modem converter now attached to ttyUSB3
[  126.067337] usbcore: registered new interface driver sierra
[  126.067340] sierra: v.1.3.8:USB Driver for Sierra Wireless USB modems
[  131.040058] usb-storage: device scan complete
[  139.356048] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.357041] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.358041] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.359039] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.360036] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.361035] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.362032] sierra ttyUSB0: resubmit read urb failed.(-1)
[  139.363052] sierra ttyUSB0: resubmit read urb failed.(-1)
[  176.040084] usb 6-2: USB disconnect, address 3
[  176.042159] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[  176.043626] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[  176.046045] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[  176.047617] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[  202.030050] usb 6-2: new full speed USB device using uhci_hcd and address 4
[  202.218885] usb 6-2: configuration #1 chosen from 1 choice
[  202.228819] usb-storage: probe of 6-2:1.0 failed with error -5
[  202.228877] usb 6-2: USB disconnect, address 4
[  203.790056] usb 6-2: new full speed USB device using uhci_hcd and address 5
[  203.978095] usb 6-2: configuration #1 chosen from 1 choice
[  203.984023] sierra 6-2:1.0: Sierra USB modem converter detected
[  203.985060] usb 6-2: Sierra USB modem converter now attached to ttyUSB0
[  203.985105] usb 6-2: Sierra USB modem converter now attached to ttyUSB1
[  203.985148] usb 6-2: Sierra USB modem converter now attached to ttyUSB2
[  203.985189] usb 6-2: Sierra USB modem converter now attached to ttyUSB3
[  203.991334] scsi8 : SCSI emulation for USB Mass Storage devices
[  203.996541] usb-storage: device found at 5
[  203.996543] usb-storage: waiting for device to settle before scanning
[  209.001540] usb-storage: device scan complete
easy@easy-laptop:~$ 

Hope this helps.  And once again thanks to all who work on this to make 10.04 great!

---

### Post by mrjohnston on 2010-03-31
Here is my dmesg file. This seems to be the relevant and repeated part when it fails.
[    9.911474] type=1505 audit(1270068174.516:5):  operation="profile_load" pid=1028 name="/usr/share/gdm/guest-session/Xsession"
[    9.912831] type=1505 audit(1270068174.520:6):  operation="profile_replace" pid=1033 name="/sbin/dhclient3"
[    9.913080] type=1505 audit(1270068174.520:7):  operation="profile_replace" pid=1033 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.913218] type=1505 audit(1270068174.520:8):  operation="profile_replace" pid=1033 name="/usr/lib/connman/scripts/dhclient-script"
[   10.059216] type=1505 audit(1270068174.664:9):  operation="profile_load" pid=1034 name="/usr/bin/evince"
[   10.062372] type=1505 audit(1270068174.668:10):  operation="profile_load" pid=1034 name="/usr/bin/evince-previewer"
[   10.064351] type=1505 audit(1270068174.672:11):  operation="profile_load" pid=1034 name="/usr/bin/evince-thumbnailer"
[   11.605997]   alloc irq_desc for 29 on node -1
[   11.606001]   alloc kstat_irqs on node -1
[   11.606011] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X

---

