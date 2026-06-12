---
title: "Problem using apt-get"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by smj on 2008-06-30
Hi,
Trying to install build-essentials and screen but getting the following error:

$ sudo apt-get install screen
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package screen

Does anyone know what I'm doing wrong?  I assume apt-get must be configured wrong but I haven't used it before so I don't know how to fix it.

Thanks

---

### Post by dominiquec on 2008-06-30
You might want to check your /etc/apt/sources.list.  Try to enable all the repositories.

Then:

sudo apt-get update

---

### Post by bikeboy on 2008-06-30
As far as I can tell screen is in the main repository, so you shouldn't need to enable others. It's also installed by default in 8.04 Desktop FWIW.

edit: try running this first.
```
sudo apt-get update
```

---

### Post by smj on 2008-06-30
I had tried doing apt-get update and that didn't solve the problem.

But as dominiquec suggested, I enabled some repositries in /etc/apt/sources.list and then it worked.

Many thanks

---

### Post by oldos2er on 2008-06-30
The package name is "build-essential"

---

