---
title: "compilation problems"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by matrix003 on 2011-01-21
[SIZE=2]Hi guys,[/SIZE]
[SIZE=2]I`m new to ubuntu, and I have problem with compilation of source codes...[/SIZE]
[SIZE=2]I wanted to compile kontrollerlab source code, but I can`t because an error is detected.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]my problem is like this:[/SIZE]
 
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ cd/home/njazi/Desktop/prog/
njazi@njazi-System-Name:~/Desktop/prog$ ls[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]acinclude.m4    config.log       INSTALL                      po[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]aclocal.m4      configure        kontrollerlab.kdevelop       README[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]admin           configure.files  kontrollerlab.kdevelop.spec  src[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]AUTHORS         configure.in     Makefile.am                  stamp-h.in[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]autom4te.cache  configure.in.in  Makefile.cvs                 subdirs[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ChangeLog       COPYING          Makefile.in                  templates[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]config.h.in     doc              NEWS                         TODO[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ cd /home/njazi/Desktop/prog/admin[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog/admin$ ./configure[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]bash: ./configure: No such file or directory[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog/admin$ cd /home/njazi/Desktop/prog/aclocal.m4[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]bash: cd: /home/njazi/Desktop/prog/aclocal.m4: Not a directory[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog/admin$ cd /home/njazi/Desktop/prog/[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ ls[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]acinclude.m4    config.log       INSTALL                      po[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]aclocal.m4      configure        kontrollerlab.kdevelop       README[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]admin           configure.files  kontrollerlab.kdevelop.spec  src[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]AUTHORS         configure.in     Makefile.am                  stamp-h.in[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]autom4te.cache  configure.in.in  Makefile.cvs                 subdirs[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ChangeLog       COPYING          Makefile.in                  templates[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]config.h.in     doc              NEWS                         TODO[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ cd /home/njazi/Desktop/[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop$ ls[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]prog[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop$ clear[/SIZE][/FONT]
[FONT=Courier New][SIZE=3] [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop$ cd /home/njazi/Desktop/prog/[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ ls[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]acinclude.m4    config.log       INSTALL                      po[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]aclocal.m4      configure        kontrollerlab.kdevelop       README[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]admin           configure.files  kontrollerlab.kdevelop.spec  src[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]AUTHORS         configure.in     Makefile.am                  stamp-h.in[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]autom4te.cache  configure.in.in  Makefile.cvs                 subdirs[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ChangeLog       COPYING          Makefile.in                  templates[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]config.h.in     doc              NEWS                         TODO[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ sh./configure[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]bash: sh./configure: No such file or directory[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]njazi@njazi-System-Name:~/Desktop/prog$ sh ./configure[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking build system type... i686-pc-linux-gnu[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking host system type... i686-pc-linux-gnu[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking target system type... i686-pc-linux-gnu[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for a BSD-compatible install... /usr/bin/install -c[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for -p flag to install... yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether build environment is sane... yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for gawk... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for mawk... mawk[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether make sets $(MAKE)... yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for style of include used by make... GNU[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for gcc... gcc[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for C compiler default output file name... a.out[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether the C compiler works... yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether we are cross compiling... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for suffix of executables... [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for suffix of object files... o[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether we are using the GNU C compiler... yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether gcc accepts -g... yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for gcc option to accept ANSI C... none needed[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking dependency style of gcc... gcc3[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking how to run the C preprocessor... gcc -E[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for g++... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for c++... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for gpp... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for aCC... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for CC... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for cxx... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for cc++... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for cl... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for FCC... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for KCC... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for RCC... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for xlC_r... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking for xlC... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether we are using the GNU C++ compiler... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether g++ accepts -g... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking dependency style of g++... none[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether g++ supports -Wmissing-format-attribute... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether g++ supports -Wundef... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether g++ supports -Wno-long-long... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking whether g++ supports -Wnon-virtual-dtor... no[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]checking how to run the C++ preprocessor... /lib/cpp[/SIZE][/FONT]
[COLOR=#0070c0][FONT=Courier New][SIZE=3]configure: error: C++ preprocessor "/lib/cpp" fails sanity check[/SIZE][/FONT][/COLOR]
[COLOR=#0070c0][FONT=Courier New][SIZE=3]See `config.log' for more details.[/SIZE][/FONT][/COLOR]
 
I will be thankful for any suggestions...

---

### Post by lykeion on 2011-01-21
First of all when posting code output please enclose it in CODE tags (the # button) for readability.

And regarding your problem, have you checked config.log for details? Otherwise it's hard to tell why the compilation failed.

However rather than compiling yourself it might be easier to install a precompiled binary, and if you go to the [download section](http://www.cadmaniac.org/projectMain.php?projectName=kontrollerlab&section=download) of the homepage for KontrollerLab, you'll find DEB packages for Ubuntu. 
And if you really want the v0.8.0-alpha version you can use the Debian (Sid) package.

---

### Post by oldos2er on 2011-01-21
Have you installed *build-essential*?

---

