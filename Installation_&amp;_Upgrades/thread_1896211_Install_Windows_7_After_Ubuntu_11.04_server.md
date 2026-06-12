---
title: "Install Windows 7 After Ubuntu 11.04 server"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by Xiao2011 on 2011-12-16
I just installed Windows 7 Professional 64 after Ubuntu 11.04 server 64bit. But I can not see Ubuntu in boot menu. My machine just boot into Windows. I use Boot-repair to generate a boot info. You can check it here.
[http://paste.ubuntu.com/772374/](http://paste.ubuntu.com/772374/)

---

### Post by 2F4U on 2011-12-16
Windows destroyed Grub and placed its own bootloader into the MBR. This is a well known behaviour. If you want grub back into the MBR, here is a tutorial on how to do that.

[https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu_after_Windows](https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu_after_Windows)

---

### Post by N00b-un-2 on 2011-12-16
[http://ubuntuforums.org/showpost.php?p=11540647&postcount=4]("http://ubuntuforums.org/showpost.php?p=11540647&postcount=4")

---

