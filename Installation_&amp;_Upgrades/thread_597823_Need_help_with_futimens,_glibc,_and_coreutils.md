---
title: "Need help with futimens, glibc, and coreutils"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by jkchow on 2007-10-30
Hey all,

I'm an undergrad computer science student, and I use Ubuntu to compile my projects for class. I've recently installed Gutsy on my laptop and i've installed build-essential. My problem is that everytime I try to compile the coreutils, I receive this error:

Making all in lib
make[1]: Entering directory `/home/jkchow/Desktop/coreutils-6.9/lib'
make  all-am
make[2]: Entering directory `/home/jkchow/Desktop/coreutils-6.9/lib'
gcc -std=gnu99  -I.      -g -O2 -MT utimecmp.o -MD -MP -MF .deps/utimecmp.Tpo -c -o utimecmp.o utimecmp.c
In file included from utimecmp.c:33:
utimens.h:2: error: conflicting types for 'futimens'
///usr/include/sys/stat.h:370: error: previous declaration of 'futimens' was here
make[2]: *** [utimecmp.o] Error 1
make[2]: Leaving directory `/home/jkchow/Desktop/coreutils-6.9/lib'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jkchow/Desktop/coreutils-6.9/lib'
make: *** [all-recursive] Error 1

I did a lot of research, and it seems like I need to patch something but I'm a complete newbie at Linux. I would really appreciate it, since my grade depends on this and I really do not want to use a lame Knoppix Live CD everytime I want to compile a program :(

---

### Post by matimatik on 2007-11-02
> **jkchow said:**
> Hey all,
...
In file included from utimecmp.c:33:
utimens.h:2: error: conflicting types for 'futimens'
///usr/include/sys/stat.h:370: error: previous declaration of 'futimens' was here
...
:(
```

for file in src/{copy,touch}.c lib/utimens.{c,h} ; do \
   cp -v $file{,.orig}
   sed 's/futimens/gl_&/' $file.orig > $file
done

```
in coreutils-6.9's source dir will help u :) . U need sed to be installed before do this, of course :) .

---

### Post by jkchow on 2007-11-02
> **matimatik said:**
> ```

for file in src/{copy,touch}.c lib/utimens.{c,h} ; do \
   cp -v $file{,.orig}
   sed 's/futimens/gl_&/' $file.orig > $file
done

```
in coreutils-6.9's source dir will help u :) . U need sed to be installed before do this, of course :) .

Thanks for the tip. I'm just wondering what the "gl_&" means in your sed command? Also, in another forum (i forgot where) the person suggested to change "futimens" to "cu_futimens." Any problems with this?

---

### Post by matimatik on 2007-11-02
> **jkchow said:**
> Thanks for the tip. I'm just wondering what the "gl_&" means in your sed command? Also, in another forum (i forgot where) the person suggested to change "futimens" to "cu_futimens." Any problems with this?
No problems ;) . It's only impotant, that "smth_futimens" isn't equal "futimens" :) .

---

