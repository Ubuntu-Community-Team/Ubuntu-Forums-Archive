---
title: "[SOLVED] dual boot:window-no ubuntu/now ubuntu -no windows"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by shalemjale on 2008-03-27
I wanted to set up my laptop(orig. OS xp) to be a dual boot Ubuntu 7.1/xp. By an error on my part it I totally formatted the hd for 7.1. I used gparted to repartition and installed windows on a partition. After that, it only booted xp.

found this site> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
followed its directions to change MBR and now it only boots to 7.1. And I can't figure how to change the MBR to boot from either OS.
Suggestions?

pertinent info:
computer: Presario laptop v2000
me: noob w/ Linux

---

### Post by confused57 on 2008-03-27
> **shalemjale said:**
> I wanted to set up my laptop(orig. OS xp) to be a dual boot Ubuntu 7.1/xp. By an error on my part it I totally formatted the hd for 7.1. I used gparted to repartition and installed windows on a partition. After that, it only booted xp.

found this site> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
followed its directions to change MBR and now it only boots to 7.1. And I can't figure how to change the MBR to boot from either OS.
Suggestions?

pertinent info:
computer: Presario laptop v2000
me: noob w/ Linux
Open a terminal and check your partitions:
```
sudo fdisk -l
```
-l is a lowercase "L"

If your Windows is on partition #2, e.g. /dev/sda2, you can then add a Windows entry to grub:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
then add your Windows entry below the line ###END DEBIAN AUTOMAGIC KERNELS LIST:
```
title   Windows XP
root   (hd0,1)
makeactive
chainloader +1
```

If Windows is on /dev/sda3, then change the root to (hd0,2).

Quit & Save...you should have an entry in your grub boot menu that will boot Windows.

---

### Post by shalemjale on 2008-03-27
Bless you!!! That did the trick.:biggrin:

---

