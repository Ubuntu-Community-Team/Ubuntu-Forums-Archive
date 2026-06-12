---
title: "Update problem"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by skyking on 2007-09-03
Hello-
Newbie here and continue to get this error message when attempting to update 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any suggestions would be very very much appreciate.

thanks'

---

### Post by Pumalite on 2007-09-03
Run: sudo dpkg --configure -a

---

### Post by merlinus on 2007-09-03
Enter this in a terminal:

```

sudo dpkg --configure -a

```-merlin

---

### Post by Pumalite on 2007-09-03
Hey, Merlin; at least we are consistent

---

### Post by merlinus on 2007-09-03
Yeah, but consistently what?

:)

-merlin

---

### Post by Pumalite on 2007-09-03
> **merlinus said:**
> Yeah, but consistently what?

:)

-merlin

Consistently right

---

### Post by skyking on 2007-09-04
Thanks for help. Ran this and get 


pat@pat-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
pat@pat-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
pat@pat-desktop:~$ 


Was installing a Java update when this problem started occurring :(.

Tnhaks

---

### Post by davidjmayo on 2007-09-04
As merlinus and pumalite said already
```
sudo dpkg --configure -a
```
you forgot the **sudo** in your command

sudo=**s**uper**u**ser+**do**

---

### Post by skyking on 2007-09-05
my stupid mistake. Pardon for the fark-up. and thanks for the help.

---

