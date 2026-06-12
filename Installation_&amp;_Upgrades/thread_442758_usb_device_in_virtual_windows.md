---
title: "usb device in virtual windows"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by bittergourd on 2007-05-13
just wondering: is it possible to install the driver for an usb device in a virtual windows under linux, even if the host linux doesn't know how to use it?  of course the usb bus is properly recognized by linux, but not the device itself.

i have no idea how guest os communicates with physical devices thru linux, but if linux only takes care of the data transfer at low level (like repeater and hub in the physical level for the ether net), then it is absolutely possible to use the device "under" linux without a linux driver.

just crazy thought.  too lazy to restart my computer time after time just to use my TV card.

-E

---

### Post by veloce on 2007-05-18
> **bittergourd said:**
> just wondering: is it possible to install the driver for an usb device in a virtual windows under linux, even if the host linux doesn't know how to use it?  of course the usb bus is properly recognized by linux, but not the device itself.

i have no idea how guest os communicates with physical devices thru linux, but if linux only takes care of the data transfer at low level (like repeater and hub in the physical level for the ether net), then it is absolutely possible to use the device "under" linux without a linux driver.

just crazy thought.  too lazy to restart my computer time after time just to use my TV card.

-E

Yes, this should work - it has been known to work with usb printers.

Set up a usb controller in the virtual machine hardware.  
Start the vm
Use the VM - Removable Devices menu in vmware console to select the usb device to use.

---

