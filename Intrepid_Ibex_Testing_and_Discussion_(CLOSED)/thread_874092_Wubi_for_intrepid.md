---
title: "Wubi for intrepid?"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gilean on 2008-07-29
In the last intrepid alpha i saw wubi, but it is for 8.04.1!!!. I'm planning to test Intrepid, but only with wubi (i consider it a true revolution). When will it be avaiable for intrepid? tnx a lot and greetings from italy :)

---

### Post by jnw222 on 2008-07-29
sorry but probbaly in the later alphas and betas

---

### Post by ibuclaw on 2008-07-29
Install Hardy in Wubi and Change your source files to point to Intrepid instead...

---

### Post by Joeb454 on 2008-07-29
Or just install intrepid inside a virtual machine, that's what I've done :)

---

### Post by ago on 2008-07-30
I will do a custom release shortly using the old codebase, the codebase is being rewritten (slowly...)

---

### Post by Counterfeit187 on 2008-09-30
or the easiest way for now that I can see is install hardy then in hardy press "Alt + F2" to open the launcher window and type in "update-manager -d" without the quotation marks to do a distro upgrade.

---

### Post by ago on 2008-09-30
the latest daily ISOs already contain Wubi 8.10:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

or you can download wubi 8.10 from

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

---

### Post by anhvu2875 on 2008-10-03
i upgraded UBuntu 8.10 OK , but i still get this bug sometimes 

''**E: grub: subprocess post-installation script returned error exit status 1**''

and how can i know which UBuntu 8.10 i am using ? Alpha or Beta ??
i typed this : ```
lsb_release -a
```

dinhvu2875@dinhvu2875-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu intrepid (development branch)
Release: 8.10
Codename: intrepid
dinhvu2875@dinhvu2875-desktop:~$

not know Alpha or Beta ?!
THANKS !

---

### Post by ago on 2008-10-03
Look into .disk/info inside the CD

---

### Post by anhvu2875 on 2008-10-03
**ago**
i upgraded without using CD , so.. ?

---

### Post by ago on 2008-10-03
If you upgrade you have always the latest packages, so you are already post-beta

---

