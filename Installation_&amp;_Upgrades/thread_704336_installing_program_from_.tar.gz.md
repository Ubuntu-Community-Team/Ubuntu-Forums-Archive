---
title: "installing program from .tar.gz"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by fourthofjuly on 2008-02-22
Using Ubuntu since over 8 months but i have never been able to install even a single programme from source files. I know ./configure make & make install, but they always give me trouble.

AS I HAVE NOW MOVED COMPLETELY FROM backward-slash TO forward-slash, I DESPERATELY WON'T TO LEARN AS TO WHERE I HAVE BEEN GOING WRONG IN THE INSTALL PROCESS... SO PLEASE HELP...

currently using Ubuntu 7.10... have chosen a program called grass for this...

i have the source file that i copied from a CD to my desktop

file name is**[COLOR="Red"] grass-6.2.2.tar.gz [/COLOR]** which I wish to install on my system

1) right clicked and extracted to a folder grass-6.2.2 on desktop 
2) cd to this folder
3) ./configure gives some error

[B][COLOR="Red"]devang@ubuntu:~$ cd /home/devang/Desktop/grass-6.2.2
[/COLOR][/B]
[COLOR="Red"]**devang@ubuntu:~/Desktop/grass-6.2.2$ ls**[/COLOR]
aclocal.m4          configure               display      imagery     man       REQUIREMENTS.html   SUBMITTING_TCLTK
AUTHORS             configure.in            doc          include     misc      rfc                 swig
binaryInstall.src   contributors.csv        gem          INSTALL     paint     rpm                 testsuite
ChangeLog_6.2.2.gz  contributors_extra.csv  general      install-sh  ps        scripts             TODO
CHANGES             COPYING                 GPL.TXT      lib         raster    sites               tools
config.guess        db                      grass.pc.in  locale      raster3d  SUBMITTING          vector
config.sub          demolocation            gui          Makefile    README    SUBMITTING_SCRIPTS  visualization

**[COLOR="Red"]devang@ubuntu:~/Desktop/grass-6.2.2$ ./configure[/COLOR]**
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for executable suffix... no
checking for full floating-point support... yes
checking for pwd... /bin/pwd
checking for source directory... /home/devang/Desktop/grass-6.2.2
checking for build directory... /home/devang/Desktop/grass-6.2.2
checking how to build libraries... shared
yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... Linux-2.6.22-14-generic
checking for dlopen in -ldl... yes
checking for ar... ar
checking for SysV... no
checking for XDriver... socket
checking for additional include dirs... 
checking for additional library dirs... 
checking for a BSD compatible install... /usr/bin/install -c
checking for flex... lex
checking for yywrap in -ll... no
checking for lex... no
configure: error: *** Unable to locate lex.


should i consider this error or proceed further with make?

thanks & regards,

devang.

---

### Post by taurus on 2008-02-22
Looks like you need to install flex.

```
sudo apt-get update
sudo apt-get install flex
```
And if you get an error message from ./configure, no need to go further with make or sudo make install because it will not work.

---

### Post by fourthofjuly on 2008-02-22
thanks

have installed flex...

again cd to the directory & ./configure gives an error

**[COLOR="Red"]devang@ubuntu:~/Desktop/grass-6.2.2$ ./configure[/COLOR]**
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for executable suffix... no
checking for full floating-point support... yes
checking for pwd... /bin/pwd
checking for source directory... /home/devang/Desktop/grass-6.2.2
checking for build directory... /home/devang/Desktop/grass-6.2.2
checking how to build libraries... shared
yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... Linux-2.6.22-14-generic
checking for dlopen in -ldl... yes
checking for ar... ar
checking for SysV... no
checking for XDriver... socket
checking for additional include dirs... 
checking for additional library dirs... 
checking for a BSD compatible install... /usr/bin/install -c
checking for flex... flex
checking for yywrap in -lfl... yes
checking for bison... no
checking for byacc... no
checking for yacc... no
configure: error: *** Unable to locate yacc.

please help...

regards,

devang.

---

### Post by taurus on 2008-02-22
```
sudo apt-get update
sudo apt-get install bison byacc
```

---

### Post by fourthofjuly on 2008-02-22
thanks, have done that too...

got the following error:

