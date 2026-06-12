---
title: "Ubuntu installation doesn't recognize Windows OS"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Adrian Sarmas on 2010-08-13
I had some problems with a dual-boot Ubuntu-Win XP. ]After I made some changes to Xorg.conf and other system files (I'm not too smart, I know), Ubuntu only booted in text mode. I tried everything I knew or found on the Internet to start in GUI mode, but with no luck. So I decided to uninstall Ubuntu and to reinstall it, without affecting Windows XP (if possible). I ended up with a system that didn't boot anymore from the hard disk. It could boot from a CD (I could use the Ubuntu Live CD), but when trying to boot from hard disk it hanged right before the Grub menu should appear. Next I reinstalled the Windows Xp over its old partition (I just formated it) and it works (the Grub menu does not appear anymore). I want to reinstall Ubuntu to get back to the old dual mode, but when I start the installation program, it doesn't find the Windows os. It says the I have an empty harddisk and that I should format it all. Gparted (from the live cd) only shows an unallocated space. System>Administration>Disk Utility shows that the partitions are there but there seem to be some problems. I have an NTFS logical partition which seems to be outside the extended partition. Also there is an unallocated space I dindn't knew about. The Disk Management in Windows doesn't show any problem. I also deleted the Ubuntu partition and the swap partition from the Disk Management in Windows. I guess I might messed up everything.

What should I do to reinstall Ubuntu and get back to the old dual-mode?

Sys info:
Intel Celeron @ 2Ghz
Video VIA Chrome9
RAM 1 GB
HDD 160GB

***This is the way the partitions looked before I started to make changes, the old dual-boot WinXp-Ubuntu10.04***
[I]-Win XP 21GB
-Ubuntu partition(Ext4) 8.3 GB
-Swap partition 430 MB
-Logical partition(NTFS) 120GB[/I]

---

