---
title: "Modifying Live CD ISO images"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by rdbrown on 2010-07-10
Are the grub/menu.lst and the mkiso script for building the Live ISO images available for download?

For the upcoming Software Freedom Day, we'd like to be able to give away DVDs with TheOpenDisc windows software collection, but that boots as an Ubuntu Live CD.

Using the menu.lst and mkiso command from [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)
2008-02-06 "Transforming your Installation into a Live DVD/CD" gives me a menu when testing with
QEMU but booting fails with "Error 15: File not found", even why trying the Memory Test

$ qemu -cdrom ~/live-cd.iso -boot d  # stderr output
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"

---

### Post by rdbrown on 2010-07-20
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)  provide the necessary documentation.

---

