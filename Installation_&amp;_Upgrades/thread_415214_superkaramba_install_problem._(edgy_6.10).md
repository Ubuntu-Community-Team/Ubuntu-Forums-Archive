---
title: "superkaramba install problem. (edgy 6.10)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by CombatWolf on 2007-04-20
ok I've been trying to install Superkaramba for the past 3 days. i googled my problem, looked for every possible way to install it. Tried using Adept Manager and doesn't find Superkaramba. Tried running it from Konsole and i get this message when i input ./configure after compiling.

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
danny@crystalis:~/superkaramba-0.39$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
danny@crystalis:~/superkaramba-0.39$ urpmi gcc gcc-cpp gcc-c++
bash: urpmi: command not found
danny@crystalis:~/superkaramba-0.39$ cd /home/danny
danny@crystalis:~$ urpmi gcc gcc-cpp gcc-c++
bash: urpmi: command not found
danny@crystalis:~$ cd /home/danny/superkaramba-0.39
danny@crystalis:~/superkaramba-0.39$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```

like i said, i tried alternate methods to install superkaramba upon doing much googling. Adept Manager won't find it, my settings are fine there. i searched through the forums before this and i read its in standard repositories, but no find. 

can anyone help?

---

### Post by CombatWolf on 2007-04-20
ok another hurdle.

after running make, it keeps saying "leaving directory" in a few strings before finishing. then i try running make install and i get this.


```
Making install in doc
make[1]: Entering directory `/home/danny/superkaramba-0.39/doc'
Making install in .
make[2]: Entering directory `/home/danny/superkaramba-0.39/doc'
make[3]: Entering directory `/home/danny/superkaramba-0.39/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/danny/superkaramba-0.39/doc'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/doc'
Making install in superkaramba
make[2]: Entering directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[3]: Entering directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/share/doc/HTML/en/superkaramba
mkdir -p -- /usr/share/doc/HTML/en/superkaramba
mkdir: cannot create directory `/usr/share/doc/HTML': Permission denied
make[3]: *** [install-nls] Error 1
make[3]: Leaving directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/danny/superkaramba-0.39/doc'
make: *** [install-recursive] Error 1

