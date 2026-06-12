---
title: "How to uninstall something??"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by da3shot on 2008-01-26
hey guys,

i've had ubuntu for about 2 weeks and i downloaded netbeans 6.0 from the internet. well, i didnt like it and got eclipse instead. Now I want to uninstall netbeeans from the computer, so i go to the folder to where it is and click on uninstall.sh. When i click on it, it wont let me uninstall it and it says "Cannot write to local directory - not enough permissions" Whats up with this message?? btw, im the only user on the computer, so shouldnt i have the permission to do anything with the files?

---

### Post by Pumalite on 2008-01-26
Try:
gksudo nautilus

---

### Post by Pandemic187 on 2008-01-26
> **da3shot said:**
> "Cannot write to local directory - not enough permissions" Whats up with this message?? btw, im the only user on the computer, so shouldnt i have the permission to do anything with the files?
I'm not sure about uninstalling it, but in Linux, even if you're the only user you don't have full permission, unless you use the sudo command.

Just wondering, how did you go about installing the program?

---

### Post by da3shot on 2008-01-26
thx pumalite, it worked. so what does gksudo nautilus actually do??

and for pandemic187, i went to this website-> [http://wiki.netbeans.org/InstallingNetbeansUbuntu7.04](http://wiki.netbeans.org/InstallingNetbeansUbuntu7.04)

---

### Post by Pumalite on 2008-01-26
It lets you navigate with root privileges.

---

