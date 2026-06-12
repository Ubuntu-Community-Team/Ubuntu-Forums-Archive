---
title: "specify /boot folder for installation, since root fs drive is not recognized by BIOS"
date: 2019-04-25
forum: Installation &amp; Upgrades
---

### Post by onlinespending on 2019-04-25
I have a Dell desktop at work with a 3.5" spinning HDD with Windows installed on it, and a NVMe SSD that I installed in a PCIe x4 adapter, as the motherboard doesn't offer an NVMe slot. Problem is, the BIOS doesn't recognize the NVMe drive, and it's only after the kernel is loaded that it is. This becomes problematic when installing Ubuntu using the standard installation process, as it obviously has no way of knowing that the drive I'm installing it to (the NVMe) is not recognized by the BIOS. So it ends up installing the /boot folder to that NVMe, which causes Grub to fallback to the rescue prompt when booting up the system.

One solution would be to simply create a boot partition on the 3.5" drive that's recognized by the BIOS, with the root filesystem on the NVMe. But in the interest of tidiness, I'd like to have it create the /boot folder in the ESP partition which already contains the Windows Boot Manager. **How can I install the bootloader files to a /boot directory contained on that EFI partition, while installing the root filesystem to the NVMe SSD? I have tried boot-rescue and manually re-installing grub, but that doesn't work as it simply installs grub to the EFI partition with the /boot files still located on the NVMe, as it again is unaware that this won't work since the NVMe isn't recognizable by the BIOS.**

---

### Post by onlinespending on 2019-04-25
I went ahead and just used the obvious solution I mentioned of creating a /boot partition on the bootable, BIOS-recognizable drive and putting the root filesystem on the NVMe SSD which the BIOS cannot recognize. It works quite well and am satisfied with that solution.

---

