---
title: "Dual Boot off PCI Express [Card] USB 3"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by LaferriereJC on 2016-03-06
I have a server class system that doesn't have onboard usb 3, so I have a usb 3 pci express card.  I've read if I enable XHCI in the initramfs, Ubuntu will boot; however, this is with a computer which supports booting from USB 3; which mine does not.

I would like to chainload from an hdd to usb 3 using grub, and ensuring I load the proper modules in grub to allow me to do so.

Does anyone know all the steps?  I'm currently running windows 10 as the main OS.  Oh yes, the main OS is using a raid controller which is running 3 ssd's in Raid 0.  So i'm not sure if I need to resize the partition to allow for a single hard drive to have a /boot partition for ubuntu to chainload off of, or if I can just use the raid array as is with a resized partition.

If this is too difficult, I might just use a usb2 drive with grub installed and chainload off of that rather than mess with my raid configuration.

Currently, I have Ubuntu installed to a USB 3 flash drive, but am using it on USB 2.0 ports.

---

