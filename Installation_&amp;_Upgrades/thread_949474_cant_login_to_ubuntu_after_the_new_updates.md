---
title: "cant login to ubuntu after the new updates"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by le1232 on 2008-10-16
after i download the new updates(beside the non free updates) i cant login to ubuntu
anyone knows what to do with this problem?(i have a 64 bit hardy heron)

---

### Post by penguinpi.com on 2008-10-16
Can you login as root via "Recovery Mode"? When GRUB is loading press esc and select "Recovery Mode". If you can log in as root, you can change your password or check /var/log/auth.log to see why you were having login problems.

---

### Post by le1232 on 2008-10-16
i can open the recovery mode
i wrote
/var/log/auth.log  as root but i get the message "permission denied"
when i type it with "sudo"  i get "no such file or directory"

---

### Post by faisal892 on 2008-10-16
Try this

sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo startx

I hope this will help.

Regards

Faisal.

---

