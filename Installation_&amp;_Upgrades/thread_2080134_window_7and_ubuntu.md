---
title: "window 7and ubuntu"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by ebn on 2012-11-03
How can I install window 7 along with ubuntu 10.04?
 Now I am using ubuntu 10.04 as my operating system.I tried to install windows 7 along with ubuntu and failed to install windows.It asks for NTFS partition and  for windows installer.How can I solve the problem,please help me

---

### Post by Bliepo32 on 2012-11-03
A quick rundown would be: make a NTFS partition for win 7 and one ext partiton for Ubuntu (two if you want to have a sperate home partition). Then install Win 7 first, the install Ubuntu.
If you want to have a guide, here it is: [https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)

---

### Post by Bucky Ball on 2012-11-03
*Moved to **Installation & Upgrades***

---

### Post by oldfred on 2012-11-03
Windows has to boot from a primary partition (sda1 thru sda4)  formatted NTFS with the boot flag.

You will need an Ubuntu liveCD to reinstall grub2's boot loader.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

