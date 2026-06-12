---
title: "PackageKit"
date: 2008-07-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-07-06
Just a finding and a question if someone
tested Packagekit.... ?

Menu System > Administration > Add/Remove Software


[[img]http://pici.se/thumbs/t_eGIMsdcqX.gif[/img]](http://pici.se/298582)

---

### Post by plun on 2008-07-06
Well it was easy to test....

```
plun@dunder:~$ gpk-application

Segmentation fault

```

:---)

---

### Post by ronacc on 2008-07-06
It doesn't segfault for me on my amd64 system . runs ok wheather started from system>administration>add remove software or from term with   gpk-application .

---

### Post by ShirishAg75 on 2008-07-06
no segfault here too, right from the CLI as well as from the Admin Menu > Add/Remove software. No issues at all.

---

### Post by plun on 2008-07-07
Sorry I left out one fact that the seg fault arrives
directly when I mark a package for install

The GUI starts OK....

I tested with a Geany install

---

### Post by ronacc on 2008-07-07
yes that segfaults it . have you filed a bug on it ? I'll confirm .

---

### Post by plun on 2008-07-07
> **ronacc said:**
> yes that segfaults it . have you filed a bug on it ? I'll confirm .

Thanks for confirming.

Bug filed

[https://bugs.launchpad.net/ubuntu/+source/packagekit-gnome/+bug/246255](https://bugs.launchpad.net/ubuntu/+source/packagekit-gnome/+bug/246255)

---

### Post by aamukahvi on 2008-07-07
The application started but didn't work properly. Also the apt backend is seriously lacking still.

---

