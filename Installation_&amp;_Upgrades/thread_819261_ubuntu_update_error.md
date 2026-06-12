---
title: "ubuntu update error"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by syedaliraza on 2008-06-05
hello :guitar:

i am very beginner in Linux..yesterday i just installed my ubuntu very first time..and i am very happy with it..

but now i am getting error message when i open update manager ..

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please guide me what is this ..and how can i check my ubuntu updates..

thanks

---

### Post by Pumalite on 2008-06-05
sudo dpkg --configure -a
(in the Terminal)

---

### Post by Kevbert on 2008-06-05
Open Applications - Accessories - Terminal
enter the following code:
```
sudo dpkg --configure -a
```
It will ask you for your login password.  While you're at it, enter
```
sudo apt-get install -f
```
to check for any broken packages.
You can now check for updates with
```
sudo apt-get update
```
Exit from terminal with
```
exit
```

---

### Post by syedaliraza on 2008-06-05
oh thanks alot..problem solved..so nice of you..thanx all..

LINUX RULLZ

---

### Post by Kevbert on 2008-06-05
You're welcome.:)

---

