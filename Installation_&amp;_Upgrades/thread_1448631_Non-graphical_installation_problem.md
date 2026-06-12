---
title: "Non-graphical installation problem"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by Lebuin on 2010-04-06
[CENTER][LEFT]Hi everyone

I am new to Linux, and I just tried to compile a program (powertab tools) from source. I'm having som problems doing that. The "./configure" command works fine, but when I run "make", it gives an error:

```

seppe@Thuis:~$ cd ptabtools-0.5.0
seppe@Thuis:~/ptabtools-0.5.0$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for poptGetArg in -lpopt... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBXML... yes
checking for LIBXSLT... yes
checking for CHECK... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking popt.h usability... yes
checking popt.h presence... yes
checking for popt.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
configure: creating ./config.status
config.status: creating Makefile.settings
config.status: creating ptabtools.spec
config.status: creating ptabtools.pc
config.status: creating config.h
config.status: config.h is unchanged
seppe@Thuis:~/ptabtools-0.5.0$ make
gcc -shared -Wl,-soname,libptb.so.0 -Wl,-soname,libptb.so.0 -Wl,libptb.so.0.5.0 -g -O2 -g -Wall  -DHAVE_CONFIG_H= -o libptb.so.0.5.0 ptb.po gp.po ptb-tuning.po
libptb.so.0.5.0: file not recognized: File truncated
collect2: ld returned 1 exit status
make: *** [libptb.so.0.5.0] Fout 1
```Are there some packages that I am missing? Or something else?
(I am running Ubuntu 9.10)


[/LEFT]
[/CENTER]

---

### Post by Lebuin on 2010-04-07
I didn't fix the problem, but I just installed a windows program with wine, and it works great.

---

