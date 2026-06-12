---
title: "Unable to boot 18.04LTS on my new lenovo V145-V15 AST"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by aldo82 on 2020-07-29
I have just installed Ubuntu 18.04  LTS.  The installation was successful, but
 the problem now is there is no boot system. "No filename received"
I checked  the disk, it is ok. So, what to do?

---

### Post by oldfred on 2020-07-29
Did you install in UEFI boot mode?
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 


Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If very new system, you may need 20.04 to get very latest kernel, drivers & support software.

Have you updated UEFI from Lenovo, even new systems may need an update.

---

### Post by aldo82 on 2020-07-30
Solved. On the lenovo notebook there was no booting system.So
I simply reinstalled  18.04 LTS, and It worked.

---

