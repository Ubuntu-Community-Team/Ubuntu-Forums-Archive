---
title: "installed Ultimate 3.2 and can get startup menu"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2012-04-15
I installed Ultimate 3.2 version of Ubuntu and have tried everything to get the startup menu. I have used the Boot Repair disk have reinstalled the MBR and also reinstalled Grub.  I have also tried the sudo mount /dev/sda6 /mnt and sudo grub-install --root-directory=/mnt/ /dev/sda, but still no start menu. I can start up on windows 7 if I reinstall the mbr or start up unbuntu if I reset grub. but no start up menu either way.

---

### Post by lindsay7 on 2012-04-16
solved by this,

[http://forums.scotsnewsletter.com/index.php?showtopic=45226](http://forums.scotsnewsletter.com/index.php?showtopic=45226)

olved Grub Menu Not showing in Dual Boot with Windows 7 is SolvedFor any of you in the forum having a problem with Grub Menu not showing in Ubuntu 11.04 Here is a simple fix.If you are dual booting and need the grub menu (of course you do). Then open a terminal and do the following:code

Quote
sudo gedit /etc/default/grub
un-comment the line that says #GFX640x480 by removing the # sign. Save the file and in the terminal type code

Quote
sudo update-grub

---

