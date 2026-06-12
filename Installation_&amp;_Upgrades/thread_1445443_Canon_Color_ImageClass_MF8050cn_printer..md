---
title: "Canon Color ImageClass MF8050cn printer."
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2010-04-02
I'm using Ubuntu 9.10 64-bit on an Intel i7.

I just bought a Canon color ImageClass MF8050cn laser printer and connected it to the network.  I let the software pick a driver, but when I print my document goes into a black hole never to be found again.

I also have a Mac and a Vista machine which can both connect just fine and print in color.  So it's not the printer.

Has anyone successfully made this work?  If so, what driver are you using, where do I get it if it's not in Synaptic, and what settings do I use?  I checked on the Canon site, but they only support Windows and Mac.

Before anyone goes there, I would like to use a non-generic driver for this if possible.

I'm at work right now and the printer is at home, so I can't get specifics at the moment.  I will post them later if somebody wants to help diagnose rather than just tell me what they have.

Thanks.

---

### Post by 1clue on 2010-04-03
I'm really struggling here.  Is there some 'pure printer' driver that I can use, or am I stuck with no printing from Linux at all?

---

### Post by 1clue on 2010-04-04
I found this thread:

[http://ubuntuforums.org/showthread.php?t=1140724](http://ubuntuforums.org/showthread.php?t=1140724)

The thing is, I'm using 64-bit 9.10 so the driver isn't exactly compiled for my setup.

I got the source (it comes in the archive referenced in the thread) and I'm trying to compile it.

I got the dependencies set up as far as I can tell, and It's still broken.

Is there anyone who thinks this driver might be available for 9.10 somewhere else?  I'm not having luck compiling this thing.

Here's what I'm getting:

~/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00
make gen
(cd cngplp; ./autogen.sh; make) || exit 1
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 3458764513820540925
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
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
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  fr it de es ja
configure: creating ./config.status
config.status: creating Makefile
config.status: creating cngplpmod/Makefile
config.status: creating cnjatool/Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
Now type `make' to compile.
make[1]: Entering directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp'
make  all-recursive
make[2]: Entering directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp'
Making all in po
make[3]: Entering directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp/po'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp/po'
Making all in cngplpmod
make[3]: Entering directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp/cngplpmod'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -O2 -fPIC -g -O2 -MT cngplpmod.lo -MD -MP -MF .deps/cngplpmod.Tpo -c -o cngplpmod.lo cngplpmod.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -O2 -fPIC -g -O2 -MT cngplpmod.lo -MD -MP -MF .deps/cngplpmod.Tpo -c cngplpmod.c  -fPIC -DPIC -o .libs/cngplpmod.o
In file included from cngplpmod.c:27:
cngplpmod.h:31:23: error: cups/cups.h: No such file or directory
cngplpmod.c:38: error: expected declaration specifiers or ‘...’ before ‘cups_dest_t’
cngplpmod.c:39: error: expected declaration specifiers or ‘...’ before ‘cups_dest_t’
cngplpmod.c:41: error: expected declaration specifiers or ‘...’ before ‘cups_dest_t’
cngplpmod.c: In function ‘cngplpInitOptions’:
cngplpmod.c:138: error: ‘cups_dest_t’ undeclared (first use in this function)
cngplpmod.c:138: error: (Each undeclared identifier is reported only once
cngplpmod.c:138: error: for each function it appears in.)
cngplpmod.c:138: error: ‘all_dests’ undeclared (first use in this function)
cngplpmod.c:139: error: ‘curr_dest’ undeclared (first use in this function)
cngplpmod.c:142: warning: implicit declaration of function ‘cupsGetDests’
cngplpmod.c:147: warning: implicit declaration of function ‘cupsGetDest’
cngplpmod.c:160: error: too many arguments to function ‘SetCupsStoreOption’
cngplpmod.c:175: error: too many arguments to function ‘SetPPDStoreOption’
cngplpmod.c:179: error: too many arguments to function ‘SetPPDStoreUIValue’
cngplpmod.c:188: warning: implicit declaration of function ‘cupsFreeDests’
cngplpmod.c: In function ‘GetPrinterInfo’:
cngplpmod.c:205: error: ‘cups_dest_t’ undeclared (first use in this function)
cngplpmod.c:205: error: ‘all_dests’ undeclared (first use in this function)
cngplpmod.c:206: error: ‘curr_dest’ undeclared (first use in this function)
cngplpmod.c: At top level:
cngplpmod.c:294: error: expected declaration specifiers or ‘...’ before ‘cups_dest_t’
cngplpmod.c: In function ‘SetPPDStoreOption’:
cngplpmod.c:298: error: ‘cups_option_t’ undeclared (first use in this function)
cngplpmod.c:298: error: ‘opt’ undeclared (first use in this function)
cngplpmod.c:313: error: ‘curr_printer’ undeclared (first use in this function)
cngplpmod.c: At top level:
cngplpmod.c:502: error: expected declaration specifiers or ‘...’ before ‘cups_dest_t’
cngplpmod.c: In function ‘SetCupsStoreOption’:
cngplpmod.c:506: error: ‘cups_option_t’ undeclared (first use in this function)
cngplpmod.c:506: error: ‘opt’ undeclared (first use in this function)
cngplpmod.c:508: error: ‘curr_printer’ undeclared (first use in this function)
cngplpmod.c: In function ‘CreatePPDOptions’:
cngplpmod.c:602: warning: implicit declaration of function ‘cupsGetPPD’
cngplpmod.c:602: warning: cast to pointer from integer of different size
cngplpmod.c: In function ‘DeletePPDOptions’:
cngplpmod.c:673: warning: implicit declaration of function ‘unlink’
cngplpmod.c: At top level:
cngplpmod.c:708: error: expected declaration specifiers or ‘...’ before ‘cups_dest_t’
cngplpmod.c: In function ‘SetPPDStoreUIValue’:
cngplpmod.c:711: error: ‘cups_option_t’ undeclared (first use in this function)
cngplpmod.c:711: error: ‘opt’ undeclared (first use in this function)
cngplpmod.c:711: error: ‘curr_printer’ undeclared (first use in this function)
cngplpmod.c: In function ‘CheckJobAccount’:
cngplpmod.c:771: warning: implicit declaration of function ‘getuid’
make[3]: *** [cngplpmod.lo] Error 1
make[3]: Leaving directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp/cngplpmod'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ken/Downloads/UFR_II_Printer_Driver_for_Linux_V200_uk_EN/Sources/cndrvcups-common-2.00/cngplp'
make: *** [gen] Error 1

---

### Post by 1clue on 2010-04-05
Solved!

I had to install "alien" and "rpm".  Alien allows RPM to install rpm packages, and then evidently modifies the debian package database properly.  I used the 64-bit RPMs from the archive mentioned in the above thread, and everything worked fine.

Thanks.

---

### Post by biermeister on 2012-09-18
Just found the solution after lots of searching and luck.  I'm using Ubuntu 12.04 32 bit.  The install of the deb files previously failed dependencies up until version 2.2 from canon.  I found version 2.5 worked.  I found the drivers at:

[http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/color_imageclass_mf8050cn?selectedName=DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/color_imageclass_mf8050cn?selectedName=DriversAndSoftware)

with the title:

UFR II Printer Driver for Linux Version 2.50

Just unpack the file, find the two .deb files, right click on the *common* one first and open with Ubuntu Software Centre.  Once that is installed, do the same with the second .deb file *cndrvcups-ufr2-us_2.50-1_i386* and so the same.  

Print test page.  All works.

Now I'm in UK and the mF8050cn is part of the iSENSYS range, but in the US it's Imageclass.  I've seen another name for the range, also in the US, whilst hunting for an answer.  Same printers however as far as I can tell.

Good luck, and thanks to the world of forums for helping me to the answer.

---

### Post by pdc on 2012-09-18
good work; well done; 

for the 32bit ubuntu, there are .deb packages in the UFR as you found.............for 64bit systems, Canon only seem to supply rpm packages, so alien is needed to convert these to .deb

enjoy your printer

---

