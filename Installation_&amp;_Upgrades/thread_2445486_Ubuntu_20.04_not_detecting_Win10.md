---
title: "Ubuntu 20.04 not detecting Win10"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by Mylorharbour on 2020-06-15
Hi guys,
I have an 8 year old i5 desktop which dual booted with Win7 and Ubuntu 16.04 (on a suitably partitioned 1Tb hard disk), clearly both in need of an upgrade. I downloaded the Win10 upgrade and 20.04 and backed up my files. I struggled to upgrade Windows as I couldn’t get my head around GPT and UEFI so I handed the machine over to my friendly local PC expert who wiped the drive and installed Win10. When he returned it I used Win10’s disk management to shrink the Win10 partition to about 230Gb then used gparted to set up a Shared NTFS partition of 490Gb, a 200Gb ext4 for Ubuntu and an 8Gb swap.

Attempting to install Ubuntu from a DVD I found it failed to detect Win10. Following this thread on the forum, [https://ubuntuforums.org/showthread.php?t=2392572](https://ubuntuforums.org/showthread.php?t=2392572) I tried the various options but had no joy. Digging around the machine I found the bios mode is legacy and the partition style had been changed to MBR from GPT during the Win10 install. I’ve disabled fast start up and can find nothing about secure boot, probably due to the lack of UEFI.

Any ideas where I should go from here?

---

### Post by CelticWarrior on 2020-06-15
> I found the bios mode is legacy and the partition style had been changed to MBR from GPT during the Win10 install.

Your friendly local PC expert is undeserving of such title. It's absurd to force Legacy mode for Windows 10. The preinstalled Windows 7 typically was even in the early UEFI machines but there's absolutely no reason to change GPT to MBR and consequently be forced to install Windows 10 in Legacy mode.

That said, the reason why the Ubuntu installer isn't detecting Windows can be one or both of the following conditions (neither mentioned in the thread linked): 1. You're booting Ubuntu media in UEFI mode and/or 2. Windows Fast Startup is enabled.

The Ubuntu media needs to be booted in the same mode Windows was installed. How it boots is how it installs. For dual-booting you can't mix different modes. And in any scenario or mode Fast Startup should be disabled first in Windows (not applicable to any Windows version prior to Windows 8, reason why it wasn't an issue before, with Windows 7).

---

### Post by Mylorharbour on 2020-06-15
Thanks for the prompt reply CW. I&#8217;ll look into this further. How can I check what mode the Ubuntu media was booted and how would I change it?

---

### Post by CelticWarrior on 2020-06-15
Likely you have both modes enabled so external media should show up twice, one entry with "UEFI", one without it. Or, depending on how it was done (the ISO "burning") it may only boot in one mode.

---

### Post by Mylorharbour on 2020-06-17
Getting there CW.
I found out how to boot the Ubuntu installation disk in legacy mode then began the install. This time it spotted Win10 but in the Installation Type window it shows:
sda1.    ntfs.    607MB          Used 482MB.        System Windows 10
sda2.    ntfs.    249867MB.    Used 26481MB.    
sda5.    ntfs.    511315MB.    Used 112MB
sda6.    ext4.   229828MB.    Used 4743MB
sda7.    swap.  8581MB

Although not labelled as such I suspect Windows 10 is actually sitting on sda2?
sda5 will be a shared partition for files
sda6 will be Ubuntu

Does this look ok to you? Why does it show Windows 10 in sda1 and would I be ok to continue with the installation?

---

### Post by oldfred on 2020-06-17
Windows in BIOS boot mode has a Boot partition that you normally do not see in Windows.
Windows in UEFI boot mode has many required partitions.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

You do know that BIOS/MBR started 35 years ago with the IBM PC & DOS. Many kluges to keep it working on newer systems. It still works with Windows 10, but you will have some issues.

Make sure you have good backups.
Make a Windows repair flash drive & keep your Ubuntu live installer.

Grub only boots working Windows. That means if Windows 10 turns fast start up back on with an update, which it often does, you will not be able to boot Windows from grub. Or if Windows needs chkdsk, or other fixes grub will not boot it.

With BIOS you either have to temporarily install a Windows boot loader to MBR and see if it boots & f8 gets you into repair console or your can  boot repair/recovery flash drive, fix Windows & then use Ubuntu live installer to restore grub to MBR.

With UEFI, it is like having multiple MBRs as each system has boot files in the ESP - efi system partition and you, at any time can reboot & start that system from UEFI.

---

