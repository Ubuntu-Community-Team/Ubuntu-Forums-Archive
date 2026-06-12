---
title: "Duplicate option in Boot Loader"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-10
Each time I start my computer and enter the boot menu I have two identical options of recovery mode and regular mode. I have tried to remove them from the /boot/menu.1st file but they appear again after I reboot.

When I reboot or shutdown I use the following command (I use FVWM window Manager):

exec sudo shutdown -r now
exec sudo shutdown -h now

Can this be the reason it creates dupliacte boot enntries??

---

### Post by jdong on 2005-04-10
Hmm.....

Ok, I want you to post a copy of /boot/grub/menu.lst here (wrap it in CODE tags to make it in scrollboxes).

Next, run **sudo update-grub**.

Post the file again. See if the duplication still occurs.

---

