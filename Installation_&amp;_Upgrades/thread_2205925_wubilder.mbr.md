---
title: "wubilder.mbr"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by omar7 on 2014-02-16
hello
i'v installed ubuntu in duel boot with windows 7 using wubi ;after that i reinstalled windows without uninstalling ubuntu first i'v just delete it as an ordinary folder,so i had this message when i'v rebooted the system
fichier : /ubuntu/winboot/wubilder.mbr
statut : OxcOOOOOOf



I'v already installed another ubuntu with the new installed windows.

please help.
thx.

---

### Post by oldfred on 2014-02-16
If your reinstall did not write a new BCD, then you may have old entry. In Windows you can use bcdedit to remove extra entry.

 [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

---

