---
title: "Dual boot Ubuntu &amp; Windows Server 2016, with the latter on a PCIe SSD without UEFI"
date: 2017-03-05
forum: Installation &amp; Upgrades
---

### Post by SonicMetal15 on 2017-03-05
I have been trying to figure this out for the past week without any luck.  

Basically, I want Windows Server 2016 to boot off of the NVMe PCIe SSD (which my legacy BIOS does not see) and have Ubuntu boot from a normal SATA drive using GRUB2.  My BIOS is setup to boot the SATA drive where Ubuntu and GRUB2 are installed, so that I can dual boot Windows and Ubuntu from the GRUB2 menu.  I have no problem booting into Ubuntu, but I cannot get into WIndows.  It always results in this error: 

"Error no such device / Setting partition type to 0x83 / Error invalid signature EA8EC0CF8EC0960B"

I have tried:
-the Boot-Repair PPA without success
-os-prober and update-grub commands without success
-the Windows installation to fix the boot sector and MBR without success
-Tianocore-UEFI-DUET bootloader without success (this results in error messages in red upon booting it from a USB thumb drive)
-Cloverfield bootloader without success (this was a last resort since it is a Mac OS bootloader but supposedly works to multiboot Linux and Windows)

Out of curiosity I reversed it and was able to dual boot Ubuntu from the NVMe PCIe SSD and Windows Server 2016 from the SATA drive, but that is not what I want.  

My first attempt at this was to do the recommended installation of Windows Server 2016 first on the SSD, then Ubuntu second so that GRUB2 could handle the bootloading.  When that didn't work, I tried doing it the other way around - installing Ubuntu first on the SATA drive, and WIndows Server second on the SSD, and updatding GRUB2.  When that failed, I tried installing both Ubuntu AND Windows Server on the SATA drive (which worked - I was able to boot into both successfully) then used Clonezilla to copy the Windows Server partition to the SSD and delete it from the SATA drive after, but still was unable to boot into Windows on the SSD after reconfiguring and updating its boot sector.    

Here is the current state of my system:

[http://paste.ubuntu.com/24121014/plain/](http://paste.ubuntu.com/24121014/plain/)

I know that the real issue here is Windows not liking the lack of BIOS boot support from the NVMe PCIe SSD, but I'm sure there is a way to have GRUB2 boot up Windows from the SSD even if your BIOS doesn't natively support it.  Does anyone have any idea how to make this work?

---

