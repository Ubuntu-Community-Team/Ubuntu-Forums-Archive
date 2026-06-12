---
title: "Windows 8.1 not showing up after installation of Ubuntu 18.04"
date: 2018-08-04
forum: Installation &amp; Upgrades
---

### Post by neozencoder on 2018-08-04
Hi,

I had Ubuntu 16.04 along with Windows 8.1 dual boot system, working fine on my HP Envy laptop. I completely erased Ubuntu partition, and reinstalled Ubuntu 18.04, but Windows 8.1 is not being detected by grub. sudo os-prober (that worked previously) doesn't work anymore. I also did boot-repair, and but still not being able to bring Windows to grub menu or boot into Windows. I shall be grateful to you if you can look at it:

[http://paste.ubuntu.com/p/PpsPjqrjj2/](http://paste.ubuntu.com/p/PpsPjqrjj2/)

Thank you very much.

Thanks,
neozen

---

### Post by oldfred on 2018-08-04
Was Windows pre-installed?
Pre-installed Windows had to be UEFI boot on gpt partitioned drive.

But you now have MBR(msdos) partititioned drive and Windows only boots from MBR with BIOS boot.
And Ubuntu is installed in UEFI boot mode.
And grub is then reinstalled in BIOS boot mode to both MBR of drive and partition of drive?

The Windows BCD is also missing, it would have been in the ESP - efi system partition or in the BIOS version in the Windows boot partition. That can be recreated with Windows repair tools, but not from Linux.

---

### Post by neozencoder on 2018-08-04
This is not pre-installed Windows 8,1 Pro, rather I had installed it along with Ubuntu 16.04. Previously os-probe had worked to update grub. This time, when I erased Ubuntu 16.04 and installed 18.04 LTS, it was unable to detect Windows. Its bootloader (?) was on sda1, formatted as ntfs. With some searching on forum, I found that sda1 should be formatted as fat32 and marked as /boot/efi. I followed it, and messed it. I formatted sda1 to fat32 and with boot-repair installed grub even on that. Looking for suggestions to move ahead. Thanks.

---

### Post by oldfred on 2018-08-04
It looks more like you installed Windows in BIOS boot mode to a MBR partitioned drive.
You cannot change to UEFI boot without reinstalling Windows.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.
So if Windows is BIOS boot, you want Ubuntu in BIOS boot. And since you show grub in MBR, it looks like you must at some point had Ubuntu in BIOS boot mode, perhaps old install.

How you boot install media UEFI or BIOS, for both Windows & Ubuntu is then how it installs. 
Newer system should be UEFI, but do not have to be, since UEFI has CSM.
       
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Best just to convert sda1 back to Windows boot partition as NTFS with boot flag and run Windows repairs. And then using Boot-Repair reinstall the BIOS boot version of grub.

---

