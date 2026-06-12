---
title: "Transfering a user"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Babica on 2007-11-08
I have to reinstall my Ubuntu(7.10) because one day just started giving me segmentation fault on boot. (sometimes the system starts and sometimes it doesnt)
Is there a way, to save all my settings, programs..in fact all the changes that i made since the last installation?

..or has anybody a better idea how to solve the problem? (only if its not a to hard way..im only using linux for 2 months now:)

---

### Post by taurus on 2007-11-08
If you have a separate partition for /home, then you just mount that partition to /home again when you reinstall it, without reformatting /home.  But if you don't, then you need to back up /home before you reinstall.  After you have reinstalled, just copy the backup back to /home again and you will have all your settings when you log in.

---

### Post by Babica on 2007-11-08
I've been using a laptop, so I needed to set up the touchpad (not in a file that is in my home dir) and if I only backup the /home this configuration will be lost..wont be?!

---

