---
title: "Can't finish Installation of 8.04"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by rillip on 2008-09-14
I'm trying to do a clean install of Heron and running into some issues.

Just for history, I got the error initially that

"this device is not an 8139C+ compatible device, try using 8139too instead."  Doing some research this seemed to be related to the Realtek onboard LAN card.  This particular card has a standard card identified as Realtek and a secondary card identified as Gigabyte Ethernet something.  I disabled this one from bios, and now it's getting past that and finding the Realtek card.

My issue now is that the installation is not proceeding at another point.  It's not frozen; I can still interact in the initramfs shell.  However, it is not proceeding after letting it "think" for over two hours, so I'm confident it's not going to proceed at this point.  The last line in dmesg is 

```
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6: USB HID core driver
```

Any ideas?  I've researched this quite a bit and tried the following:

passing irqpoll from the startup options
passing noapic from the startup options
passing noacip from the startup options
setting the sata controller to ahci mode instead of ide from bios

I can't recal the exact models, but it's a AMD 64x2 processor, AM2 ATX motherboard, I think from Asus, and a Maxtor 80 gigabyte SATA II drive.  

On a side note, I'm also seeing errors indicating it's loosing connection to the sata drive, retrying in 5 seconds... then it says SATAII link up, 1.5 GBPS, etc.  Impending failing hard drive, or normal latency?

Edit: after reading some more of the posts on here, I've also tried setting the SATA controller back to ide mode and passing all_generic_ide from the startup options, but again, no change

---

### Post by rillip on 2008-09-14
As another update, I've replaced the drive with an alternate and am still getting the same errors, now on a different SATA port, so I don't think it's the drive.  Still no joy getting past the USB portion in the original message however.

---

