---
title: "Synaptic issue"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by rectec794613 on 2008-03-26
Hey! I cant run synaptic now because i get the following error message```
E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)


```
And when I tried to reinstall it is says that i already have it and i cant. so can you do me a favor and help me out?:(

---

### Post by kerry_s on 2008-03-26
synaptic is suppose to be only run as root.

**sudo synaptic**

---

### Post by rectec794613 on 2008-03-26
Well before it ran perfectly and i could run it by clicking on its shortcut in the menu

---

### Post by rectec794613 on 2008-03-26
> **kerry_s said:**
> synaptic is suppose to be only run as root.

**sudo synaptic**

Also when i try to run it as root in the terminal i get the same error message :mad:

---

### Post by MONODA on 2008-03-26
thats weird, why do you have a /home/root directory, the root's home should be /root

---

### Post by rectec794613 on 2008-03-26
Oh Yeah! That's right. I tried to move the root directory to the home directory attempting to make root a user that I can log in to via the login window. didn't work.
But I cant find the root folder in the home folder OR the root one!

---

### Post by MONODA on 2008-03-26
ok then try and change it back the way that you changed it in the first place.

---

### Post by rectec794613 on 2008-03-26
> **MONODA said:**
> ok then try and change it back the way that you changed it in the first place.
Like I said Before: > But I cant find the root folder in the home folder OR the root one! :mad:

---

### Post by kerry_s on 2008-03-27
open a terminal->
**sudo mkdir /root**

everything should start going back in there.

---

