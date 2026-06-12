---
title: "installing packages"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by hatem1990 on 2007-12-04
hi
i am a new user of ubuntu and i try to install packages without synaptic because it is not available in it.So i download files with .tar.gz extension i didnt find any problem in extracting it but when i use the terminal to install it & write (as written in the instructions) ./configure
it give me this

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

i type make then make install it doesnt install the package
plz any one can help send me reply

---

### Post by oldos2er on 2007-12-04
You probably need to install the build-essential package first:

sudo aptitude install build-essential

---

### Post by hatem1990 on 2007-12-04
i made what u said when i write ./configure it gave me this

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMAN... configure: error: Package requirements (              gtk+-2.0 >= 2.8.0             gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMAN_CFLAGS
and COMAN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.







and then i wrote make install 

make: *** No rule to make target `install'.  Stop.

and nothing is installed

plz if anyone have how to deal with this post a reply
& thanks

---

### Post by Topsiho on 2007-12-04
You write: i am a new user of ubuntu and i try to install packages without synaptic because it is not available in it.

That's correct and ...  you can really very easily get synaptic:

In a console (text screen) you  enter:

sudo apt-get install synaptic  (followed by enter)

Enter your password, and synaptic will be installed.

After that you can use synaptic to install any program you like, if it is in the repositories of Ubuntu.

Do not compile  tarballs yourself if that is not really necessary (e.g. if it is not in one of the repositories that are enabled in synaptic). The programs in these repositories are considered safe, while those that are available as tarballs (tar.gz files), that you compile yourself (even if that is great fun) may not be quite harmless. Or you should scrutinize the source code to see whether it all is what it is supposed to be).

If you know the name of a package, such as synaptic, gparted, or build-essential, you can even more easily install these in the same manner as now you are going to do with synaptic :) 

Success,

Topsiho

---

### Post by hatem1990 on 2007-12-04
you got me wrong i have synaptic but the program i need in not in synaptic

---

### Post by ruibernardo on 2007-12-04
> **hatem1990 said:**
> checking for COMAN... configure: error: Package requirements (              gtk+-2.0 >= 2.8.0             gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMAN_CFLAGS
and COMAN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
You have installed build-essential. Now you can compile and install applications from sources.

Generally the developer have a README file or a COMPILING or a INSTALL or something like that within the sources directory. One of those files should specify what packages and other sources are needed to compile the application. Please search, read and install them to have the requirements for the compilation.

If you don't do that, you will have to google for the errors that occurs when you try. In this case I "googled" for "ubuntu No package gtk+-2.0 found" and one of the first links that google returned says that you need to install the package "libgtk2.0-dev". For the second error, you need to install "libglib2.0-dev".
> **hatem1990 said:**
> and then i wrote make install 

make: *** No rule to make target `install'.  Stop.

and nothing is installed

plz if anyone have how to deal with this post a reply
& thanksYou did not pass the configure step, so no makefile was created to compile.

Once you passed the ./configure step and the "make" or "make install" command fails, solve the problem, clear the compilation directory with "make clear" and start over (sometimes from the ./configure step).

---

### Post by NathanB on 2007-12-04
The *correct* answer to your question is that you need to use Synaptic to install the 'gtk+-2.0' package before doing a "./configure...make...make install" process on your tarball.

---

### Post by hatem1990 on 2007-12-06
hey guys thanks for all these helps but i faced errors when i type make i get this

> make  all-recursive
make[1]: Entering directory `/home/hatem/Desktop/beryl-manager-0.2.1'
Making all in src
make[2]: Entering directory `/home/hatem/Desktop/beryl-manager-0.2.1/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hatem/Desktop/beryl-manager-0.2.1/src'
Making all in pixmaps
make[2]: Entering directory `/home/hatem/Desktop/beryl-manager-0.2.1/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hatem/Desktop/beryl-manager-0.2.1/pixmaps'
Making all in po
make[2]: Entering directory `/home/hatem/Desktop/beryl-manager-0.2.1/po'
file=`echo ar_AR | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar_AR.po
/bin/sh: -o: not found
make[2]: *** [ar_AR.gmo] Error 127
make[2]: Leaving directory `/home/hatem/Desktop/beryl-manager-0.2.1/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hatem/Desktop/beryl-manager-0.2.1'
make: *** [all] Error 2


and when write make install i got this

> Making install in src
make[1]: Entering directory `/home/hatem/Desktop/beryl-manager-0.2.1/src'
make[2]: Entering directory `/home/hatem/Desktop/beryl-manager-0.2.1/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'beryl-manager' '/usr/local/bin/beryl-manager'
/usr/bin/install: cannot remove `/usr/local/bin/beryl-manager': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/hatem/Desktop/beryl-manager-0.2.1/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/hatem/Desktop/beryl-manager-0.2.1/src'
make: *** [install-recursive] Error 1


---

### Post by Bablefish on 2007-12-06
Make your life simpler check out [www.getdeb.net](www.getdeb.net)

---

### Post by hatem1990 on 2007-12-06
hey thanx for this website but i realy didnt find beryl in it the only extentions i can get from beryl is .tar.gz & .rpm

---

### Post by oldos2er on 2007-12-06
Beryl is outdated; compiz-fusion is its successor. Compiz-fusion is installed by default (if your hardware supports it) in 7.10 Gutsy Gibbon. Look in System, Preferences, Appearance, Visual Effects.

---

