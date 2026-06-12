---
title: "missing gcc and no internet"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2011-01-04
hi friends
I installed kubuntu. Now I am facing two problems:
1. I have to install LAN driver manually. I have my LAN driver.
2. GCC is missing. Since no LAN driver I can't install the missing gcc from internet.

The problem is I need gcc for install my LAN driver. What should I do?

---

### Post by c2tarun on 2011-01-04
I have the GCC tar ball with me. I also have ubuntu 10.04 LTS live CD with me.
Can anyone either please tell me how to install with the tar ball.
Or Can I extract the deb version of gcc from ubuntu  10.04 Live CD.
Please reply

---

### Post by c2tarun on 2011-01-12
124 views and no solution :(
please help

---

### Post by sj1410 on 2011-01-12
even if you have the tarball you need the make and other files to compile it.

you will need internet to

```

sudo apt-get install build-essential

```

---

### Post by c2tarun on 2011-01-13
Is there anyway to register a bug so that kubuntu developers start embedding gcc compiler into kubuntu kernel?
> **sj1410 said:**
> even if you have the tarball you need the make and other files to compile it.

you will need internet to

```

sudo apt-get install build-essential

```

---

### Post by sj1410 on 2011-01-13
well its not a bug, but you can submit a feature request.

---

