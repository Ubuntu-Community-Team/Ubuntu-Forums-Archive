---
title: "Can't remove Ubuntu partition that shows up on boot screen"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by matt119 on 2014-07-02
Hello,

I installed Ubuntu with Wubi, and everything was fine, until I wanted to remove the Ubuntu partition, and just deleted the relevant folders instead of running ubuntu-uninstall (I didn't know about it at the time). Now, whenever I boot my computer, there's the option to start either Windows 7 or Ubuntu, as before, but since the folders are deleted the Ubuntu option doesn't work. I've gone to my Disk Manager, but it doesn't show the partition there, and all the relevant Ubuntu folders are deleted from my Windows hard drive (so far as I've searched). Does anyone know if there's anything else to do to "completely" remove Ubuntu from my computer? (I wanted a fresh Ubuntu installation, so I ran Wubi again, but the boot screen just showed two Ubuntu options along with the Windows 7 one, and I properly uninstalled it the second time around. My only remaining problem is with the first "ghost" Ubuntu installation.)

Thanks!

---

### Post by Mark Phelps on 2014-07-02
Wubi does NOT create an Ubuntu partition; instead, it creates a single file (root.disk) which is stored inside an existing Windows filesystem partition.  Thus, there is no "Ubuntu partition" to remove.

---

### Post by matt119 on 2014-07-02
Oh, my bad. Thanks for the clarification.

---

### Post by oldfred on 2014-07-02
If you still see a boot option you have to mnaually edit BCD to remove it. You can use bcdEdit:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

---

### Post by matt119 on 2014-07-02
Thank you, oldfred, those links helped me fix the problem.

---

