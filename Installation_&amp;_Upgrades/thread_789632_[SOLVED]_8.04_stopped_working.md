---
title: "[SOLVED] 8.04 stopped working"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by socngill on 2008-05-10
Hi guys.

I have come back to test the new version of Ubuntu to see how it fares compared with the old one - but I have hit a problem.

First some background - I mounted the ISO and chose the "install in Windows" option.  After a short while the system installed and everything was hunky dory.  I rebooted the system, it gave me the duel boot screen, I selected Ubuntu and up it came - excellent.

The first thing it did was tell me that I needed an updated driver for my ATI graphics card.  So I installed the updates and also installed the system updates and rebooted.  however, this time it hung on me.  I left it for a good 10 minutes in case it was doing something in the background, but in the end I restarted, and now it won't run - it just comes up with error messages - something unavailable.

Anyhow - I can't find a separate partition to delete it and start again - but I am assuming that's because it has inbeded itself inside the Vista installation.  So firstly, can the problem be fixed, secondly any ideas what will have caused it (so I don't do it again) and thirdly, do I just delete the Ubuntu folder in Vista to uninstall and start again?

EDIT: The error message that come up is this:

Find--set-root--ignore-floppies/ubuntu/install/boot/grub/menu.lst
Error 15: File not found

---

### Post by socngill on 2008-05-12
Nobody else had this problem, or know how to fix it?

---

### Post by bobnutfield on 2008-05-12
Installing inside of Windows does not give you the complete functionality of a hard drive install on a separate partition.  I am guessing that installing the ATI drivers has pevented it from booting.  I would go into Windows and UNINSTALL (it gives you that option in a WUBI install, don't just delet the folders or you will leave the grub boot menu there.)  Start again and don't install the ATI drivers.

Bob

---

### Post by socngill on 2008-05-12
Many thanks - i'll give that a go.

---

