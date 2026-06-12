---
title: "karmic udev boot issues"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sena_akada on 2009-09-20
are these fixed yet?

---

### Post by VMC on 2009-09-21
No, but then you know that when you boot, correct? This suppose to be fixed sometime this coming week.

edit: by the way, you can see these errors using a terminal:
```
grep SYM /var/log/syslog
``` If that's the udev issues your referring to.

---

### Post by VMC on 2009-09-21
They apparently have been fixed with the current run of updates. Here's the fixed version:
Package: udev
State: installed
Automatically installed: no
Version: 147~-3

You can read the original [**LP**]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654") .

---

### Post by Thura on 2009-09-22
I just removed the /lib/udev/rules.d/*udev-defaults* , and it automatically creates another file, and doesn't show any error  msg during boot ...

---

### Post by TDK800 on 2009-09-22
they got fixed with todays updates for me

---

### Post by golusweet on 2009-09-25
I am still having this issue.

Running latest updates, and still hasn't fixed yet.:confused:

anyone know, how to fix?

---

### Post by philinux on 2009-09-25
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by rohitfeb14 on 2009-10-13
i sometimes don't get my graphics properly loaded while starting.. and it corrects on restart

---

