---
title: "Installation Doesn't Find Windows 10"
date: 2019-03-29
forum: Installation &amp; Upgrades
---

### Post by jgpfersich3 on 2019-03-29
I downloaded Ubuntu 18.04.2 and installed it on a USB stick. Tried to install it on a Dell Inspiron 3670. I got to the screen where the process scans the disk. It didn't find any other OS. Anybody else see this problem? I don't want to wipe Windows, but I also don't want to manually set up the partitions if I can help it.

---

### Post by CatKiller on 2019-03-29
Windows' Fast Boot option (which is on by default, and gets re-enabled by updates) means that the computer never properly shuts down. It hibernates, and marks the NTFS partitions as in-use. Ubuntu won't touch them, or display them, or do anything with them, since any changes at all to those partitions would leave the Windows install broken. Turn off Fast Boot in Windows and they should appear.

---

### Post by yancek on 2019-03-29
I would suggest you read the Ubuntu documentation on dual booting with windows 10 at the link below before beginning.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-03-29
In addition to above:
Dell typically has drive set for RAID, not AHCI.
       Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 
    
Similar Dell models:
       Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)

---

### Post by jgpfersich3 on 2019-04-04
I already had fast boot disabled. I read the UEFI doc and decided to try the UEFI mode based on that  article. It worked. The Dell doc I was running from is a little  outdated. Maybe I'll do my own writeup, but it seems, everytime i  install Ubuntu, it's something different to do. Thanks for the tips.

By the way, here's the screen you get when you hit F12 when you start up the computer. (Pic not inserted because this BBS doesn't deal with pictures And yes it is a BBS, how quaint)

---

### Post by oldfred on 2019-04-04
If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 
    
Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

