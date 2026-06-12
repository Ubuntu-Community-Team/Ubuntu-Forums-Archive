---
title: "Accessing PC Angel recovery partition"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by blueskies1977 on 2010-01-25
My mum has an Iqon PC which had Windows XP preinstalled and had a PC Angel recovery partition.

As part of my ongoing quest to convert my mum to Ubuntu I installed a dual boot system a while ago.

I need now to reinstall the Windows partitition from the recovery partition as it has been destroyed by a virus but the PC Angel software crashes whenever I load it from the GRUB menu. I have tried fixmbr but this will not allow me to access the recovery software. I would really like to be able to install Windows from this without having to pay for another copy of Windows.

Any help would be greatly appreciated

---

### Post by Mark Phelps on 2010-01-25
Are you doing the stuff in the link below:

[http://www.pcrecoverydisks.com/iqon-pc-restore.html]("http://www.pcrecoverydisks.com/iqon-pc-restore.html")

If that's not working, and you have an XP CD, you can try doing fixboot as well.

You can use a SuperGrubDisk to restore a generic MS Windows MBR, but if you have an XP disk, you already have the same capability.

---

### Post by presence1960 on 2010-01-25
Boot into Ubuntu and use lilo to repair the MBR. Open a terminal and run ```
sudo apt-get install lilo
```
Once installed run in terminal ```
sudo lilo -M /dev/sda mbr
```

---

