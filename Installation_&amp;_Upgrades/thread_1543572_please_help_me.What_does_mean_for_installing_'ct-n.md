---
title: "please help me.What does mean for installing 'ct-ng.comp' into you 'bash_completion.d"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by kernelshell on 2010-08-01
First thank you for sparing your precious time to read this:
:KS
I am a chinese and a newer for ubuntu.
I want to make use of crosstool-ng(crosstool-ng-1.7.2) to create crosstooll on my computer (system:ubuntu 10.04).so i can do something on ARM(AT91-ARM926EJ).but i meet difficulty.Please see copy words as follows. I am very eager to someone can contact me on my phone 086-010-15910734367.i am also eager to learn English from you and i can teach you chinese.thank you! i work in Beijing now,and my hometown is Province Heilongjiang.
 
sudo ./configure --prefix=/opt/crosstool-ng-1.7.2
Checking for 'grep'... /bin/grep
Checking whether '/bin/grep' supports -E... yes
Checking for 'sed'... /bin/sed
Checking whether '/bin/sed' supports -i and -e... yes
Checking for 'bash'... /bin/bash
Checking for 'cut'... /usr/bin/cut
Checking for 'install'... /usr/bin/install
Checking for 'make'... /usr/bin/make
Checking for 'gcc'... /usr/bin/gcc
Checking for 'awk'... /usr/bin/awk
Checking for 'bison'... /usr/bin/bison
Checking for 'flex'... /usr/bin/flex
Checking for 'makeinfo'... /usr/bin/makeinfo
Checking for 'automake'... /usr/bin/automake
Checking for 'libtool'... /usr/bin/libtool
Checking for 'stat'... /usr/bin/stat
Checking for 'aria2c'... /usr/bin/aria2c
Checking for 'cvs'... /usr/bin/cvs
Checking for 'patch'... /usr/bin/patch
Checking for 'tar'... /bin/tar
Checking for 'gzip'... /bin/gzip
Checking for 'bzip2'... /bin/bzip2
Checking for 'lzma'... /usr/bin/lzma
Checking for 'readlink'... /bin/readlink
Checking for 'ncurses/ncurses.h'... no
Checking for 'ncurses/curses.h'... no
Checking for 'ncurses.h'... yes
Checking for 'libncursesw.so'... no
Checking for 'libncursesw.a'... no
Checking for 'libncursesw.dylib'... no
Checking for 'libncurses.so'... yes
Computing version string... 1.7.2
Building up Makefile... done
crosstool-NG configured as follows:
PREFIX='/opt/crosstool-ng-1.7.2'
BINDIR='/opt/crosstool-ng-1.7.2/bin'
LIBDIR='/opt/crosstool-ng-1.7.2/lib/ct-ng-1.7.2'
DOCDIR='/opt/crosstool-ng-1.7.2/share/doc/ct-ng-1.7.2'
MANDIR='/opt/crosstool-ng-1.7.2/share/man'
Now run:
make
make install
lym@localhost:/work/crosstool-ng-1.7.2$ make
SED 'ct-ng'
/bin/sh: cannot create ct-ng: Permission denied
make[1]: *** [ct-ng] Error 2
make: *** [build] Error 2
lym@localhost:/work/crosstool-ng-1.7.2$ sudo make
SED 'ct-ng'
SED 'scripts/crosstool-NG.sh'
SED 'scripts/saveSample.sh'
SED 'scripts/showTuple.sh'
SED 'docs/ct-ng.1'
GZIP 'docs/ct-ng.1.gz'
lym@localhost:/work/crosstool-ng-1.7.2$ sudo make install
MKDIR '/opt/crosstool-ng-1.7.2/bin'
INST 'ct-ng'
RMDIR '/opt/crosstool-ng-1.7.2/lib/ct-ng-1.7.2/'
MKDIR '/opt/crosstool-ng-1.7.2/lib/ct-ng-1.7.2'
INST 'config/'
INST 'kconfig/'
INST 'patches/'
INST 'scripts/'
INST 'steps.mk'
INST 'paths.mk'
INST 'samples/'
MKDIR '/opt/crosstool-ng-1.7.2/share/doc/ct-ng-1.7.2'
INST 'docs/CREDITS'
INST 'docs/overview.txt'
MKDIR '/opt/crosstool-ng-1.7.2/share/man/man1'
INST 'ct-ng.1.gz'
For auto-completion, do not forget to install 'ct-ng.comp'
into you 'bash_completion.d'
i don't know how to do for "For auto-completion, do not forget to install 'ct-ng.comp'
into you 'bash_completion.d' "

---

### Post by 23dornot23d on 2010-08-01
There is some more information here , [link]("http://ymorin.is-a-geek.org/projects/crosstool")

after

./configure --local
make

___________________________ You just need to do this now ......

chmod a+rx ct-ng

then

./ct-ng menuconfig

[Link to it running]("http://5270667693938030042-a-1802744773732722657-s-sites.googlegroups.com/site/23dsources/home/Screenshot-1.png?attachauth=ANoY7cpObrbowZumoF54_7ewktbkZDmhJpWREIEPE9t5_GKghe623YrzRUsG8hdTFfZzROZB99tmxhC4IXkQO4TfF-LvJrHrXBJ6P_7SMimjMKXgAzDn5ZPxSawTdKzMrFPbUCk-DB5FSLXkdiDIc80w2PIApt0tqlgG9YAfchA39S-q5U42plviz0xMALN_gjixgfdV51ER1dsI7mVkwDcCi201WNYE-w%3D%3D&attredirects=0")

---

