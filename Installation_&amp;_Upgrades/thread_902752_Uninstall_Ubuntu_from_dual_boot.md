---
title: "Uninstall Ubuntu from dual boot"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by malexous on 2008-08-27
Hi, I recently installed Ubuntu 8.04 LTS Desktop Edition as a dual boot system with Windows XP Home Edition SP3. I can't get the wireless to work, therefore I have no need for Ubuntu. How do I go about uninstalling Ubuntu and then repartition Windows. I had trouble when I was trying to install Ubuntu. [http://ubuntuforums.org/showthread.php?t=862181](http://ubuntuforums.org/showthread.php?t=862181)

---

### Post by oilchangeguy on 2008-08-27
> **malexous said:**
> Hi, I recently installed Ubuntu 8.04 LTS Desktop Edition as a dual boot system with Windows XP Home Edition SP3. I can't get the wireless to work, therefore I have no need for Ubuntu. How do I go about uninstalling Ubuntu and then repartition Windows. I had trouble when I was trying to install Ubuntu. [http://ubuntuforums.org/showthread.php?t=862181](http://ubuntuforums.org/showthread.php?t=862181)

you can use gparted on the live cd. and then you'll need to restore windows master boot record (mbr). do you have a windows cd. not a system restore cd, but a windows only cd?

---

### Post by erfahren on 2008-08-27
it's good you asked before you just went and deleted Ubuntu off the partition - you need to restore your original MBR and it's much easier to do while you can boot into WinXP

go [here]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe"), get MBRfix.exe and follow the directions

you can then boot back up into the Ubuntu LiveCD and use gParted to delete the Ubuntu partition(s) and resize the Windows partition - launch it by opening a terminal and typing "sudo gparted"

---

