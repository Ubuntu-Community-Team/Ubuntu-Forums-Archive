---
title: "Grub Error 22 upon startup after installation"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by HæroicRaptor on 2005-11-30
After Ubuntu installed and it said that it had to reboot to finish the installation, I removed the install cd and let it reboot. Then I get this message:
[quote="Error Message"]
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22[/quote]
Can anyone help me with this problem? Also, when I was installing I kept getting an error about the boot loader, so I finally made it install as the non-main boot loader, and after it finished installing that, I went back to try installing it as the main boot loader and it worked. I think that might be my problem, but I'm not sure.

---

### Post by amohanty on 2005-12-01
Search the forums for:
Grub 22

then look here:[http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)

For more GRUB info:
[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

scroll down to 22

Basically your partition table is messed up, follow the howto to restore it.

HTH
AM

---

