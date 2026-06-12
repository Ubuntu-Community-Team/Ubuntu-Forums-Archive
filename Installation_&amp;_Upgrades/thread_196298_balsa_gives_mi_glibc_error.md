---
title: "balsa gives mi glibc error"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by edemark on 2006-06-14
Hi all I have agreat problem. I have installed balsa on my drapper install basically to carry on working with it as an email client, as i used to have it on breezy hovever now after starting it up and after getting to the inbox part it just stops responding. The message is the following


balsa
** Message: init gpgme version 1.1.0
done, msgcnt=0
before load_messages: time=1150260373
after load messages: time=1150260373
non-local URL request ignored: [http://www.sms.ac/images/email/images/logo_smsac.gif](http://www.sms.ac/images/email/images/logo_smsac.gif)
non-local URL request ignored: [http://www.sms.ac/images/email/images/icon_invite.gif](http://www.sms.ac/images/email/images/icon_invite.gif)
non-local URL request ignored: [http://www.sms.ac/images/email/images/bar_header.gif](http://www.sms.ac/images/email/images/bar_header.gif)
non-local URL request ignored: [http://www.sms.ac/images/email/images/header_graphic.jpg](http://www.sms.ac/images/email/images/header_graphic.jpg)
non-local URL request ignored: [http://www.sms.ac/Themes/_images_shared/blank_headshot_smaller.jpg](http://www.sms.ac/Themes/_images_shared/blank_headshot_smaller.jpg)
non-local URL request ignored: [http://www.sms.ac/images/email/images/thumb_tour.jpg](http://www.sms.ac/images/email/images/thumb_tour.jpg)
non-local URL request ignored: [http://www.sms.ac/images/email/images/thumb_games.jpg](http://www.sms.ac/images/email/images/thumb_games.jpg)
update flow align
non-local URL request ignored: [http://www.sms.ac/images/email/images/but_join_now.gif](http://www.sms.ac/images/email/images/but_join_now.gif)
non-local URL request ignored: [http://is2.sms.ac/images/m/mercedesmovil_m.jpg](http://is2.sms.ac/images/m/mercedesmovil_m.jpg)
non-local URL request ignored: [http://is2.sms.ac/images/p/prado40_m.jpg](http://is2.sms.ac/images/p/prado40_m.jpg)
non-local URL request ignored: [http://is2.sms.ac/images/N/Noche88_m.jpg](http://is2.sms.ac/images/N/Noche88_m.jpg)
non-local URL request ignored: [http://is2.sms.ac/images/i/iberlinx68_m.jpg](http://is2.sms.ac/images/i/iberlinx68_m.jpg)
non-local URL request ignored: [http://www.sms.ac/images/email/images/but_go.gif](http://www.sms.ac/images/email/images/but_go.gif)
non-local URL request ignored: [http://www.sms.ac/images/email/images/bar_footer.gif](http://www.sms.ac/images/email/images/bar_footer.gif)
*** glibc detected *** free(): invalid pointer: 0x08538e98 ***
Leállítva


pls help i need this for working

thanks in advance

---

### Post by edemark on 2006-06-14
I hope that someone has o will have some answer to my question. I really need this

Pls help

---

### Post by edemark on 2006-06-16
Hi so I still have not given up on ubuntu but I do need balsa to work as I have my work email on balsa. So As you may observe i did not have luck with the balsa from repositories. Thus I thought to compile it from source but I get the following error message:

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  am az bg ca cs da de el en_CA en_GB es et fi fr ga he hi hr hu it ja ko lt lv ml ms nb ne nl nn no pa pl pt pt_BR ro ru rw sk sl sq sr sr@Latn sv tr uk vi wa zh_CN zh_HK zh_TW
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BALSA... configure: error: Package requirements (
glib-2.0
gtk+-2.0 >= 2.4
gmime-2.0 >= 2.1.9
libgnome-2.0 libgnomeui-2.0
   gnome-vfs-2.0 gnome-vfs-module-2.0 libbonobo-2.0
   libgnomeprint-2.2 >= 2.1.4 libgnomeprintui-2.2 >= 2.1.4
) were not met:

No package 'gtk+-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'libbonobo-2.0' found
No package 'libgnomeprint-2.2' found
No package 'libgnomeprintui-2.2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BALSA_CFLAGS
and BALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


It seems tha it just cannot find some installed packages

So if you have any ideas how to resolve it than PLS HELP

it is important

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running. First rename this file to see if it clears the issue, and if so, try a different theme. I was using "Glider" but changed to "Human" to correct this issue.

---