```


someone please help me?

---

### Post by CombatWolf on 2007-04-20
well im just going to update my progress even if i get zero replies.


i log into root to do make install, but whether i run make or make install (in the proper order of course) all it says it keeps leaving directories and nothing happens. can anyone help me? this is what i get.

```
Making install in doc
make[1]: Entering directory `/home/danny/superkaramba-0.39/doc'
Making install in .
make[2]: Entering directory `/home/danny/superkaramba-0.39/doc'
make[3]: Entering directory `/home/danny/superkaramba-0.39/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/danny/superkaramba-0.39/doc'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/doc'
Making install in superkaramba
make[2]: Entering directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[3]: Entering directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/share/doc/HTML/en/superkaramba
/usr/bin/install -c -p -m 644 index.docbook /usr/share/doc/HTML/en/superkaramba/index.docbook
/bin/bash ../../admin/mkinstalldirs /usr/share/doc/HTML/en/superkaramba
/usr/bin/install -c -p -m 644 index.cache.bz2 /usr/share/doc/HTML/en/superkaramba/
rm -f /usr/share/doc/HTML/en/superkaramba/common
ln -s /usr/share/doc/kde/HTML/en/common /usr/share/doc/HTML/en/superkaramba/common
make[3]: Leaving directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/doc/superkaramba'
make[1]: Leaving directory `/home/danny/superkaramba-0.39/doc'
Making install in superkaramba
make[1]: Entering directory `/home/danny/superkaramba-0.39/superkaramba'
Making install in src
make[2]: Entering directory `/home/danny/superkaramba-0.39/superkaramba/src'
make[3]: Entering directory `/home/danny/superkaramba-0.39/superkaramba/src'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c -p  'superkaramba' '/usr/bin/superkaramba'
test -z "/usr/share/applnk/Utilities" || mkdir -p -- "/usr/share/applnk/Utilities"
 /usr/bin/install -c -p -m 644 'superkaramba.desktop' '/usr/share/applnk/Utilities/superkaramba.desktop'
test -z "/usr/share/apps/superkaramba" || mkdir -p -- "/usr/share/apps/superkaramba"
 /usr/bin/install -c -p -m 644 'superkarambaui.rc' '/usr/share/apps/superkaramba/superkarambaui.rc'
make[3]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba/src'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba/src'
Making install in icons
make[2]: Entering directory `/home/danny/superkaramba-0.39/superkaramba/icons'
make[3]: Entering directory `/home/danny/superkaramba-0.39/superkaramba/icons'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/22x22/mimetypes
/usr/bin/install -c -p -m 644 ./cr22-mime-superkaramba_theme.png /usr/share/icons/crystalsvg/22x22/mimetypes/superkaramba_theme.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/16x16/mimetypes
/usr/bin/install -c -p -m 644 ./cr16-mime-superkaramba_theme.png /usr/share/icons/crystalsvg/16x16/mimetypes/superkaramba_theme.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/22x22/apps
/usr/bin/install -c -p -m 644 ./cr22-app-superkaramba.png /usr/share/icons/crystalsvg/22x22/apps/superkaramba.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/64x64/mimetypes
/usr/bin/install -c -p -m 644 ./cr64-mime-superkaramba_theme.png /usr/share/icons/crystalsvg/64x64/mimetypes/superkaramba_theme.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/64x64/apps
/usr/bin/install -c -p -m 644 ./cr64-app-superkaramba.png /usr/share/icons/crystalsvg/64x64/apps/superkaramba.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/32x32/apps
/usr/bin/install -c -p -m 644 ./cr32-app-superkaramba.png /usr/share/icons/crystalsvg/32x32/apps/superkaramba.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/128x128/mimetypes
/usr/bin/install -c -p -m 644 ./cr128-mime-superkaramba_theme.png /usr/share/icons/crystalsvg/128x128/mimetypes/superkaramba_theme.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/48x48/apps
/usr/bin/install -c -p -m 644 ./cr48-app-superkaramba.png /usr/share/icons/crystalsvg/48x48/apps/superkaramba.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/16x16/apps
/usr/bin/install -c -p -m 644 ./cr16-app-superkaramba.png /usr/share/icons/crystalsvg/16x16/apps/superkaramba.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/scalable/mimetypes
/usr/bin/install -c -p -m 644 ./crsc-mime-superkaramba_theme.svgz /usr/share/icons/crystalsvg/scalable/mimetypes/superkaramba_theme.svgz
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/48x48/mimetypes
/usr/bin/install -c -p -m 644 ./cr48-mime-superkaramba_theme.png /usr/share/icons/crystalsvg/48x48/mimetypes/superkaramba_theme.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/128x128/apps
/usr/bin/install -c -p -m 644 ./cr128-app-superkaramba.png /usr/share/icons/crystalsvg/128x128/apps/superkaramba.png
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/scalable/apps
/usr/bin/install -c -p -m 644 ./crsc-app-superkaramba.svgz /usr/share/icons/crystalsvg/scalable/apps/superkaramba.svgz
/bin/bash ../../admin/mkinstalldirs /usr/share/icons/crystalsvg/32x32/mimetypes
/usr/bin/install -c -p -m 644 ./cr32-mime-superkaramba_theme.png /usr/share/icons/crystalsvg/32x32/mimetypes/superkaramba_theme.png
make[3]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba/icons'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba/icons'
Making install in mimetypes
make[2]: Entering directory `/home/danny/superkaramba-0.39/superkaramba/mimetypes'
make[3]: Entering directory `/home/danny/superkaramba-0.39/superkaramba/mimetypes'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/mimelnk/application" || mkdir -p -- "/usr/share/mimelnk/application"
 /usr/bin/install -c -p -m 644 'x-superkaramba.desktop' '/usr/share/mimelnk/application/x-superkaramba.desktop'
make[3]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba/mimetypes'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba/mimetypes'
make[2]: Entering directory `/home/danny/superkaramba-0.39/superkaramba'
make[3]: Entering directory `/home/danny/superkaramba-0.39/superkaramba'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba'
make[2]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba'
make[1]: Leaving directory `/home/danny/superkaramba-0.39/superkaramba'
make[1]: Entering directory `/home/danny/superkaramba-0.39'
make[2]: Entering directory `/home/danny/superkaramba-0.39'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Leaving directory `/home/danny/superkaramba-0.39'
make[1]: Leaving directory `/home/danny/superkaramba-0.39'

```


please, someone help me?

---

### Post by Emily on 2007-04-29
I'm running Feisty Fawn, one version later than you, but I was able to install it by typing in the Konsole:

```
sudo apt-get install superkaramba
```

I'm not sure why the Superkaramba website suggests that you d/l it and then configure/make install, because I also ran into errors when I tried to do that.

---

