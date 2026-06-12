---
title: "I Need Help !!!! Fast !!!"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by andahunter on 2008-04-10
Ubuntu I need help fast. I cant install any programs, it says i have error and i can only correct it via this 'dpkg --configure -a', but when i tipe that into terminal i get i need superuser privileges. I'm happy for that i know that u will help me... Thank You fowardly... You're loyal AndaHunter... :D

---

### Post by Linkinxp on 2008-04-10
I think this issue has been resolve already , search for it

---

### Post by tamoneya on 2008-04-10
use ```
sudo dpkg --configure -a
```  Sudo will give superuser privilages to the command that follows it.

---

### Post by sisco311 on 2008-04-10
```
sudo dpkg --configure -a
```
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by andahunter on 2008-04-10
Thank You both

---

### Post by andahunter on 2008-04-10
Tnx again it salved my problems only i cant dl updates, but i guess i just need 2 fix the broken package becouse i have 1

---

### Post by Partyboi2 on 2008-04-11
> **andahunter said:**
> Tnx again it salved my problems only i cant dl updates, but i guess i just need 2 fix the broken package becouse i have 1
To fix the broken packages you can use
```
sudo apt-get -f install
```

---

