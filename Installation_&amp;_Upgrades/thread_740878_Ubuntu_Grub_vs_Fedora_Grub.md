---
title: "Ubuntu Grub vs Fedora Grub"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by HuXu on 2008-03-31
I just installed Ubuntu and i let it write a new MBR.  I had the fedora version of grub which allowed a splash screen as it counted down... when i attempt splash screen with the version of grub that ubuntu uses and hidden menu, i have to press esc (vs fedora grub press any key) and it doesnt show my splash image until i press esc (vs fedora grub showing it during hidden menu and when menu is shown.

How do i fix these options??

---

### Post by aashay on 2008-03-31
Looks like you have grub-gfxboot installed. Try copying[ this]("http://www.gnome-look.org/content/download.php?content=58248&id=1&tan=50774477") file to your /boot/grub and add this line to the top of the menu.lst.ls
```
gfxmenu (hd0,4)/boot/grub/58248-message.cristal
```
Replace hd0,4 with whatever your root partition is.
See if it helps

---

