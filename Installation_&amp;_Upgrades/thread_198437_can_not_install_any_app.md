---
title: "can not install any app"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2006-06-17
when i want to install any app i get this error
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

and when i try dpkg --configure -a nothing happens
```

 sudo dpkg --configure -a
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

```

what i can do that this will start working?

thx

---

### Post by jtwJGuevara on 2006-06-17
Hi, 

Are you running dpkg directly or are you using apt or syanptic?  Its my understanding that dpkg is a low level way of installing things and the other two abstract its details away from you.  If you are running dpkg directly, try running apt instead.

Also, what are you trying to install and where are you getting it from?  Are these packages from the repositories or manual downloads distrubuted as .debs?

---

### Post by opera on 2006-06-17
same problem a couple of hours ago

---

