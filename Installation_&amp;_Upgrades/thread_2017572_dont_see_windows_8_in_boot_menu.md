---
title: "dont see windows 8 in boot menu"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by disco_kiza on 2012-07-05
[http://paste.ubuntu.com/1076958/](http://paste.ubuntu.com/1076958/)

I had ubuntu installed on 500gb hdd and then i installed win8 on another 80gb hdd
Later i read that i needed to install win first so i left win on 80gb and installed new ubuntu again on my 500gb. 

Now when boot menu (grub) pops up it has ne win8 on it.

Sorry for my bad english :(

---

### Post by YannBuntu on 2012-07-05
Hello
Your Windows has some boot files missing (/Boot/BCD and maybe more).
Use a Windows Repair CD to repair it, then use Boot-repair to recover the GRUB menu.

---

### Post by oldfred on 2012-07-05
We have seen where the BIOS boot drive is sda and an install of Windows to sdb drive, Windows then puts a small hidden 100MB boot/repair partition on sda. Did you have a small NTFS 100MB partition on sda?

Windows really likes to be on sda & the first partition of sda, but does not have to be. But it then does some things you have to be aware of.

Ubuntu does not care. So I would make the 80GB drive sda and set BIOS to boot from that, and install the Windows to that or repair your current install of Windows.  Then with grub2 in sdb, you can set BIOS to boot sdb and sudo update-grub will find Windows and let you boot either. If you ever have issues you can set BIOS to boot sda & you can directly boot Windows.

If dual booting you may want to change some settings in Windows 8.
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

