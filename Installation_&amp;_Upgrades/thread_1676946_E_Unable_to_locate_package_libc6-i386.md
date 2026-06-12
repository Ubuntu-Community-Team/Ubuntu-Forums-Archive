---
title: "E: Unable to locate package libc6-i386"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by adityagoel123 on 2011-01-27
Hi,

I am trying to install oracle 10g xpress edition onto my laptop. i am currently working on ubuntu 10.10.
when i am trying to get 32 bit libraries by: sudo apt-get install libc6-i386
I am getting this error: 
E: Unable to locate package libc6-i386 .

Please help OR specify how to install oracle onto ubuntu 10.10


thanks in advance

:confused:
:guitar:

---

### Post by sikander3786 on 2011-01-28
Go to Software Center > Edit > Software Sources > Updates Tab and make sure maverick-security and maverick-updates are enabled.

Then from Applications > Accessories > Terminal:

```
sudo apt-get update
```

```
sudo apt-get install libc6-i386
```

---

