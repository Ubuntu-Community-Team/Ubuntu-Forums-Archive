---
title: "Install UEFI version to disk using BIOS/MBR live boot?"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by Langevguy on 2016-02-22
I have a Lenovo M92p that suffers from the Lenovo Bios problem (will
only UEFI-boot Windows and RHEL OS's) even after a BIOS firmware update
from 10/2015. (See threads here for some details if interested
[https://mjg59.dreamwidth.org/20187.html](https://mjg59.dreamwidth.org/20187.html))

Here's what I need to do to make a workaround - but I can't:

1. Boot a USB drive with a Ubuntu or Mint live CD iso in BIOS/MBR mode
(because the Lenovo won't boot these as UEFI per above). I can easily
do this using legacy boot mode and selecting the USB drive as the boot
device.

2. Install Ubuntu or Mint *as a UEFI install* from the BIOS/MBR booted
live CD. I need to get the EFI bootloaders into the GPT format boot
partition and keep it as GPT. *I CAN'T FIGURE OUT HOW TO DO THIS STEP*
using the live CD installer. Remember, I can't boot the live USB key
as UEFI.

If I can perform step 2, then I can reboot the live CD (as BIOS/MBR
again), and go in and edit the EFI boot manager labels in the
hard-disk EFI boot partition to "fool" the Lenovo BIOS into thinking
there is an RHEL image being booted from the hard disk. (Again, see thread above for
details.)

So, anybody know how to accomplish Step 2 above?

Thanks,

- Les

---

### Post by oldfred on 2016-02-22
You may also be able to boot from the default or fallback entry.
All external devices boot from /EFI/Boot/bootx64.efi.
So one of the main work arounds is to copy shimx64.efi as bootx64.efi and boot hard drive entry.
Also those systems that use description often will boot an Ubuntu only install by changing description of ubuntu to "Windows Boot Manager"
If dual booting with Windows but Redhat works, you may need exact description but could use that description to boot ubuntu's shim file.

Boot-Repair can convert a BIOS install to UEFI. All it really does is totally un-install grub-pc(BIOS) and install grub-efi-amd64.
To install in BIOS mode on a gpt partitioned drive, you need the 1 or 2MB unformatted partition with the bios_grub flag if using gparted, or gdisk use ef02 type.

---

