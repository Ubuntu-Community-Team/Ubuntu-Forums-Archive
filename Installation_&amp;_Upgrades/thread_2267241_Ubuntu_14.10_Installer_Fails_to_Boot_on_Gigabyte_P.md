---
title: "Ubuntu 14.10 Installer Fails to Boot on Gigabyte PC"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by iExchange128 on 2015-02-28
When I boot my bootable ubuntu 14.10 USB on my GIGABYTE H97-HD3 motherboard with i5 4690 CPU, 16GB RAM and GTX750 graphics, I selected Install Now option and it shortly get stuck at the following lines:
```
[2.974542] nouveau E[  PGRAPH][0000:01:00.0] failed to load fuc409c
[2.974593] nouveau E[  DEVICE][0000:01:00.0] failed to create 0x18000717, -22
[2.974657] nouveau E[     DRM] failed to create 0x80000080, -22

```Would appreciate if you could let me know what I could try...

---

### Post by oldfred on 2015-02-28
It seems all Gigabyte motherboards have issues or need IOMMU settings in UEFI and/or boot parameter.
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

Also may have issues with video card.

 Maxwell 750 - kernel 3.15 required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
 open-source driver support for Maxwell, there's none right now, at least not mainline.  Feb 2014

I do not normally suggest installing a version that is not yet released, unless you have it as a second install for testing, but you may do better with the latest or 15.04 which will be out in April. That has major updates to kernel, support software & video that make it easier to install. You can use ppa which update an older install to newer kernel & drivers if installing older verison of Ubuntu.

---

