---
title: "install bash from source"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by priyamvaidya on 2011-02-24
hello everybody


i had download bash source by running the command "apt-get source bash" .  The bash source does not contains .c [source file ] for the commands such as cd and pwd.  bash contains cd.def file whic says that cd.c will be created from this .def file.

There is no makefile here.   when i do ./configure  it does not runs. so how could i compile and install this bash commands from the .def files

---

### Post by dino99 on 2011-02-24
its easier to use the devs packages for your distro

[https://launchpad.net/ubuntu/+source/bash](https://launchpad.net/ubuntu/+source/bash)

---

### Post by gmargo on 2011-02-24
Make sure you run "apt-get build-dep bash".  Then it should configure and compile.

---

### Post by priyamvaidya on 2011-02-24
@gmargo---- Thanks for your reply.   But this is not what i intend to do.   

I had the bash source, which i got by running the command "apt-get source bash" . there is the file cd.def which has some code in it.  there is a script "configure" in the folder.  but when i run the script by ./configure,there is a error.

i think there is someother way to .def file.  let me know if anyone knows how to do this. 

i had added  4-5 lines of code in that .def file.  i want to compile and install this so that when i run the cd command, my code is executed first and then the actual command is executed.

let me know if there is any solution to this


@dino99----Thanks for your reply

i know it is much easier to use .deb package, but right now i am compiling a source

---

### Post by priyamvaidya on 2011-02-24
please find the exact error message when i do ./configure in the bash directory.

"c compiler can not create executables.  See config.log for more details"

---

### Post by priyamvaidya on 2011-02-25
the error message as on the screen 


root@ubuntu:/home/priyam/Desktop/bashoriginal/bash-4.1/bash-4.1# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for emacs... no
checking for xemacs... no

Beginning configuration for bash-4.1-release for i686-pc-linux-gnu

checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/home/priyam/Desktop/bashoriginal/bash-4.1/bash-4.1':
configure: error: C compiler cannot create executables
See `config.log' for more details.


On googling for this error message i found that it requires build-essentail package , lib6-dev gcc .  All these packages are upto date.

i had successfully install passwd,  coreutils by the same manner i.e ./configure ----- make ------ make install .  I am only having problem with ./configure in bash source.


do anyone has a reply to this.????

---

### Post by gmargo on 2011-02-25
I can only think that you've messed up your C compiler somehow.  Have you been compiling gcc?

Here's the C program that the ./configure script can't compile.  I've left out the confdefs.h part:
```

int
main ()
{

  ;
  return 0;
}

```

---

### Post by priyamvaidya on 2011-02-25
@gmargo

i did not try to compile gcc.  

i dowloded the package **build-essential** by doing "**apt-get build-essential**".  After this was downloded and installed i compiled and install **coreutils package**, **vim73 package, and shadow package** from the source by doing  **./configure---make----make install**.  i did not have any problems with all the three packages.  

The only problem i am facing is with bash package.

here is the output of the config.log file .  

```
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215939800 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216754904 
PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216230616 
configure:2096: checking build system type
configure:2114: result: i686-pc-linux-gnu
configure:2136: checking host system type
configure:2151: result: i686-pc-linux-gnu
configure:2232: checking for emacs
configure:2262: result: no
configure:2232: checking for xemacs
configure:2262: result: no
configure:2887: checking for gcc
configure:2903: found /usr/bin/gcc
configure:2914: result: gcc
configure:3146: checking for C compiler version
configure:3154: gcc --version >&5
gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3158: $? = 0
configure:3165: gcc -v >&5
Using built-in specs.
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
configure:3169: $? = 0
configure:3176: gcc -V >&5
gcc: '-V' option must have argument
configure:3180: $? = 1
configure:3203: checking for C compiler default output file name
configure:3225: gcc    conftest.c  >&5
conftest.c:1: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'World'
configure:3229: $? = 1
configure:3267: result: 
configure: failed program was:
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216955608 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216877784 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216566488 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216591064 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215689944 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215657176 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215821016 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1217008856 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216066776 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215345880 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216525528 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216345304 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216820440 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216259288 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216091352 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215890648 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1217025240 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216738520 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216218328 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215382744 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216496856 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216369880 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1217336536 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215325400 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216627928 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215984856 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1217369304 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216099544 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215878360 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1215337688 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216525528 
| Hello World
| Param1: 
| Param2: Param1:0.000000 Param2:-1216271576 
configure:3273: error: in `/home/priyam/Desktop/bashoriginal/bash-4.1/bash-4.1':
configure:3276: error: C compiler cannot create executables
See `config.log' for more details.

Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216500952 

ac_cv_build=i686-pc-linux-gnu
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_DEBUGGER_START_FILE_set=
ac_cv_env_DEBUGGER_START_FILE_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_YACC_set=
ac_cv_env_YACC_value=
ac_cv_env_YFLAGS_set=
ac_cv_env_YFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnu
ac_cv_prog_ac_ct_CC=gcc

Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215829208 

ALLOCA=''
AR=''
ARFLAGS=''
BASHVERS='4.1'
BUILD_DIR=''
BUILD_INCLUDED_LIBINTL=''
CATOBJEXT=''
CC='gcc'
CC_FOR_BUILD=''
CFLAGS=''
CFLAGS_FOR_BUILD=''
CPP=''
CPPFLAGS=''
CPPFLAGS_FOR_BUILD=''
CROSS_COMPILE=''
DATADIRNAME=''
DEBUG=''
DEBUGGER_START_FILE='${datadir}/bashdb/bashdb-main.inc'
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EMACS='no'
EXEEXT=''
GENCAT=''
GLIBC21=''
GMSGFMT=''
GREP=''
HELPDIR=''
HELPDIRDEFINE=''
HELPINSTALL=''
HELPSTRINGS=''
HISTORY_DEP=''
HISTORY_LIB=''
HIST_LIBDIR=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
INSTOBJEXT=''
INTLBISON=''
INTLLIBS=''
INTLOBJS=''
INTL_DEP=''
INTL_INC=''
INTL_LIBTOOL_SUFFIX_PREFIX=''
JOBS_O=''
LDFLAGS=''
LDFLAGS_FOR_BUILD=''
LIBICONV=''
LIBINTL=''
LIBINTL_H=''
LIBOBJS=''
LIBS=''
LOCAL_CFLAGS=''
LOCAL_DEFS=''
LOCAL_LDFLAGS=''
LOCAL_LIBS=''
LTLIBICONV=''
LTLIBINTL=''
LTLIBOBJS=''
MAKE_SHELL=''
MALLOC_DEBUG=''
MALLOC_DEP='$(MALLOC_LIBRARY)'
MALLOC_LDFLAGS='-L$(ALLOC_LIBDIR)'
MALLOC_LIB='-lmalloc'
MALLOC_LIBRARY='$(ALLOC_LIBDIR)/libmalloc.a'
MALLOC_SRC='malloc.c'
MALLOC_TARGET='malloc'
MKINSTALLDIRS=''
MSGFMT=''
MSGMERGE=''
OBJEXT=''
PACKAGE_BUGREPORT='bug-bash@gnu.org'
PACKAGE_NAME='bash'
PACKAGE_STRING='bash 4.1-release'
PACKAGE_TARNAME='bash'
PACKAGE_VERSION='4.1-release'
PATH_SEPARATOR=':'
POSUB=''
PROFILE_FLAGS=''
PURIFY=''
RANLIB=''
READLINE_DEP=''
READLINE_LIB=''
RELSTATUS='release'
RL_INCLUDE=''
RL_INCLUDEDIR=''
RL_LIBDIR=''
RL_MAJOR=''
RL_MINOR=''
RL_VERSION=''
SET_MAKE=''
SHELL='/bin/bash'
SHOBJ_CC=''
SHOBJ_CFLAGS=''
SHOBJ_LD=''
SHOBJ_LDFLAGS=''
SHOBJ_LIBS=''
SHOBJ_STATUS=''
SHOBJ_XLDFLAGS=''
SIGLIST_O=''
SIGNAMES_H=''
SIGNAMES_O=''
SIZE=''
STATIC_LD=''
TERMCAP_DEP=''
TERMCAP_LIB=''
TESTSCRIPT='run-all'
TILDE_LIB=''
USE_INCLUDED_LIBINTL=''
USE_NLS=''
XGETTEXT=''
YACC=''
YFLAGS=''
ac_ct_CC='gcc'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
incdir=''
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
lispdir=''
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216603352 

Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216877784 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216566488 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216591064 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215689944 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215657176 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215821016 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1217008856 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216066776 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215345880 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216525528 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216345304 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216820440 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216259288 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216091352 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215890648 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1217025240 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216738520 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216218328 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215382744 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216496856 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216369880 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1217336536 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215325400 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216627928 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215984856 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1217369304 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216099544 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215878360 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215337688 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216918744 

configure: exit 77
```

---

### Post by gmargo on 2011-02-26
> compiled and install **coreutils package**

```
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1215939800 
Hello World
Param1: 
Param2: Param1:0.000000 Param2:-1216754904 

```Here's the problem: you compiled the **coreutils** package.  And you messed around with the **cat** source code, didn't you? (Or maybe it was a library function?)  Those "Hello World Param" strings should not be there.

---

### Post by priyamvaidya on 2011-03-09
@gmargo

yes i downloaded the source for coreutils and i added some lines as per my requirment to the cat.c file. 

R U saying that coreutils package should never be touched ??

do you think this has caused the problem.

regards

---

