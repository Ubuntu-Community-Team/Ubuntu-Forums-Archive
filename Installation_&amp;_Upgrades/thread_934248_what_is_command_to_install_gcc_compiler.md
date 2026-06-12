---
title: "what is command to install gcc compiler?"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by abhilashm86 on 2008-09-30
I have downloaded all ubuntu codecs,but not able to compile program..........please tell how to install gcc compiler...........

---

### Post by VMC on 2008-09-30
It should be installed. Type the following.

```
gcc -dumpversion
```

If not installed or you need a more current version then type

```
apt-get install gcc
```

---

### Post by DrMega on 2008-09-30
Don't forget to make sure you have installed the package 'build-essential', otherwise you'll have a job getting anything to compile as most of the standard headers etc will be missing.

---

### Post by oldos2er on 2008-09-30
> **abhilashm86 said:**
> I have downloaded all ubuntu codecs,but not able to compile program..........please tell how to install gcc compiler...........

 sudo aptitude update && sudo aptitude install build-essential

---

