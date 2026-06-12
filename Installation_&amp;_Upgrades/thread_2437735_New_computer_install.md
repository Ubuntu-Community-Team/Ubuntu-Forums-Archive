---
title: "New computer install"
date: 2020-02-28
forum: Installation &amp; Upgrades
---

### Post by hopkinsfd on 2020-02-28
I just bought a acer tc-885 with windows 10.  I was wanting to have dual boot on it.  I have tried 16.04.6 and 18.04.4 and cant get eather one to install.  It all works great tell it looks for the root and then there is nothing.  I tried putting a unallocated piece In the hard drive but that didnt help.

Thanks

---

### Post by CelticWarrior on 2020-02-28
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

This should be applicable to yours. 
There's no point in installing 16.04 now. 18.04 is the current LTS release but a new one - 20.04 - will be released in April (you can install it right now if you want). But in any case you will need to follow the guide above to prepare the system before attempting to install.

---

### Post by yancek on 2020-02-28
Do you have fastboot and anything related to hibernation OFF in windows.
Newer Acer machines with windows 10 pre-installed require you to set a supervisor password in the BIOS firmware and enable trust before you can install another OS.

---

### Post by VMC on 2020-02-28
I have one of those TC-885's. God to Windows Disk Management and shrunk down the partition enough for Linux partition and swap partition. Then with bootable usb create partitions using gparted.

---

