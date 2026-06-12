---
title: "VMWare Player 2.0 not recognizing usb 2.0 device"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by foulox on 2007-12-16
Hi everyone,

I'm trying to use several USB 2.0 devices within Ubuntu by using a virtual machine running windows.  After a lot of trying I can't get any of my USB 2.0 devices working at USB 2.0 speeds in either VirtualBox or VMWare Player.  Both virtual machines degrade the devices to USB 1.1.

So now I'm wondering if the problem is not the virtual machine but the Ubuntu kernel.  

What can I do to test if Ubuntu is recognizing these devices as USB 2.0 devices?  I'm asking because from what I read I believe that if Ubuntu recognizes the device as USB 2.0 than the guest OS will too.

---

### Post by kejava on 2008-01-08
i hear yah foulox.  i created my vmx from the Server, then switched to running it from Player when I heard that USB 2.0 was supported.  Turns out that's only good for thumb drives or similar storage devices, at least in my case.

I have one USB 2.0 device ([Kvaser Leaf Light CAN controller]("http://www.kvaser.com/prod/hardware/leaf_light.htm")) that will only work in VMWare Player if I plug it into a USB 1.1 hub.

I considered making a switch to VirtualBox but I've seen similar behavior on VB 1.5.4 which is supposed to support EHCI.  Sadly, VB doesn't recognize some of the USB 1.1 devices that do work on Player.

What devices are you attempting to use?

---

### Post by steeven on 2008-05-07
add folloing lines to vmx file:
```
scsi0.present = "TRUE"
scsi0.pciSlotNumber = "18"
ehci.present = "TRUE"
ehci.pciSlotNumber = "19"
```

wm workstation add these lines for usb2.0 suppport. it worked for vm player 2.03 @ubuntu 8.04.

good luck~

---

### Post by philhinz on 2008-06-05
This worked for me.  (Vmplayer 2.03, Ubuntu 8.04)

Thanks!

---

### Post by mfoerster on 2008-07-15
Worked for me too!  2.04 and 8.04:)

---

