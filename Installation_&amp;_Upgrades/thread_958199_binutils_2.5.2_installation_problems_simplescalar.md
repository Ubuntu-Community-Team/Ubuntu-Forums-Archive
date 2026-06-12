---
title: "binutils 2.5.2 installation problems simplescalar"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by nahla on 2008-10-25
hello,
I want to to install simplescalarversion 3 on linux redhat 9, when installing binutils 2.5.2 i have error in file binutils2.5.2/libeberty/ dummy.c and .././fuction.def.
how can I eliminate this problems.
thanks

---

### Post by n2ubu on 2009-02-28
hi,
 i am also facing problem while installing binutils-2.5.2


here is the output error
----------------------------
ubuntu@ubuntu:~/simplesim$ export HOST=i386-unknown-linux
ubuntu@ubuntu:~/simplesim$ pwd
/home/ubuntu/simplesim
ubuntu@ubuntu:~/simplesim$ export IDIR=/home/ubuntu/simplesim
ubuntu@ubuntu:~/simplesim$ cd $IDIR/binutils-2.5.2
ubuntu@ubuntu:~/simplesim/binutils-2.5.2$ configure --host=$HOST --target=ssbig-na-sstrix --with-gnu-as --with-gnu-ld --prefix=$IDIR
bash: configure: command not found
ubuntu@ubuntu:~/simplesim/binutils-2.5.2$ ./configure --host=$HOST --target=ssbig-na-sstrix --with-gnu-as --with-gnu-ld --prefix=$IDIR
Created "Makefile" in /home/ubuntu/simplesim/binutils-2.5.2 using "config/mh-linux"
ubuntu@ubuntu:~/simplesim/binutils-2.5.2$ make
make[1]: Entering directory `/home/ubuntu/simplesim/binutils-2.5.2/libiberty'
echo "# !Automatically generated from ./functions.def"\
          "- DO NOT EDIT!" >needed2.awk
grep '^DEFVAR(' < ./functions.def \
         | sed -e '/DEFVAR/s|DEFVAR.\([^,]*\).*|/\1/ { printf "#ifndef NEED_\1\\n#define NEED_\1\\n#endif\\n" }|' \
         >>needed2.awk
grep '^DEFFUNC(' < ./functions.def \
         | sed -e '/DEFFUNC/s|DEFFUNC.\([^,]*\).*|/\1/ { printf "#ifndef NEED_\1\\n#define NEED_\1\\n#endif\\n" }|' \
         >>needed2.awk
gcc -c -g -I. -I./../include  ./dummy.c 2>/dev/null
(gcc -o dummy -g   dummy.o  ) >errors 2>&1 || true
echo "/* !Automatically generated from ./functions.def"\
          "- DO NOT EDIT! */" >lconfig.h
awk -f needed2.awk <errors >>lconfig.h
cp lconfig.h config.h
gcc -c -g -I. -I./../include  argv.c
gcc -c -g -I. -I./../include  basename.c
gcc -c -g -I. -I./../include  concat.c
gcc -c -g -I. -I./../include  cplus-dem.c
cplus-dem.c: In function ‘demangle_template’:
cplus-dem.c:931: warning: incompatible implicit declaration of built-in function ‘abort’
gcc -c -g -I. -I./../include  fdmatch.c
gcc -c -g -I. -I./../include  getopt.c
gcc -c -g -I. -I./../include  getopt1.c
gcc -c -g -I. -I./../include  getruntime.c
gcc -c -g -I. -I./../include  floatformat.c
gcc -c -g -I. -I./../include  obstack.c
obstack.c: In function ‘_obstack_free’:
obstack.c:341: warning: incompatible implicit declaration of built-in function ‘abort’obstack.c: In function ‘obstack_free’:
obstack.c:375: warning: incompatible implicit declaration of built-in function ‘abort’gcc -c -g -I. -I./../include  spaces.c
spaces.c: In function ‘spaces’:
spaces.c:50: warning: conflicting types for built-in function ‘malloc’
gcc -c -g -I. -I./../include  strerror.c
strerror.c:467: error: static declaration of ‘sys_nerr’ follows non-static declaration/usr/include/bits/sys_errlist.h:27: error: previous declaration of ‘sys_nerr’ was herestrerror.c:468: error: conflicting types for ‘sys_errlist’
/usr/include/bits/sys_errlist.h:28: error: previous declaration of ‘sys_errlist’ was here
make[1]: *** [strerror.o] Error 1
make[1]: Leaving directory `/home/ubuntu/simplesim/binutils-2.5.2/libiberty'
make: *** [all-libiberty] Error 2
ubuntu@ubuntu:~/simplesim/binutils-2.5.2$

----------------------------------------

pls help

---

### Post by bakshi.hrishikesh on 2009-03-13
Try installing simpleutils instead of binutils.

You can download it from:

[http://csrl.unt.edu/downloads/simplescalar.tgz](http://csrl.unt.edu/downloads/simplescalar.tgz)

The detailed instructions I followed are on this page:

[http://harryscode.blogspot.com/2008/10/installing-simplescalar.html](http://harryscode.blogspot.com/2008/10/installing-simplescalar.html)

---

### Post by varunpandit on 2009-03-22
Hi,

I am facing problems with compiling programs so that they run on SimpleScalar. I followed the installation guides that are on the web and I got PISA gcc in place. But when I go to compile programs it gives me an error saying "-lm not found" (Math Library). I am also unable to compile C++ programs using g++ that was compiled during the installation due to some missing C++ header files. Can anybody suggest something??

---

### Post by bakshi.hrishikesh on 2009-09-29
What gcc have you installed? is it gcc 2.7.2?

---

