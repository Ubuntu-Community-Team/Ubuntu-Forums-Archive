---
title: "no acceptable C compiler found in $PATH"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by macm10 on 2006-06-24
hello, while running the configure shell script for [gweled]("http://sebdelestaing.free.fr/gweled/") it gave me the following line: 

> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH


i know i am somewhat new at this but i would assume that ubuntu would come with a C compiler.

---

### Post by Perfect Storm on 2006-06-24
*It does:

```
sudo apt-get install build-essential
```

---

### Post by macm10 on 2006-06-24
ok i installed all of those nice programs useing that code. now i get the following error message

> 
checking for pkg-config... /usr/bin/pkg-config
checking for libglade-2.0,libgnomeui-2.0,librsvg-2.0... Package libglade-2.0 was  not found in the pkg-config search path. Perhaps you should add the directory c ontaining `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No packa ge 'libglade-2.0' found Package libgnomeui-2.0 was not found in the pkg-config s earch path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Pa ckage librsvg-2.0 was not found in the pkg-config search path. Perhaps you shoul d add the directory containing `librsvg-2.0.pc' to the PKG_CONFIG_PATH environme nt variable No package 'librsvg-2.0' found
configure: error: Library requirements (libglade-2.0,libgnomeui-2.0,librsvg-2.0)  not met; consider adjusting the PKG_CONFIG_PATH environment variable if your li braries are in a nonstandard prefix so pkg-config can find them.


i looked in the package manager and it says that i have libglade installed.

---

### Post by taurus on 2006-06-24
But you also need the development package also, libglade-dev, if you want to build something from source!

---

### Post by macm10 on 2006-06-24
hmmm that got the configureing out of the way. now when i run the "make" command i get the folowing errors:

```

main.c:33:20: error: mikmod.h: No such file or directory
main.c:55: error: syntax error before ‘*’ token
main.c:55: warning: data definition has no type or storage class
main.c:56: error: syntax error before ‘*’ token
main.c:56: warning: data definition has no type or storage class
main.c: In function ‘main’:
main.c:265: error: ‘MikMod_errno’ undeclared (first use in this function)
main.c:265: error: (Each undeclared identifier is reported only once
main.c:265: error: for each function it appears in.)
main.c:309: warning: assignment makes pointer from integer without a cast
main.c:312: warning: assignment makes pointer from integer without a cast
main.c:318: warning: assignment makes pointer from integer without a cast
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/ubuntu/Desktop/gweled-0.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubuntu/Desktop/gweled-0.7'
make: *** [all] Error 2

```

---

