---
title: "Multi-Boot Help Needed"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by 4real*leb on 2008-05-16
Hello, I have recently been trying to get a quad boot situation to work. The operating systems are; Vista, XP, Ubuntu 8.04 and openSUSE. The problem is that I cannot boot into openSUSE. I am currently using the vista bootloader, however I would like to switch to GRUB and configure it for my situation. Does anyone know if this is possible and if it is, how?

---

### Post by Kevbert on 2008-05-16
I reckon it's possible if you've got two hard disks.  Firstly I'd install XP followed by Vista via the method here on one hard disk: [http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm]("http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm")
Next I'd install openSUSE on the second hard disk, followed finally by Ubuntu.
I believe you need two hard disks as you can only hard a maximum of three OS on a single one due to the partition limitations of linux (I may be wrong, but have only been able to install a maximum of three on a single drive).  Ubuntu is best installed last as when grub is installed it should recognize all the OS (if not you can always use a SuperGrub disk see [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")).    
I've got WinXP on one drive and Fedora, Kubuntu 8.04, and Ubuntu 7.10 on the other.
Good luck.

---

### Post by 4real*leb on 2008-05-16
> **Kevbert said:**
> I reckon it's possible if you've got two hard disks.  Firstly I'd install XP followed by Vista via the method here on one hard disk: [http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm]("http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm")
Next I'd install openSUSE on the second hard disk, followed finally by Ubuntu.
I believe you need two hard disks as you can only hard a maximum of three OS on a single one due to the partition limitations of linux (I may be wrong, but have only been able to install a maximum of three on a single drive).  Ubuntu is best installed last as when grub is installed it should recognize all the OS (if not you can always use a SuperGrub disk see [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")).    
I've got WinXP on one drive and Fedora, Kubuntu 8.04, and Ubuntu 7.10 on the other.
Good luck.

Thank you for the reply. There is something strange though. When I install openSUSE, Ubuntu does not detect it as openSUSE (nither does supergrub) but just as another partition. I cannot boot into it, even if I use supergrub. So I will uninstall Ubuntu, install openSUSE, and then reinstall Ubuntu as you suggested.

---

### Post by Kevbert on 2008-05-16
This post may also be of use: [http://ubuntuforums.org/showthread.php?t=539417]("http://ubuntuforums.org/showthread.php?t=539417")

---

### Post by 4real*leb on 2008-05-17
Thank you KevBert, your first suggestion worked (reinstalling the os's in that order). I currently have all of my os's working.

---

