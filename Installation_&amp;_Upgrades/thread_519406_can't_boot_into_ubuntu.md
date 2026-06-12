---
title: "can't boot into ubuntu"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by Taleman on 2007-08-07
Ok here's the issue, I was installing ubuntu and winXP on separate partitions (dual boot). Normally this works out fine but this time without thinking I installed Ubuntu first and windows much later. Anyway after installing windows i cant boot into ubuntu. I know i didn't override ubuntu  because i can still see the partition in the live cd. Is there anyway I can get the ability to boot into ubuntu back?

---

### Post by benanzo on 2007-08-07
This is a common problem if you install Windows after *anything*.  Windows does not respect the possibility that the user might have other systems (including other Windows versions) installed on the same drive.

You just need to reinstall **grub** to the MBR of your hard disk.  [Here's]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") the Ubuntu help article detailing how to recover from this scenario.

---