**[COLOR="Red"]devang@ubuntu:~/Desktop/grass-6.2.2$ ./configure[/COLOR]**
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for executable suffix... no
checking for full floating-point support... yes
checking for pwd... /bin/pwd
checking for source directory... /home/devang/Desktop/grass-6.2.2
checking for build directory... /home/devang/Desktop/grass-6.2.2
checking how to build libraries... shared
yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... Linux-2.6.22-14-generic
checking for dlopen in -ldl... yes
checking for ar... ar
checking for SysV... no
checking for XDriver... socket
checking for additional include dirs... 
checking for additional library dirs... 
checking for a BSD compatible install... /usr/bin/install -c
checking for flex... flex
checking for yywrap in -lfl... yes
checking for bison... bison -y
checking for ranlib... ranlib
checking for ar... ar
checking for env... env
checking for perl... /usr/bin/perl
checking for ANSI C header files... yes
checking for limits.h... yes
checking for termio.h... yes
checking for termios.h... yes
checking for unistd.h... yes
checking for values.h... yes
checking for g2c.h... no
checking for f2c.h... no
checking for sys/ioctl.h... yes
checking for sys/mtio.h... yes
checking for sys/resource.h... yes
checking for sys/time.h... yes
checking for sys/timeb.h... yes
checking for sys/types.h... yes
checking for sys/utsname.h... yes
checking for libintl.h... yes
checking for iconv.h... yes
checking for langinfo.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for off_t... yes
checking for uid_t in sys/types.h... yes
checking return type of signal handlers... void
checking for Cygwin environment... no
checking for ftime... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for lseek... yes
checking for nice... yes
checking for time... yes
checking for uname... yes
checking for seteuid... yes
checking for setpriority... yes
checking for setreuid... yes
checking for setruid... no
checking for drand48... yes
checking for putenv... yes
checking for setenv... yes
checking for nanosleep... yes
checking whether setpgrp takes no argument... yes
checking for W11... no
checking for X... no
checking whether to use Curses... yes
checking for curses.h... no
configure: error: *** Unable to locate curses includes.


i would also like to learn how you can judge what's missing?

thanks...

---

### Post by maybeway36 on 2008-02-22
Googling curses.h I find this:
[http://www.unix.com/high-level-programming/2741-curses-h-not-found.html](http://www.unix.com/high-level-programming/2741-curses-h-not-found.html)
That's for Red Hat, but I know now to look for the ncurses development libraries, which are in Ubuntu as lib32ncurses5-dev:
```
sudo apt-get install lib32ncurses5-dev
```

---

### Post by taurus on 2008-02-22
You know that grass is available in the repos.

```
sudo apt-get update
sudo apt-get install grass grass-doc
```

---

### Post by fourthofjuly on 2008-02-22
got the following error:

devang@ubuntu:~/Desktop/grass-6.2.2$ sudo apt-get install lib32ncurses5-dev
[sudo] password for devang:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32ncurses5-dev

---

### Post by fourthofjuly on 2008-02-22
> **taurus said:**
> You know that grass is available in the repos.

```
sudo apt-get update
sudo apt-get install grass grass-doc
```

Sir, yes indeed, but i wish to install it from source, as i have never been able to install any program from .tar.gz files & i get stuck up...

---

### Post by taurus on 2008-02-22
> **fourthofjuly said:**
> Sir, yes indeed, but i wish to install it from source, as i have never been able to install any program from .tar.gz files & i get stuck up...

Then you need to install all the dependencies first before you can build it from source.

---

### Post by maybeway36 on 2008-02-22
I can't believe I didn't think of this before.
```
sudo apt-get build-dep grass
```
installs all packages needed to build grass form source.

---

### Post by fourthofjuly on 2008-02-23
Sir, how do i find out how many dependencies are missing? or I would keep on installing the dependencies & never know when it will end? also i am not able to judge for myself WHICH dependencies are required? its only because you suggested that i could install 2 of them (flex & bison byacc).

will the file grass-6.2.2.tar.gz not contain the required dependencies, since i have to download them from the internet?

please help...

regards,

devang.

I understand that grass is available in the repos,

---

### Post by fourthofjuly on 2008-02-23
i will try out maybeway36's suggestion...

---

