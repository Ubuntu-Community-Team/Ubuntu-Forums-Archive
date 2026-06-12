---
title: "Deleting from registry"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Ccc56 on 2011-06-19
I had a hard time deleting Wubi from Windows 7.

To make sure it all got off, I want to manually check and delete anything Ubuntu and/or Wubi related from my registry, since I did a full install.

What/where do I need to look?

Thanks.

---

### Post by Rubi1200 on 2011-06-20
Hi,
the instructions here include options to clean the registry:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

### Post by Ccc56 on 2011-06-20
Ubuntu/Wubi is not showing up in the program list and it is not in that registry key. However, I am still seeing the Ubuntu option at startup, so I know there is something else that hasn't been gotten rid of yet and the Uninstall-Ubuntu.exe will not download correctly for some reason.
 
Thanks.

---

### Post by Rubi1200 on 2011-06-21
The only other thing I can think of is to edit the settings as described here:
[http://www.howtogeek.com/howto/windows-vista/easily-set-default-os-in-a-windows-vista-and-xp-dual-boot-setup/](http://www.howtogeek.com/howto/windows-vista/easily-set-default-os-in-a-windows-vista-and-xp-dual-boot-setup/)

Basically, you need to remove the entry for Wubi from the menu.

This is from the Wubi Guide:

> In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

