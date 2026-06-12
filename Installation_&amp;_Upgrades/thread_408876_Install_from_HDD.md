---
title: "Install from HDD"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by nads on 2007-04-13
Hello,

I tried installing Ubuntu from a burned ISO image but failed because the CD drive failed.

Is there a way to boot and install the same ISO image but using the HDD? 

The ideal setup would be to have another spare partition with the Ubuntu image and boot from it. Has anyone done anything of the sort? Is it possible?

Thanks!

nads

---

### Post by raja on 2007-04-13
I dont think you will be able to do it from the hard drive. If you dont have a working CD drive, the options may be to use a USB drive (if you have one larger than 1 GB and your bios can boot from a USB device), netboot if you can PXE boot or do it with grub for NT as explained [here]("http://marc.herbert.free.fr/linux/win2linstall.html"). I have used the last 2 methods as I have a laptop without an optical drive.

---

### Post by nads on 2007-04-13
Thanks for the quick reply...

My pc is kind of old, so I don't have an option to use a usb-drive as a bootup device.

I do have a CD drive, but it doesn't always read the CDs well. I can boot with it - but it always gets stuck in the middle of the installation.

Isn't there a way to first boot from a CD and then "boot again" from an ISO file?

---

### Post by raja on 2007-04-13
Do you have windows already installed (and trying to dual boot). In that case you can use grub for NT to boot of a downloaded linux image and then download the rest online.   If you dont have any OS installed at present, I am not sure what else you can do.

---

