---
title: "Windows 7 Suspend kills Ubuntu 9.10"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by avidity on 2009-12-24
Installed Ubuntu 9.10 on a new Dell Studio 1555 running Windows 7. I used the Windows Installer for Ubuntu. I was very surprised how easy it was. I tested the installation by shutting down and restarting several times both into Windows and Ubuntu. Everything worked perfectly (with the exception of minor touchpad crazyness under Ubuntu.) I left the notebook running Windows 7. It suspended to hard drive. The next day I woke up Windows and resumed working. After a bit I rebooted and selected Ubuntu from the boot menu. I saw a few lines where it appeared it was searching for somehing to boot (there were at least two partitions referenced) and finally I was dumped out at a grub prompt. (See below)
 
Try (hd0,0): FAT16: No WUBILDR
Try (hd0,1): NTFS5: No wubildr
Try (hd0,2): NTFS5: 
 
sh:grub>_
 
Sorry if this has been addressed previously, but the forum search did not turn up any relevant posts.

---

