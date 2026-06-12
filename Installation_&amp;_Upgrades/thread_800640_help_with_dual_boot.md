---
title: "help with dual boot"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by dazift on 2008-05-20
Hi. i have two hard drives, one is a 40G with windows xp and about 5 years of very important files the other is an empty 20G hard drive. i have used wubi to dual boot, i used ubuntu for about 2 days and fell in love. i now want to switch to a permanent solution as opposed to the problem prone wubi version that can not hibernate i tryed to dual boot b4 and ended up erasing xp on a different computer. i now need a step by step way to set up ubuntu on the second hard drive and have a dual boot system.
i am a two day linux user so the simpler the directions the better thank you

---

### Post by iaculallad on 2008-05-20
Try this [howtoforge]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty") link. It gives detailed steps on doing a dual boot b/w Ubuntu and windoze.

---

### Post by Gio-van-I on 2008-05-20
You deleted windows in the past :s.

I guess you used an automated installer that repartitioned your first partition to a swap and ext3 partition. And thus deleting windows.

Things I want to say:
-It's always a good plan to back up before unknown operations.
-There are no tools in ubuntu to resize ntfs. So without free hard disk space you are in a twist.
-I had problems writing to ntfs partitions in the past. Might be an idea to avoid this by using fat32 for shared data disks.

Now about your situation.
Why not install ubuntu with grub on the 20 GB disk. And when you get this working the way you want add the 40GB back into your system and adding a line to grub to load windows from that disk. This way you are defenitly sure you won't delete anything from your old HD when installing ubuntu.
You can easely find documentation on how to add windows to your grub list all over the web.

---

### Post by iaculallad on 2008-05-20
Actually you can resize NTFS partition using GParted as long as the ntfsprogs package is installed. LiveCD's are already pre-built with the ntfsprogs so you could actually resize NTFS partition.

---

### Post by dazift on 2008-05-20
im probably going to sound like the biggest newb ever but whats grub?

---

### Post by DeLaNooch on 2008-05-20
Grub is a "boot loader."  A boot loader is responsible for loading the Operating System or "OS" after the startup sequence is completed.  "Lilo" is another popular boot loader. If you are dual-booting, then you need a boot loader in order to be select wich OS to boot into after startup.

---

