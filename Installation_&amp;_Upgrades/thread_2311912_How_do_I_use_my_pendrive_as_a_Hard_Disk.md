---
title: "How do I use my pendrive as a Hard Disk?"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by guilhermebidarra on 2016-01-31
I want to Install a Linux distribution on my Pendrive so I can go to another computer and still using my Operative System with my things (files...).

What I should do?








(sorry for my english)

---

### Post by sudodus on 2016-01-31
You can install Ubuntu or another Ubuntu flavour like it were an internal drive. Avoid proprietary drivers! You can add the boot option noatime to the root partition (in the file /etc/fstab).

See this link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

You may have problems, if the computers are too different, and there may be problems in UEFI mode with installed systems that get corrupted. The following link might solve that problem.

[Stable portable systems - good for USB sticks](https://help.ubuntu.com/community/Installation/FromUSBStick#Stable_portable_systems_-_good_for_USB_sticks)

---

### Post by ajgreeny on 2016-01-31
It is essential that you install using the "Something Else" option when you get to the partitioning/disk preparation stage.
If you do not choose that option there will be no way that you can make sure that grub is put on the USB drive rather than the machine's internal hard disk, which you definitely do not want.

---

### Post by C.S.Cameron on 2016-01-31
It is safest to unplug your internal hard drives before installing Ubuntu to your pendrive.
You can then install as normal, or use "Something Else" if you want to do fancy partitioning.

---

