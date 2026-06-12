---
title: "Having problem installing new applications."
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by 123bjrnar on 2007-07-03
Hi, I'm new her, so be nice to me!

Everytime i try to add or remove an application i get the following message: E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache>open()failed, please report

What should i do?

---

### Post by GeeZor on 2007-07-03
open a terminal and perform the action 
```
dpkg --configure -a
```
(or pres Ctrl-Alt-F2 to go to a terminal, use Alt-F7 to return to your X-session)



after that do an 
```
sudo apt-get clean
```
 now you should be able to install everything again. 
Also, please look at the top of your desktop. If there is an orange icon that says Software Update, run that first to install updates for you system... 


Good luck.

---

### Post by 123bjrnar on 2007-07-03
Hi again!

I've tried typing dpkg --configure -a in the terminal, but everytime i do that it says that this action needs "superuser" access. What am i doing wrong?

---

### Post by GeeZor on 2007-07-03
```
sudo dpkg --configure -a 
```

to run it as root

---

### Post by 123bjrnar on 2007-07-03
Ok, it works now! Thanks for the help!

---

