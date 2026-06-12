---
title: "Screen Stuck at 800x600"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Patrick793 on 2008-09-20
I just upgraded to Ubuntu 8.10 Intrepid Ibex, because I like to play around in Alphas and Betas.

Anyway, the upgrade went fine, except for 2 things.

1: My screen resolution is stuck at 800x600. I can't figure out how to fix it.

2: This may help 1. I have been trying to install my ATI drivers, but have some problems. When I try installing with Hardware Drivers, it doesn't download anything, and when I try with EnvyNG, it crashes before it starts (EnvyNG I mean, not Ubuntu).

Any help?

---

### Post by Nullack on 2008-09-20
Have a look at the debugging x section of the ubuntu wiki

---

### Post by alienexplorers on 2008-09-20
In Envyng did you start it with the gtk installer if so, open terminal and start envy by typing:
> sudo envyng -t

---

### Post by Patrick793 on 2008-09-20
> **alienexplorers said:**
> In Envyng did you start it with the gtk installer if so, open terminal and start envy by typing:
When I tryed that I got this (after choosing the drivers).

```
False


 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+

```

---

### Post by gjoellee on 2008-09-20
In most cases running "xfix" should fix the problem. Read more here: [http://www.kshoster.net/?c=tipsandtricks&h=xfix](http://www.kshoster.net/?c=tipsandtricks&h=xfix)

---

### Post by jespdj on 2008-09-20
> **Patrick793 said:**
> ```
False


 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+

```
Install the package build-essential and try again:
```
sudo apt-get install build-essential
```

---

### Post by BwackNinja on 2008-09-20
Did you update your xserver when you upgraded from hardy to intrepid? If so, I don't think fglrx supports the current xserver yet. Try the opensource drivers. You might run into problems with LibGl.so.* files, for those look in one of the other ati driver threads here. I don't remember which one.

---

