---
title: "Kubuntu / Windows 2003 Installation problems"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by QuinRiva on 2006-08-14
I am having difficulty getting Kubuntu to run on my desktop machine post install.  After I install Kubuntu (Dapper Drake 6.06 /AMD64) and then reboot my machine, it promptly loads Windows.

My machine details:
Opteron 165
DFI LanParty SLI-DR Extreme
XFX GeForce 7800GT
Windows 2003 SP1

Currently I have 5 hard drives.
Seagate 320Gb 7200.10 – Partition 1 (8Gb, Primary, NTFS) Windows 2003, Partition 2 (remainder Gb, Primary, NTFS) Data
Samsung 250Gb – Partition 1 (2060 Mb, primary, swap-file) /Swap, Partition 2 (6Gb, primary, ext3) ‘/’ linux root, Partition 3 (remainder, primary, NTFS) Data (I may change this to ext3 if I need to)
Seagate 250Gb 7200.8 – Partition 1 (2060Mb, primary, NTFS) Primary Windows Pagefile, Partition 2, (Remainder, Primary, NTFS) Data
Seagate 160Gb 7200.8 – Partition 1 (All, primary, NTFS) Data
Seagate 80Gb – Partition 1 (2060, primary, NTFS) Secondary Windows Pagefile, Partition 2 (remainder, primary, NTFS) Data

Thus linux reports
	sda1, sda2, sdb1, sdb2, sdb3, sdc1, sdc2, sdd, hda1, hda2 respectively

From above you should realise that windows is sda1, the swap-file is sdb1 and the root directory is sdb2.

After installation of linux (to sdb2) and then rebooting, forcing my motherboard to boot from the Samsung drive (sdb) the bios reports ‘cannot find system disk’.  I do not believe that this is an issue relating to having the system located after the swap-file given that I have a high end new motherboard and that it was happy to load Windows when I previously had it installed on partition 2 (basically the same way Kubuntu is installed now).

I tried to manually install GRUB onto the sdb1 or sdb2:
Boot from Live CD and then sudo into root and tried to mount sdb1 or sdb2, however I received a ‘drive does not exist in fstab or mstab file and indeed it doesn't.  How do I add the drives to fstab/mstab and how/where do I install grub.

Anyway I am a complete noob and have no idea how to fix.  Every set of instruction I’ve used to correct this problem has failed.

Thanks for any assistance.

---

### Post by QuinRiva on 2006-08-15
bump

---

### Post by seshomaru samma on 2006-08-16
How did you try to install grub?
Did you try :
```
sudo grub
find /boot/grub/stage1
```
replace the question marks with whatever output you got from the last commandt (in my case it was hd0,1):
```
root (hd?,?)

```
and then:
```
setup (hd0)
quit
```

does that help?

---

### Post by QuinRiva on 2006-08-18
Tried all that.
Every thing went fine, then when I restarted Windows loaded up, no grub.  Forcing the comp to boot from the linux drive (via BIOS) caused the following error.

Error. Could not load operating system.

---

