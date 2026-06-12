---
title: "install to usb, now will not boot w/out usb, cannot access recovery console"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by ranchersd on 2008-08-01
I have seen threads that help explain some but not all of my issues.

I installed Ubuntu to a USB drive attached to my ibm r51 laptop. After installation, I get the Error 21 if I do not have my usb attached AND my XP install disc in the CD tray. After the "press any key to install" message times out from the XP install disc, then, and only then, do I get my grub boot menu with Ubuntu and XP options.

Ultimately, I would like to default boot to XP if the usb is not attached (without needing the XP disk in the tray).

Right now, I cannot get out of this installation quagmire. I am unable to access my recovery console to run fixboot and fixmbr. The recovery console is not accepting my administrator password. I have changed the password and then tested by booting to safe mode to make sure the password is correct but my recovery console insists says the password is wrong. Not sure how this can be but it is the situation. 

I am fortunate to have a very recent bare-metal back of my laptop but I am not certain of its value as the bios is looking for grub if my suspicion is right. If I am not able to resolve my boot order problem and need to resort to the bare-metal backup, will my bios be fixed by going to default settings. That is, if I can access my bios which I have not tried yet.

Any help would be greatly appreciated.

---

### Post by awam66 on 2008-08-01
It looks as if you have your grub installed on the USB drive. Try reinstallig grub to your windows MBR.
Can't remember how to do it exactly but there are plenty of threads explianing how.

---

