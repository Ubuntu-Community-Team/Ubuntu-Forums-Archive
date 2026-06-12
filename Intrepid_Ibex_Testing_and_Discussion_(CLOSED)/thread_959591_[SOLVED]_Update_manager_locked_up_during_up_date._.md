---
title: "[SOLVED] Update manager locked up during up date.  Now have an error."
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2008-10-26
Ran update Manager today and halfway threw with the upgrade install Update Manager locked up.  When I reran it, it told me to run sudo dpkg --configure -a which I did. Things looked good until I received this message:
> terminator@terminator-desktop:~$ sudo dpkg --configure -a
[sudo] password for terminator: 
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

Basically I need to know what to do now?

---

### Post by sdowney717 on 2008-10-26
can you go into synaptic and remove the broken packages?

---

### Post by alienexplorers on 2008-10-26
That's the odd thing.  Nothing in synaptic shows as a broken package.

---

### Post by Kevbert on 2008-10-26
Does
```
sudo apt-get install -f
```
in terminal do anything ?
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://www.go2linux.org/problem-upgrading-debian").

---

### Post by ktp on 2008-10-26
I would try that too.

---

