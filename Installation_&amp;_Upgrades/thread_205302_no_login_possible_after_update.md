---
title: "no login possible after update"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by dawandeh on 2006-06-28
hey!

i downloaded the ubuntu 6.06 yesterday...installing was easygoing...today i plugged in a friends dslcable and downloaded the updates...
BIG SURPRISE:
after restart the login screen comes up as usual...i enter username and password and up comes a black screen for 1 second saying:
"Ubuntu 6.06LTS computername tty1"
"computername login:"
then i get back to the login screen!

-when i type a wrong username or pw...he says "incorrect login/pw"
- typing the correct username/pw ->no login possible as described above

i really do hope someone can help me on this, please don´t send me back to winxp 

tnx a lot
dawandeh

---

### Post by dawandeh on 2006-06-28
hey!

problem solved:
aptitude clean
aptitude update
aptitude upgrade

---

