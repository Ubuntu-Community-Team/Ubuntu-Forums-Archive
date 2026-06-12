---
title: "dpkg --configure -a Problem"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by rv53705 on 2008-11-13
Hi, i've installed emesene from Terminal, so when I wanted to install another app, i got this error, you can see the screenshot for more details.

[[IMG]http://img380.imageshack.us/img380/1176/dpkgconfigureaoz7.th.jpg[/IMG]](http://img380.imageshack.us/my.php?image=dpkgconfigureaoz7.jpg)

Any help you can give is cool. ;)

---

### Post by oilchangeguy on 2008-11-13
in the terminal type sudo dpkg --configure -a and press enter.

---

### Post by rv53705 on 2008-11-13
I did it, and as you can see in 5-6 lines on Terminal, it gives me and error.

---

### Post by cariboo on 2008-11-13
In your terminal cd to /var/lib/dpkg/updates and delete 0006 you have to use sudo to delete just that one file. After the file has been deleted run:

```
sudo dpkg --configure -a
```

and see if that works.

Jim

---

### Post by oilchangeguy on 2008-11-13
> **cariboo907 said:**
> In your terminal cd to /var/lib/dpkg/updates and delete 0006 you have to use sudo to delete just that one file. After the file has been deleted run:

```
sudo dpkg --configure -a
```

and see if that works.

Jim

see post #2

---

### Post by rv53705 on 2008-11-14
> **cariboo907 said:**
> In your terminal cd to /var/lib/dpkg/updates and delete 0006 you have to use sudo to delete just that one file. After the file has been deleted run:

```
sudo dpkg --configure -a
```

and see if that works.

Jim

I did what you said, delete a lot of files (0006, 0007, ..., 0012) and now i get this other error:

[[IMG]http://img512.imageshack.us/img512/1009/errorcode1jw1.th.png[/IMG]](http://img512.imageshack.us/my.php?image=errorcode1jw1.png)

---

