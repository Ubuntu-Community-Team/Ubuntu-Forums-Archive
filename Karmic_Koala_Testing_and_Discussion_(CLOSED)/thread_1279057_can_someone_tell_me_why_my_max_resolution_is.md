---
title: "can someone tell me why my max resolution is"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joshuapbell on 2009-09-30
960*600 or lower? right now I have it on 800*600 and it is horrible to do anything on? any help or suggestions would be great.

---

### Post by Tibuda on 2009-09-30
Have you installed your graphic card driver? Check if it is available in System > Admin > Hardware drivers.

---

### Post by joshuapbell on 2009-09-30
> **danielrmt said:**
> Have you installed your graphic card driver? Check if it is available in System > Admin > Hardware drivers.

I have checked, there is nothing there.

---

### Post by VMC on 2009-09-30
What's the output of this:

```
lspci|grep VGA

```

---

### Post by joshuapbell on 2009-09-30
> **VMC said:**
> What's the output of this:

```
lspci|grep VGA

```

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by fela on 2009-09-30
edit: too slow

edit2: sorry but I have no idea on how to get them to work. Best idea is to search on their website for drivers.

---

### Post by Martje_001 on 2009-09-30
SiS just f***** sucks, sorry. It takes a long time searching and compiling to get it to work.

Are you able to remove this card or do you have a laptop?

---

### Post by VMC on 2009-09-30
> **joshuapbell said:**
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Have you used any of [**_these_**]("http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads") drivers?

---

### Post by joshuapbell on 2009-09-30
> **Martje_001 said:**
> SiS just f***** sucks, sorry. It takes a long time searching and compiling to get it to work.

Are you able to remove this card or do you have a laptop?

This is my work computer, I do not have access to another video card :-(

---

