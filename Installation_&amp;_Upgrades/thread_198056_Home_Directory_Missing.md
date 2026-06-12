---
title: "Home Directory Missing"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by yellowone on 2006-06-16
Greetings,

I have searched for my error and can'r seem to find it on here. I get "Your directory listed as "    directory name    "does not exist. Would you like to use root as your home directory. It is unlikely that anything will work unless you use one of the failsafe options."


If I say yes I am logged off almost immediately. Did I do something wrong during the install. Ubuntu 6.0.6 I downloaded from Distrowatch and it was the DVD ISO/

Thanks for taking time to read.

---

### Post by mscman on 2006-06-16
If you boot into recovery mode and do:
```
deluser <username>
```
and then do
```
adduser <username>
```
to delete and re-add your user.

---

### Post by yellowone on 2006-06-16
thanks...worked perfectly.

---

