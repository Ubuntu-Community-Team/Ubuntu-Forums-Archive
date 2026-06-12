---
title: "cannot upgrade, &quot;grub-install: error: cannot find EFI directory&quot;"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2022-10-13
Dual boot machine, windows 11 and Ubuntu 18.04.  Ran sudo apt update, then sudo apt upgrade.  Update returned "9 packages upgradeable",  upgrade gives an error:  grub-install: error: cannot find EFI directory.

Have 3 nvme hard drives, /dev/nvme0n1, /dev/nvme1n1, and /dev/nvme2n1.  Appears than /dev/nvme0n1 has a partition (/dev/nvme0n1p2) that is named "EFI system partition" (according to GPARTED).  This partition is on the same drive as the windows 11 installation.  
In addition there is also a partition on the 3rd drive, /dev/nvme2n1p5, has a FAT32 file system, and "flags" boot, esp (GPARTED flags).

Is the error message caused by having the "EFI system partition" on the drive containing windows?

Any and all suggestions greatly appreciated.

---

### Post by oldfred on 2022-10-13
Ubiquitys default install is to ESP on first drive. Those that do not want it on the first drive need to manually partition in advance to include an ESP on desired drive. Many work arounds in very old but current bug report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

In bug report, and probably easiest.
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

If system is new enough for Windows 11, it may need 22.04 to have latest kernel & drivers to support that new of a system.
Windows 11 fast start up and/or an UEFI setting on protecting UEFI boot may be locking ESP on Windows drive, so grub cannot do its default install to that ESP.

---

