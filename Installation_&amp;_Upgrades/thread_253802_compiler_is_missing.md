---
title: "compiler is missing"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by cccc on 2006-09-08
hi

I have a fresh installation of dapper drake, 
and would like to install some programs from the source, but the compiler is missing by default.
which packets should be installed ?

greetings
cccc

---

### Post by adwait on 2006-09-08
use
```
sudo apt-get install build-essentials
```

---

### Post by qamelian on 2006-09-08
Do ```
sudo apt-get install build-essential
``` and the package manager will install all the stuff that you will need at a bare minimum. Just the things that you really can't or shouldn't do without.

---

### Post by cccc on 2006-09-09
> **adwait said:**
> use
```
sudo apt-get install build-essentials
```
correct is:```

# sudo apt-get install **build-essential**
``` 
build-essential**s** is a wrong name.

---

### Post by az on 2006-09-09
If you are not on the net, insert the install cd once you are at the desktop and  you will be able to install it from the cd.

---

