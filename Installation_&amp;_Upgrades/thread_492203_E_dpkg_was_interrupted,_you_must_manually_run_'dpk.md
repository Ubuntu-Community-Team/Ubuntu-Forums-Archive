---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by theROKR on 2007-07-04
I dont know what this error message means!!!!!
i get it every time i try to install something on my Ubuntu 6.06LTS Dapper Drake

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

how do i solve it?

---

### Post by ThrobbingBrain66 on 2007-07-04
Open a terminal and type:
```
sudo dpkg --configure -a
```
:)

Chances are a previous software installation was interupted/didn't complete correctly, this command will fix that.

---

### Post by faerytail on 2008-01-03
Thanks!

---

