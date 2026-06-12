---
title: "GRUB Trouble!!!!!"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by mattingy on 2005-07-27
I have successfully installed Unbuntu 5.04 and GRUB. However I also have Windows ME installed. I wish to make Windows boot by default but cannot find out how, please help! And also is it possible to replace GRUB with LILO?  :???:

---

### Post by super on 2005-07-27
if you edit your grub menu.lst you can change the default OS. type the following from a terminal:

[FONT=Courier New]sudo gedit /boot/grub/menu.lst[/FONT]

near the beginning of the file there should should be a line labeled [FONT=Courier New]default[/FONT] change the number that follows to the number that corresponds to the position of the Windows entry on the menu and that should be all.

yes you can swith to lilo but grub is much better and switching is not worth the trouble.

---

