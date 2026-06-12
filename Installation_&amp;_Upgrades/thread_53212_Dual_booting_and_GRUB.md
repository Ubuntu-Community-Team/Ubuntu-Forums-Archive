---
title: "Dual booting and GRUB"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by Dr. Z2A on 2005-07-30
Ok so I want to have my computer dualboot Windows XP and Ubuntu.  Unfortunately I have no clue as to where to put GRUB.  I though I could put it in the MBR until i recently found that it would overwrite the windows boot loader, causing me to be unable to boot windows.  My windows partition uses the NTFS file system.  Is that a problem?  Can anyone inform me as to where I must install GRUB?

---

### Post by kosmic on 2005-07-30
You can install Grub in the MBR (hd0) there's no problem, Grub will allow you to choose what system you want to boot, Window$ or ubuntu :)

---

### Post by Xian on 2005-07-30
[QUOTE=Dr. Z2A]I though I could put it in the MBR until i recently found that it would overwrite the windows boot loader, causing me to be unable to boot windows.[/QUOTE]
It does overwrite the current MBR but it must do this to dual boot.
The idea being to then be able to boot multiple OS's including Windows.

If you have a Windows Installation CD you can revert the MBR to default.

Read [Making Your System Bootable](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-make-bootable).

Is this foolproof? Not 100% but very close.

---

### Post by jerrykenny on 2005-07-30
Yes, you should install GRUB to the mbr . . . 

It will overwrite the existing config, however your ubuntu installation should have detected that a Windows OS is present, and will add this to your options available at boot-up time.

If Ubuntu doesnt detect/add your Windows OS, you can add it yourself later by booting into ubuntu and editing the file  /boot/grub/menu.lst ,  however its very likely you wont have to.

One big Caveat !!!   back up all your files and settings onto a cd first . (and check that the CD does actually work!)

---

### Post by Dr. Z2A on 2005-07-30
[QUOTE=jerrykenny]It will overwrite the existing config, however your ubuntu installation should have detected that a Windows OS is present, and will add this to your options available at boot-up time.[/QUOTE]
I thought that it could only detect it if I was using fat32.  Im using NTFS.

> If you have a Windows Installation CD you can revert the MBR to default.
Problem is that i dont have te windows installation cd.  So I can't fix it if it goes wrong, therefore i can't screw this up.

---

