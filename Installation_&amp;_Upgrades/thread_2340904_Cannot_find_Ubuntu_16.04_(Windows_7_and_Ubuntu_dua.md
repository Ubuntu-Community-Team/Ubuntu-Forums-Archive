---
title: "Cannot find Ubuntu 16.04 (Windows 7 and Ubuntu dual boot)"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by yukteshwar2 on 2016-10-22
Hi, 
I am a new for Ubuntu and I too have similar issue. I generated bootinfo summary and accessible through following link.
[https://dl.dropboxusercontent.com/u/78968516/New.txt](https://dl.dropboxusercontent.com/u/78968516/New.txt)

Please, have a look and suggest how to get a list of OS to select at the time of boot.

Thanks

--
Yukteshwar

---

### Post by howefield on 2016-10-23
Post moved to own thread.

---

### Post by ajgreeny on 2016-10-23
You have grub installed into the partition sda3 which is not the correct place for it; it should be in the MBR of sda, neither do you have a grub.cfg file on sda anywhere, so those two facts are why you can not get Ubuntu to boot.

I think that you need to run Boot-Repair again and accept the default repair offered, which will put grub in the MBR of sda, not the partition where it is now.

I am assuming you can still boot to Windows, and if that is the case I recommend you to ensure you have the repair disks (or install DVD) for Windows 7 before you do anything more as installing grub properly will remove your current Windows bootloader and replace it with grub.  Unfortunately I do not know how you create the repair disks for Win 7 as I no longer use Windows.

---

