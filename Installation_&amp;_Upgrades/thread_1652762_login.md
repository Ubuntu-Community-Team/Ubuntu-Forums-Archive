---
title: "login"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by techdoc48 on 2010-12-25
I tried to upgrade from 10.4 to 10.10.  Every thing went normal until the grub screen wanted me to select which kernel.  The wireless usb keyboard and mouse would not work.  I found an old keyboard and mouse, they worked.  the login screen popped up, I selected the user name and typed the password.  After a moment the login screen pops back up.  I can log into the recovery console.  I am lost at this point.  Any answers anyone?

---

### Post by AbeJarano on 2010-12-25
Try Ctrl-F1, then login,  then
mkdir 1
if it says a readonly system then /etc/fstab has to be fixed, otherwise try
sudo rm /etc/X11/xorg.conf
sudo service gdm stop
sudo service gdm start, otherwise I don't know.

---

### Post by techdoc48 on 2010-12-25
Thanks for t he replay.
When I stop things I get a rainbow across the screen and it is locked up. Power down reboot required.

---

