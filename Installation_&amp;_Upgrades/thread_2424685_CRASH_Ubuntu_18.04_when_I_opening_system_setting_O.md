---
title: "CRASH: Ubuntu 18.04 when I opening system setting OR change background logs me out"
date: 2019-08-13
forum: Installation &amp; Upgrades
---

### Post by coffee-milk on 2019-08-13
Hi there ..
I have dual boot windows 10 and linux ubuntu 18.04 LTS , and every time when I try to opening system setting or change background , Ubuntu logs me out .
THE HARDWARE IS :
- NVIDIA RTX 2070
- MSI PRO Z370 
Thank you

---

### Post by coffee-milk on 2019-08-13
I forget something , when I log in to ubuntu again all app will be closed .
NOTE : this issue does not be able when I log in with recovery mode 
SORRY ABOUT MY ENGLISH

---

### Post by cruzer001 on 2019-08-13
Open a terminal and run these commands one line at a time.
```
sudo apt update
sudo apt full-upgrade
sudo apt -f install
```
get any errors?

also install inxi
```
sudo apt install inxi
```
and post the output of
```
inxi -b
```
thankyou

---

### Post by coffee-milk on 2019-08-13
Thank you 
but this NOT work for me

---

