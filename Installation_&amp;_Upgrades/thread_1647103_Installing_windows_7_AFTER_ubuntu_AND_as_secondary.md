---
title: "Installing windows 7 AFTER ubuntu AND as secondary OS."
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by GRAYgoose12 on 2010-12-16
I currently have Ubuntu installed, but I want to install windows 7 so that I can play some games, but I do not want to change Ubuntu at all, I want it to remain as it is. 

   I think windows overwrites the GRUB bootloader and I am hoping someone could give me a step by step tutorial to revert this after windows is installed and whatever else I may need to do. 

   Thanks.

---

### Post by oldfred on 2010-12-16
Are you still running 7.04? That would be old grub legacy. New verisons of Ubuntu are using grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will have to create a primary NTFS partition and set the boot flag on for the Win7 installer to see it.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Older but discusses the issues, reinstall grub or grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

One disadvantage of grub legacy is that is does not find and create a menu stanza for win7 most times. If you need one to add to menu.lst,  I have saved several versions that usually work.

---

