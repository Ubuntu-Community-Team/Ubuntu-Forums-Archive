---
title: "Installed on P50 to Dual Boot with Windows 10"
date: 2019-03-31
forum: Installation &amp; Upgrades
---

### Post by jhbalaji on 2019-03-31
Installed 16.04LTS with Win 10 on a thinkpad P50. Can't get to GRUB to boot to my xubuntu install. During the install it didnt detect the windows install as well but I proceed with installation

PasteBin logs
[http://paste.ubuntu.com/p/Fwx3QHG7zv/](http://paste.ubuntu.com/p/Fwx3QHG7zv/)

[http://paste.ubuntu.com/p/CSXKCHnyNn/](http://paste.ubuntu.com/p/CSXKCHnyNn/)

Please let me know is there a fix. I would upgrade to 18.xx once I get back to this successfully.

---

### Post by oldfred on 2019-03-31
You have gpt partitioning on your NVMe drive.
So Windows has to be in UEFI boot mode.

But you must have installed Ubuntu in BIOS boot mode as you now have a bios_grub partition for Ubuntu/grub BIOS boot on gpt partitioned drives.

And you are not showing any Windows or Ubuntu boot entries in UEFI.

You need to first run Windows repairs to get Windows .efi boot files into the ESP & Windows boot entry into UEFI. Be sure to boot only in UEFI mode for both Windows & Ubuntu. Make sure that Windows fast start up is also off. Windows 8 & 10 use same repair instructions.
[https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    
Then run Boot-Repair to reinstall grub in UEFI boot mode.
Always boot in UEFI boot mode to install or repair your system.
More info on Ubuntu install & repair in link in my signature.

Boot-Repair now does file copy automatically, so manual copy not now required if using Boot-Repair.
       Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)

---

