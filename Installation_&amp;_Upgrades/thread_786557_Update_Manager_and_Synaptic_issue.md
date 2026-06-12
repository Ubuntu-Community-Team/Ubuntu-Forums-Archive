---
title: "Update Manager and Synaptic issue"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Jasemps on 2008-05-08
Hi guys

I upgraded from 7.10 to 8.04 recently and both Update Manager and Synaptic have stopped working outside of terminal initiation.

If I try to use either from the GUI menu (or for update manager its "updated available" icon) the applications start but hang with a minimised stub "Starting Administrative Application". It never gets to displaying the password entry dialog box. 

Any ideas how to fix this ?

Thanks

Jase

---

### Post by joselin on 2008-05-08
Try to
```
sudo dpkg --configure -a
```
to let the system configure all unconfigured packages and then retry update manager.

Regards

---

### Post by Jasemps on 2008-05-10
Thanks for the suggestion, alas it didnt work and im still having the same issue with both Update Manager and Synaptic.

I did notice that when running that command i got the message:

sudo: unable to resolve host hostname

and then it prompted me for my admin password. 

Completely removed update manager and reinstalled it and still no go ... will just run aptitude when update notify puts its icon in the bar.

Thanks anyway.

---

### Post by Pumalite on 2008-05-10
Check /etc/hostname. This is mine:
pumalite-desktop

---

### Post by Jasemps on 2008-05-13
Yep my hostname file is correct ... i think the 8.04 upgrade may just have borked :(

---

