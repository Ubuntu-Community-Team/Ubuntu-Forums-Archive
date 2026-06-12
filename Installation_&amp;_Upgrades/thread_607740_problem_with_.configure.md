---
title: "problem with ./configure"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Catdaddy on 2007-11-09
Alright I have a problem when trying to build a ./configure file

I receive this error: 
```

cat@cat-desktop:~/flex-2.5.33$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
**checking for C compiler default output... configure: error: C compiler cannot create executables**
See `config.log' for more details.

```

I get the same error when I try to build c files using Anjuta IDE, but I am not worried about that problem right now. I am sure these problems are both as a result of the same thing.

---

### Post by kellemes on 2007-11-09
Do you have "build-essential" installed?

---

### Post by Pumalite on 2007-11-09
sudo apt-get install build-essential
(if you don't have it)

---

### Post by Catdaddy on 2007-11-09
Alright great thanks guys works great!

---

### Post by Pumalite on 2007-11-09
Good luck.

---

