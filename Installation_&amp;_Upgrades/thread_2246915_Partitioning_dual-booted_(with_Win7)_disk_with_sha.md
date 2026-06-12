---
title: "Partitioning dual-booted (with Win7) disk with shared partition"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by Epistimi on 2014-10-04
I want to install Ubuntu on my Lenovo ThinkPad Edge E530 laptop, which already has Windows 7 installed (I want to dual boot the two), and I'm a bit confused about the disk partitioning. I've tried following [this]("https://help.ubuntu.com/community/DiskSpace"), but I still have some questions. This is how I've considered partitioning my (~460 GB) disk:

[LIST]
[*]Root: >=15 GB (at least 15, but is there an advantage to making it bigger?)
[*]SWAP: 4 GB (I have 4 GB of RAM)
[*]/boot*: 1 GB (Is there any way to check if I need this or not? Will I e.g. be told in the installer?)
[*]BIOS-Boot/EFI*: <=250 MB (I see there is a terminal command for checking if I need this or not. Would it also tell me which I need?)
[*]Shared: >100 GB (I see [here]("http://askubuntu.com/questions/432447/windows-7-ubuntu-dual-boot-with-shared-data-partition?rq=1") that Ubuntu can access the Windows partition. Would it then be advisable to simply use that drive instead of creating a new one?)
[*]Windows: 250-300 GB (I have 170 GB currently, but I'd like to leave a buffer for games. 250 GB would probably suffice.)
[*]Lenovo Recovery: 17.5 GB
[/LIST]
*I'm a bit concerned about these, at the link says they have to be located at the start of the disk. Would this pose a problem when I already have Windows installed?

Any advice would be greatly appreciated. Thanks!

---

### Post by yancek on 2014-10-04
15-25GB should be enough for the root filesystem of Ubuntu.  4GB of swap should also be more than enough in most cases.  You need to check to see if the windows 7 uses UEFI/GPT in your BIOS.  Probably not.  You need to install Ubuntu in the same manner, if you are using MBR for windows 7, use MBR for Ubuntu and vice versa.  A separate boot partition is not needed for Ubuntu unless it is a very old machine.  The UEFI partition is only used if you are using GPT/UEFI for windows.  If you already have an ntfs data partition, you can access it from an installed Ubuntu system.

---

