---
title: "Cannot mount volume.  Mount: Operation not supported"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Rosewood_Arts on 2007-11-11
Although I have been able to work around the issues below, I would like to share my observations with the hope that others may benefit with improvement resulting. 

There appears to be a (?kernel?) issue in Gutsy 7.10 causing unpredictable block device assignments for sdx devices in computers with multiple hard drives and filesystems.  The resulting effects are numerous and varied and occur despite a reformat & new installation.

Depending upon the early device assignment, the settings in fstab may not match, and the device(s) is not mounted.  Resulting problems range from "restricted permissions" to "mount: operation not supported" or "cannot mount volume", or "NTFS signature missing".  This did not happen to me with Feisty 7.04.

When ntfs-config-generated settings in /etc/fstab match the "Device Manager" settings (Control Center -> Hardware Information), about half the time, mounting is automatic and all is well.  But the sdx settings in Device Manager (?kernel assignment?) change unpredictably from boot to boot...even from right to wrong (compared to fstab) automatically.

Curiously, NTFS partitions erroneously reported in Device Manager as reiserfs get mounted and function properly as NTSF. 

Unless ntfs-config properly auto-generates new and correct fstab settings on each boot, NTFS partitions will not be mounted properly.  

These errors are different from those caused by an unclean Windows shutdown.  In that case, booting back into Windows, running scandisc, and re-booting twice suffices.  Not here.

Although I am not capable of resolving these issues, I thought my observations might be useful to someone who can.

Thank you for your time and work on this fine OS.

---

