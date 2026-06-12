---
title: "Upgrading to Windows 8 -- GRUB Issues to be Aware Of?"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by iaskedalice09 on 2014-03-09
I am currently running Ubuntu GNOME alongside Windows 7. i am wanting to upgrade to Windows 8.1 but worry about it screwing up the GRUB menu. Any issues to be aware of?

bobby

---

### Post by Mark Phelps on 2014-03-09
It's very likely that your upgrade will overwrite the MBR and from then on, you will boot directly into Win8.1.  But, you can easily fix that by reinstalling GRUB from the Ubuntu install media.

---

### Post by oldfred on 2014-03-09
Also, if dual booting turn off fast boot:
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

