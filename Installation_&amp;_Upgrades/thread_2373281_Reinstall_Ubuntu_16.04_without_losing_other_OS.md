---
title: "Reinstall Ubuntu 16.04 without losing other OS"
date: 2017-10-04
forum: Installation &amp; Upgrades
---

### Post by SazquatchWNC on 2017-10-04
I have been running Ubuntu alongside Windows 10 which is my primary OS.  The last time I tried to boot to Ubuntu I got a solid blue screen and was apparently locked out of the computer.  I am able to reboot to Windows by using the power switch to shut down and restart.  I would like to reinstall Ubuntu without disturbing my Windows installation.  The installation disk I have does not offer this option.  Thanks for any assistance or comments.

---

### Post by TheFu on 2017-10-04
Sometimes, Windows update trashes the boot manager that works for both OSes.
Ubuntu uses grub to manage booting all OSes.  Reinstalling grub and telling it to update the list of installed OSes should be sufficient to getting the old 16.04 back - no reinstall needed.

There is a tool - "Boot Repair" - to make that easier.  It isn't perfect and gets confused when there are multiple storage devices connected.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by RobGoss on 2017-10-05
I would also make a complete backup of your Windows partition just in case something goes wrong data important files and so on

Take Thefu advise and try using the boot repair tools it may save you some time

---

