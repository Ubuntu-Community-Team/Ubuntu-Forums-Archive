---
title: "newbie in need of help"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by cnttuchme on 2008-05-17
i am really new at ubuntu, but when i try to use" ./configure" in my terminal i get this.:(

```
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

i dont know if there is already a topic about this if so please direct me there.

---

### Post by iaculallad on 2008-05-17
Are you trying to compile something with GCC?
Try this one:


sudo apt-get install build-essential

then try your ./configure again.

---

### Post by cnttuchme on 2008-05-17
im doing that now i will see how it goes when i try again thanks for the reply

ok well i did that it worked now i need to figure out how to make the program run lol thanks for all your help

---

### Post by cnttuchme on 2008-05-17
```
Before you can run 'make' you must run
the system configuration script, type:

./configure

```
great lol on to a new challange

---

### Post by iaculallad on 2008-05-17
Im glad it helped. Goodluck with your compiling.

---

