---
title: "ATI X1200 Problems - 7.10"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by chessiv on 2008-03-23
The video card works fine with the vesa driver which is what the install chooses.  I need to set a custom modeline.  When I set the modeline it's ignored by the vesa driver.  So I tried to install the fglrx driver.  It installs fine but when I reboot and the GDM tries to start I hear the monitor click several times (I assume it's trying to determine modes) then the screen stays blank.  I can get to the root terminal so the machine isn't locked up but I can't make the driver work.  I have another machine with an X1250 integrated card and it works fine with the fglrx driver.  

I'm puzzled.  If anyone can help me solve either problem:

Get the fglrx driver working OR modeline working with the vesa driver,  I would greatly appreciate it.

---

### Post by dstew on 2008-03-23
Unfortunately, the fglrx driver does not work reliably in all Linux system, even though the same card is there. The card is only half of what the driver interacts with, the other half is the rest of the computer system. [This document]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") gives some advice on that driver, if you haven't seen it yet.

If the installation chose the vesa driver, that might be the best you can do. That driver does not have much capability (no 2D or 3D acceleration) but it gets you a functional desktop. I do not know if the open-source ati driver will work with that card. If it did, it should have been installed. But, you can [look here]("https://help.ubuntu.com/community/RadeonDriver") for possible tweaks if you can get the ati driver going.

To reconfigure your xserver if it gets messed up, use```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by observative on 2008-04-09
If you post your xorg.conf file it will help in any determination of a solution for you.

---

