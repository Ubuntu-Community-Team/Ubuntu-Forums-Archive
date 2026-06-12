---
title: "Laptop BIOS no longer sees EFI partition"
date: 2016-07-23
forum: Installation &amp; Upgrades
---

### Post by cranerja on 2016-07-23
Hello,

On the laptop MSI GE72 6QF, I installed Ubuntu to an NVMe drive that came with it. Besides having to use acpi=off, it worked alright until trying to shut down. Plymouth continued forever, and minimizing it showed the repeated message "PCIe Bus Error: severityCorrected, type=Physical Layer, idx00e0 (Receiver ID)". Since then, the BIOS no longer recognizes any EFI partition on this drive, even though the drive still works once booted.

Is this a hardware issue? Has anyone experienced this?

Thanks in advance.

---

### Post by oldfred on 2016-07-23
Not sure what boot parameter may go with what version of Ubuntu.

Similar models from same brand often have same configuration and UEFI. So same boot parameters often needed.

Other MSI systems:
 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by cranerja on 2016-07-24
> **oldfred said:**
> Not sure what boot parameter may go with what version of Ubuntu.

Similar models from same brand often have same configuration and UEFI. So same boot parameters often needed.

Other MSI systems:
 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

Thank you for the reply! I was already using acpi=off to successfully boot. The issue is now that it immediately boots to BIOS and shows no bootable partitions, even with re-installation.

---

### Post by oldfred on 2016-07-24
Then you may have installed in one boot mode, but have system booting in another boot mode.
New UEFI systems have three ways to boot. UEFI with Secure Boot, Standard UEFI, and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And you can choose to boot installer in one mode which will be the mode it installs in, but have system set to default boot in another mode.

And you may have Secure Boot on. Many systems now call that setting "Windows" or "Other". But even with Windows 7 you have to use "Other" as Windows 7 does not support secure boot mode, just BIOS or UEFI.

---

