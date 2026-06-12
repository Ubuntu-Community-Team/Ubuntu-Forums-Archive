---
title: "can't download updates"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by fboxall on 2008-06-11
I have installed ubuntu within windows XP and it seems to be working well.  When I try to download updates or try to install a program from add/remove I get this message 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a'  E: cache-> open()failed, please report.
So I went to the terminal command box and entered dpkg --configure -a and got this reply dpkg: requested operation requires superuser privilege.  I suppose superuser is administrator and I am the sole user and administrator.  So I don't know what to do. Please educate me.
Frank

---

### Post by iaculallad on 2008-06-11
On your terminal:

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by fboxall on 2008-06-13
Many thanks to iaculallad.  Your instruction solved my problem.

---

