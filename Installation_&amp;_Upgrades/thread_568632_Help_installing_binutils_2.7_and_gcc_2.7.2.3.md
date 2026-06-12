---
title: "Help installing binutils 2.7 and gcc 2.7.2.3"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by c00w on 2007-10-06
Hi I am trying to install binutils 2.7 and gcc 2.7.2.3 and I get a wierd error when I run the makefile. Any help would be appreciated

```
r00t@gaming-dev-c:~/Desktop/binutils-2.7$ sudo ./configure --target=i386-unkown-gnu --prefix=/usr/local/xdev
Configuring for a i686-unknown-linux host.
Created "Makefile" in /home/r00t/Desktop/binutils-2.7
r00t@gaming-dev-c:~/Desktop/binutils-2.7$ sudo make
make[1]: Entering directory `/home/r00t/Desktop/binutils-2.7/libiberty'
if [ -n "" ] && [ ! -d pic ]; then \
          mkdir pic; \
        else true; fi
touch stamp-picdir
echo "# !Automatically generated from ./functions.def"\
          "- DO NOT EDIT!" >needed2.awk
grep '^DEFVAR(' < ./functions.def \
         | sed -e '/DEFVAR/s|DEFVAR.\([^,]*\).*|/\1/ { printf "#ifndef NEED_\1\\n#define NEED_\1\\n#endif\\n" }|' \
         >>needed2.awk
grep '^DEFFUNC(' < ./functions.def \
         | sed -e '/DEFFUNC/s|DEFFUNC.\([^,]*\).*|/\1/ { printf "#ifndef NEED_\1\\n#define NEED_\1\\n#endif\\n" }|' \
         >>needed2.awk
gcc -O2 -c -g -I. -I./../include  ./dummy.c 2>/dev/null
(gcc -O2 -o dummy -g   dummy.o  ) >errors 2>&1 || true
echo "/* !Automatically generated from ./functions.def"\
          "- DO NOT EDIT! */" >lconfig.h
awk -f needed2.awk <errors >>lconfig.h
cp lconfig.h config.h
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   argv.c -o pic/argv.o
gcc -O2 -c -g -I. -I./../include  argv.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   basename.c -o pic/basename.o
gcc -O2 -c -g -I. -I./../include  basename.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   choose-temp.c -o pic/choose-temp.o
gcc -O2 -c -g -I. -I./../include  choose-temp.c
choose-temp.c: In function ‘choose_temp_base’:
choose-temp.c:123: warning: incompatible implicit declaration of built-in function ‘strlen’
choose-temp.c:125: warning: incompatible implicit declaration of built-in function ‘abort’
choose-temp.c:128: warning: incompatible implicit declaration of built-in function ‘strcpy’
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   concat.c -o pic/concat.o
gcc -O2 -c -g -I. -I./../include  concat.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   cplus-dem.c -o pic/cplus-dem.o
gcc -O2 -c -g -I. -I./../include  cplus-dem.c
cplus-dem.c: In function ‘demangle_template’:
cplus-dem.c:957: warning: incompatible implicit declaration of built-in function ‘abort’
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   fdmatch.c -o pic/fdmatch.o
gcc -O2 -c -g -I. -I./../include  fdmatch.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   getopt.c -o pic/getopt.o
gcc -O2 -c -g -I. -I./../include  getopt.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   getopt1.c -o pic/getopt1.o
gcc -O2 -c -g -I. -I./../include  getopt1.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   getruntime.c -o pic/getruntime.o
gcc -O2 -c -g -I. -I./../include  getruntime.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   hex.c -o pic/hex.o
gcc -O2 -c -g -I. -I./../include  hex.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   floatformat.c -o pic/floatformat.o
gcc -O2 -c -g -I. -I./../include  floatformat.c
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   obstack.c -o pic/obstack.o
gcc -O2 -c -g -I. -I./../include  obstack.c
obstack.c: In function ‘_obstack_free’:
obstack.c:341: warning: incompatible implicit declaration of built-in function ‘abort’
obstack.c: In function ‘obstack_free’:
obstack.c:375: warning: incompatible implicit declaration of built-in function ‘abort’
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   spaces.c -o pic/spaces.o
gcc -O2 -c -g -I. -I./../include  spaces.c
spaces.c: In function ‘spaces’:
spaces.c:50: warning: conflicting types for built-in function ‘malloc’
test -z "" || \
          gcc -O2 -c -g -I. -I./../include   strerror.c -o pic/strerror.o
gcc -O2 -c -g -I. -I./../include  strerror.c
strerror.c:458: error: static declaration of ‘sys_nerr’ follows non-static declaration
/usr/include/bits/sys_errlist.h:27: error: previous declaration of ‘sys_nerr’ was here
strerror.c:459: error: conflicting types for ‘sys_errlist’
/usr/include/bits/sys_errlist.h:28: error: previous declaration of ‘sys_errlist’ was here
make[1]: *** [strerror.o] Error 1
make[1]: Leaving directory `/home/r00t/Desktop/binutils-2.7/libiberty'
make: *** [all-libiberty] Error 2

```

