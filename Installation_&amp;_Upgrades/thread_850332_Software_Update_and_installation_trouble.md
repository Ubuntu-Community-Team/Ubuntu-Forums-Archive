---
title: "Software Update and installation trouble"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by jasgaravito on 2008-07-05
I just installed ubuntu in my pc and saw that Nelson Mandela video, and well I'm really impressed, the ubuntu philosophy is now part of me:)

I installed ubuntu in a 13 Gb partition (aprox) in an hp pavilion ze5417la, and everything was fine, I checked the update manager and downloaded about 223 new updates, I left the computer downloading and installing them, but when I came back the display was blank and whatever I thought to turn it on, it didn't respond. 
So I forced my computer to shutdown and started it again, exploring ubuntu I checked the Add/Remove application and when I try to install or uninstall something it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


How do I manually run that thing? What happened? and how do I report this problem? I'm completely new to this software so please give an easy-to-understand answer 

This is also my first entry on a forum so I don's know much about this. Again I'm impressed for all your efforts and support.

Thanks!

---

### Post by Midwest-Linux on 2008-07-05
Open the terminal, type in 

dpkg --configure -a

and hit enter.

---

### Post by CatKiller on 2008-07-05
Probably wants to be ```
sudo dpkg --configure -a
``` The Terminal is in Applications -> Accessories -> Terminal.

---

### Post by Midwest-Linux on 2008-07-05
> **CatKiller said:**
> Probably wants to be ```
sudo dpkg --configure -a
``` The Terminal is in Applications -> Accessories -> Terminal.

Thanks...I should have mentioned that.

---

### Post by jasgaravito on 2008-07-10
Thanks, I formatted the partition and reinstalled ubuntu cause it was the easiest for me.
Also when I entered the code you told me, it said something like that was not possible because I was not a super user.

---

