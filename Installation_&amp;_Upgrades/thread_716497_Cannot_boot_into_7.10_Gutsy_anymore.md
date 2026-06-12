---
title: "Cannot boot into 7.10 Gutsy anymore"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by psp219 on 2008-03-06
I just did the software update and it froze so i forced quit the application and had to hold down the power button on my computer to shut it off but when i turn it back on there is disk checking and thats it succesful so after i login, for 15 minutes nothing happens so im guessing it wont boot 7.10 Gutsy Desktop

---

### Post by psp219 on 2008-03-06
should i reinstall ubuntu?

---

### Post by PmDematagoda on 2008-03-06
Boot Ubuntu in Recovery Mode and then execute:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
After they are done restart Ubuntu with:-
```
sudo restart
```
and see if the problems have been solved.

---

### Post by psp219 on 2008-03-06
lol thats it?

---

### Post by Rohan sehgal on 2008-03-06
You might have installed a wrong or non.compatible package. you can revert these settings by using the recovery console the command's given above. bye

---

### Post by psp219 on 2008-03-06
this is worse ubuntu doesnt even boot now it  just says unsupported signed something 00000x0000011 and then just stops there

---

