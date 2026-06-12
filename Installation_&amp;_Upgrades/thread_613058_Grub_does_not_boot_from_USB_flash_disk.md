---
title: "Grub does not boot from USB flash disk"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by girto on 2007-11-14
I have installed SGD on a 1GB flash disk, disabled completely the hard disk and CD in the BIOS and setup up to boot from the UFD. Upon booting, all I get is a black screen with the words GRUB at the top left and the PC hangs.

Any help will be appreciated.

---

### Post by girto on 2007-11-15
Problem solved!

For anybody interested, it turned out that the PC considered the USB flash disk as a floppy disk, and thus the procedure to install SGD to a floppy should be used:
dd if=SGD_floppy_image.iso of=/dev/sda

SGD_floppy_image.iso represents the name of the floppy SGD image (change as appropriate)
/dev/sda is the device representing the usb flash disk (change as appropriate)

Reboot from the USB flash disk and you've got SGD!

---

