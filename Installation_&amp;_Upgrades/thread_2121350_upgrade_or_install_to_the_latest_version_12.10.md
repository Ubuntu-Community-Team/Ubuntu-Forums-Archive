---
title: "upgrade or install to the latest version 12.10"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by philpaq on 2013-03-01
Hello @,
I want to install Ubuntu 12.10 on an HP laptop dv4000.
Using the 12.10 without installation does not work. It simply results in a blanc screen.
So I tried 10.04.3 LTS. It does work without the install. But if I install than the installation stops with a brown screen without text.
So I tried 7.1 here the distro works without install and with installation.
Than upgrading to 8,04 LTS works fine.
Than upgrade to 10.04.3 works but halts with the message configuring 'dbus'. Than the screen turns brown. Disk activity during 1 hour and the system halts.
Reboot and/or recovery does not work. The error message is 'kernal panic not syncing out of memory and no killing process'.
Can someone help to upgrade? Or to directly install 12.10?

FYI I created an ext3 partition (20 GB) and a swap file (2GB) together with windows XP (38GB) on one harddisk of 60 GB and I have 1 MB or RAM memory on an intel processor.

Thanks in advance to help me?

---

### Post by grahammechanical on 2013-03-01
Try booting into a Live Session from the 12.10 disk. and do this

1) at the first purple screen press Enter.
2) at the next screen press Enter to select English as the default language (or select some other language)
3) at the Try - Install screen press F6 and from the drop down menu select nomodeset and press Enter
4) press ESc to get back to the Try - Install screen and press Enter to go to a live session or scroll down to Install Ubuntu and press Enter.

See what happens. You may even need to select some of the other options in that F6 menu to get to a live session.

Regards.

---

