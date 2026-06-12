---
title: "Dual boot installation"
date: 2023-12-27
forum: Installation &amp; Upgrades
---

### Post by Norm24 on 2023-12-27
Not new to Ubuntu but it has been awhile since I did a dual boot installation.

Trying to install Ubuntu Mate 22.04.3 alongside Win10 but the installer fails to recognize that there is another OS(Win10) on the PC.

Any ideas how to proceed?

---

### Post by tea for one on 2023-12-27
Backup your data
Turn off Bitlocker (if installed)
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Disk must be GPT
Windows 10 > Check via Disk Management > Right Click (C drive) > Properties > Volume > Partition Style
Use Windows (Disk Management) tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run

---

### Post by Norm24 on 2023-12-29
No love here.

Converting the disk to GPT caused a host of issues one of which made the partition containing Win10 inactive so after reboot BIOs detected no operating systems.Good thing I had a copy of Win10 on a USB stick and was able to repair and boot back into Win.

Currently running 22.04.3 on an older MacBook Air and its doing just fine.Using two laptops isn't ideal but it works for now.

---

### Post by oldfred on 2023-12-29
Microsoft required vendors to install Windows in UEFI boot mode to gpt partitioned drives since release of Windows 8 in 2012.
So almost all hardware since 2012 is UEFI. But vendors may call it BIOS. My new Dell UEFI only system still calls it BIOS.

So Windows 10 should have been UEFI/gpt. Or did you install it yourself to very old BIOS/MBR configuration?
Even Windows 7 could be installed in UEFI/gpt mode, but most were BIOS/MBR.

Windows only boots in UEFI mode from gpt drives.
Windows only boots in BIOS mode from old MBR(msdos) partitioned drives.
Ubuntu, if on same drive, must be installed in same boot mode.
But best if all systems are installed in same boot mode.

And best if gpt partitioning used. The only place for MBR is with old BIOS installs of Windows.
Ubuntu can boot in BIOS mode from gpt or MBR. 
Ubuntu also can boot in UEFI mode from MBR, but really should not. That often breaks Windows BIOS installs.

---

### Post by Norm24 on 2023-12-30
@oldfred
 
The laptop in question is a Dell Latitude E7450.It was a refurb from a friend that was used by his students and he had several that he wiped and reinstalled Win10.He must have installed using MBR config.

For now I'm good with having two separate laptops.When I have sufficient time I'll revisit this and get it figured out.

---

