---
title: "Grub error17 - Grub only loads with WinXP CD in drive"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by BoxCar on 2005-11-19
I'm relatively new to Linux and decided to give Ubuntu a go. From what I've seen I like it but I've got a problem.

I installed Ubuntu on an empty hard drive in my computer and **installed Grub to the MBR of my primary drive (a Windows partition)**. However, on reboot after the installation I received a **Grub error 17** message and the machine halted. After tinkering for a while I noticed I was able to get **Grub to load only when the Windows XP CD was in the CD-ROM drive**.

Once Grub loads I have no problems booting into either OS. Below is the relevant information (i think).

IDE Channel 0 Master - Western Digital 30GB (Windows XP Install) - /dev/hda
IDE Channel 0 Slave - Western Digital 20GB (Ubuntu Install) - /dev/hdb
IDE Channel 1 Master - CD-RW - /dev/hdc
IDE Channel 1 Slave - DVD-RAM - /dev/hdd
IDE Channel 2 Master - Western Digital 160GB (NTFS File System, used as storage) - /dev/sda

And the mappings are

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda

Any help that you could provide would be greatly appreciated.
Cheers.

---

### Post by matthewv on 2005-11-19
You could try a reinstall of grub:
from ubuntu:
```
sudo grub-install /dev/hda
```

---

### Post by BoxCar on 2005-11-19
I just tried reinstalling Grub as you suggested. Gah - I'm still getting the same error message.

Any other ideas? please...

Edit: Here's some more info, hope it helps [http://www.ubuntuforums.org/showthread.php?t=92537]("http://www.ubuntuforums.org/showthread.php?t=92537").

---

