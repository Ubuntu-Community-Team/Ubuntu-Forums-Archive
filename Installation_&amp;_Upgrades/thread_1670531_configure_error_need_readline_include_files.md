---
title: "configure: error: need readline include files"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by karpay on 2011-01-19
Dear all,

I`m trying to install a program called Clewn. As its help file mentioned I write the command in the terminal:

./configure

Then all of the log below is appeared on the terminal. Later on the configuration is ended with an error:

[error]
configure: error: need readline include files
[/error]

I googled this error, however I couldnt solve the problem.

Any kind of help is kindly appreciated.

Best regards...

The configuration log:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libncurses5-dev
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 1,580kB of archives.
After this operation, 6,693kB of additional disk space will be used.
Get:1 http://tr.archive.ubuntu.com/ubuntu/ maverick/main libncurses5-dev i386 5.7+20100626-0ubuntu1 [1,580kB]
Fetched 1,580kB in 1s (838kB/s)            
Selecting previously deselected package libncurses5-dev.
(Reading database ... 184923 files and directories currently installed.)
Unpacking libncurses5-dev (from .../libncurses5-dev_5.7+20100626-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libncurses5-dev (5.7+20100626-0ubuntu1) ...
yaprak@yaprak-Ubuntu:~/clewn-1.15$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for initscr in -lcurses... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
configure: error: need readline include files

```

---

### Post by ggaurav on 2011-07-04
Don't know if you already fixed it; I just wanted to add in case someone has a similar problem.
```

sudo apt-get install libreadline-dev

```

---

