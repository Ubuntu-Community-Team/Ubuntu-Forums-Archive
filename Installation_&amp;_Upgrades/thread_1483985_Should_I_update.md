---
title: "Should I update?"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Tanargbob on 2010-05-15
I have two Hard disks, one with Windows 7 64bit and the other with Ubuntu 9.10 64bit. 
At the moment they are both bootable with Grub. I have read that there may be some problems booting into Windows if I upgrade to Ubuntu 10.04 so I am holding off at the moment. 
I am no expert at Linux stuff, but with the video editor in 10.04, I can see less reason for ever using Windows 7. If I click on upgrade in update manager, am I likely to have a problem?

AMD 5200 X2
2 SATA HDDs
Nvidia 9800 grafix
4 Gb Ram

---

### Post by oldfred on 2010-05-15
Welcome to the forums. The main issues seem to be with instructions on installing grub to all drives, and then they present a list of all drives and partitions. Windows has essential boot files in its boot sector so if grub is installed to the windows partition it overwrites the windows boot loader. Just select sda and sdb or just sdb if your install is on sdb and install a windows boot loader in sda as a direct way to get into windows.

Some also have issues with video. I had no issue with Karmic but with Lucid I had to add nomodeset to both the installer (f6) and the first boot (kernel line edit inplace of splash & quiet). Once I had nvidia installed everything was fine.

---

