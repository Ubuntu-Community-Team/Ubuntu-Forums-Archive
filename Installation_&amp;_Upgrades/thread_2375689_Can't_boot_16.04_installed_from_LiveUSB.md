---
title: "Can't boot 16.04 installed from LiveUSB"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by chiggs88 on 2017-10-26
Hey all, completely new to Ubuntu and Linux and I'm having issues installing the LTS of Ubuntu. I made a bootable USB with Rufus and ran through the default install on my Lenovo IdeaPad V570. I'm installing Linux as the sole OS on a brand new SSD. The install seemingly ran fine until I was prompted to reboot. I just cycle through the boot through to my boot menu and get a PXE-E61 error. I ran BootRepair with the recommended repair and received this report from it. [http://paste.ubuntu.com/25825196/](http://paste.ubuntu.com/25825196/) since running BootRepair, when I try to boot I get this error:
```
Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image \EFI\BOOT\grubx64.efi: Not Found
start_image() returned Not Found
```

I'm completely over my head here and would greatly appreciate any help I can get. Please let me know if there's anything I can provide to clarify anything.
Thanks in advance.


EDIT: Problem solved. The issue I was having was that, apparently,  GRUB2 does not play nicely with EFI partition tables. To fix this, I had  to load into a Live instance of Ubuntu, open Gparted, unmount all the  partitions and swap, format the drive, and set a new MBR/MSDOS partition  table. Then, I had to reboot back to the Live USB selection menu,  choose install Ubuntu, and manually set that partitions so it would keep  the MBR partition table. Afterwards everything worked just fine!  Hopefully this is helpful to someone else who has the same issue.

---

