---
title: "I have dual boot xubuntu + window xp"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by shabbir0052 on 2010-05-23
I have xubuntu installed in dual boot with window xp
Recently I upgraded to  xubuntu to 10.04, After the upgrade File Manager (Thunar) is not behaving correctly . After a first level of folder is opened, It does not allow me to go to the next level of folders,When I click on any folder it does not select that folder, and I am unable to proceed . Then I have to right click on the current on the top bar and open it  in the new window and from the new window I can proceed to the next level of folder. I have to repeat this for every next level of folders I have to go
Please let me know how to fix this . Do I need to reinstall the xubuntu( I think during upgrade , I mistakenly forced closed one of the window which asked be some information about grub, and that point I was told that installation may be unstable) . If such is the case, how to reinstall xubuntu, if it is already installed in dual boot with window xp

---

### Post by cbecker78 on 2010-05-23
try "sudo apt-get -f install xubuntu-desktop" to fix the installation.  or else you can drop to a different tty via cntrl+alt+F5 and run "sudo apt-get remove xubuntu-desktop" then "sudo apt-get install xubuntu-desktop" then "sudo reboot"

---