---

### Post by c00w on 2007-10-07
Anyone know anything about this?

---

### Post by kast123 on 2007-12-05
Exactly the same scenario here (the errors also), but i also failed to configure binutils:

asd@cpt:~/Desktop/binutils-2.7$ ./configure --target=i386-unkown-gnu --prefix=/usr/local/xdev
Configuring for a i686-unknown-linux host.
Created "Makefile" in /home/asd/Desktop/binutils-2.7
configure: error: gnu-as: invalid package name
Configure in /home/asd/Desktop/binutils-2.7/opcodes failed, exiting.

What do do? Anyone?

---

### Post by mike^_^ on 2007-12-05
any specific reason you are trying to install such an old version of gcc?

```
mike@lulz ~ $ gcc --version
gcc (GCC) 4.1.2 (Gentoo 4.1.2 p1.0.2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by kast123 on 2007-12-06
Well, I was following this tutorial:
[http://www.acm.uiuc.edu/sigops/roll_your_own/]("http://www.acm.uiuc.edu/sigops/roll_your_own/")
until the first step of installing the cross-compiler in here:
[http://www.acm.uiuc.edu/sigops/roll_your_own/devel_env.html]("http://www.acm.uiuc.edu/sigops/roll_your_own/devel_env.html")

    *  binutils-2.7  Later versions produce elf headers inconsistant with the workshop
    * gcc-2.7.2.3 Later version will not work with c++ due to exception handlind

Maybe I should choose another tutorial? Or quit the mission? :D

---

### Post by shogun1234 on 2008-04-13
> **kast123 said:**
> Well, I was following this tutorial:
[http://www.acm.uiuc.edu/sigops/roll_your_own/]("http://www.acm.uiuc.edu/sigops/roll_your_own/")
until the first step of installing the cross-compiler in here:
[http://www.acm.uiuc.edu/sigops/roll_your_own/devel_env.html]("http://www.acm.uiuc.edu/sigops/roll_your_own/devel_env.html")

    *  binutils-2.7  Later versions produce elf headers inconsistant with the workshop
    * gcc-2.7.2.3 Later version will not work with c++ due to exception handlind

Maybe I should choose another tutorial? Or quit the mission? :D


Have you solved this problem? I encounter the same error, 
```

.././binutils-2.7/libiberty/strerror.c:458: error: static declaration of ‘sys_nerr’ follows non-static declaration
/usr/include/bits/sys_errlist.h:27: error: previous declaration of ‘sys_nerr’ was here
.././binutils-2.7/libiberty/strerror.c:459: error: conflicting types for ‘sys_errlist’
/usr/include/bits/sys_errlist.h:28: error: previous declaration of ‘sys_errlist’ was here
make[1]: *** [strerror.o] Error 1
make[1]: Leaving directory `/path/to/binutils-directory/binutils/libiberty'
make: *** [all-libiberty] Error 2


```

---

### Post by rahuldhur on 2008-06-10
please help with this as i am facing the same problem......


test -z "-fpic" || \
          gcc -c -g -O2 -I. -I./../include  -fpic strerror.c -o pic/strerror.o
strerror.c:460: error: static declaration of ?sys_nerr? follows non-static declaration
/usr/include/bits/sys_errlist.h:27: error: previous declaration of ?sys_nerr? was here
strerror.c:461: error: conflicting types for ?sys_errlist?
/usr/include/bits/sys_errlist.h:28: error: previous declaration of ?sys_errlist? was here
make: *** [strerror.o] Error 1
.............

---

### Post by wangweixun on 2008-06-26
I have the same problem...Please help~~ 

Thanks~~

obstack.c: In function &#8216;_obstack_free&#8217;:
obstack.c:341: warning: incompatible implicit declaration of built-in function &#8216;abort&#8217;
obstack.c: In function &#8216;obstack_free&#8217;:
obstack.c:375: warning: incompatible implicit declaration of built-in function &#8216;abort&#8217;
gcc -c -g -I. -I./../include  spaces.c
spaces.c: In function &#8216;spaces&#8217;:
spaces.c:50: warning: conflicting types for built-in function &#8216;malloc&#8217;
gcc -c -g -I. -I./../include  strerror.c
strerror.c:467: error: static declaration of &#8216;sys_nerr&#8217; follows non-static declaration
/usr/include/bits/sys_errlist.h:27: error: previous declaration of &#8216;sys_nerr&#8217; was here
strerror.c:468: error: conflicting types for &#8216;sys_errlist&#8217;
/usr/include/bits/sys_errlist.h:28: error: previous declaration of &#8216;sys_errlist&#8217; was here
make[1]: *** [strerror.o] Error 1
make[1]: Leaving directory `/export/research57/weixun/tools/simplescalar.old/binutils-2.5.2/libiberty'
make: *** [all-libiberty] Error 2

---

