---
title: "[SOLVED] Compiling Pidgin 2.2.2 from Source (Urgent, sort of)"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by 1337455 10534 on 2007-11-10
I've peeked at [http://ubuntuforums.org/showthread.php?t=496409](http://ubuntuforums.org/showthread.php?t=496409), but I find the instructions there lacking. How do I compile the new Pidgin?
Better yet, how do you compile stuff at all?
edit>>>
```

cd srcdir
./configure
make
sudo make install

```
- -> Have space for Pidgin?
- -> Don't forget your dependencies (Synaptic -> libpurple)
- -> Checkinstall for debs

---

### Post by 1337455 10534 on 2007-11-10
Dear g**. Spoke too soon. 5 mins of compiling later:
```

family@Purple-Blanket:~/Desktop/pidgin-2.2.2$ sudo pidgin
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

```

GAAAAAAAAAAAAAAAAAAAAHHHHHHHHHH!

---

### Post by 1337455 10534 on 2007-11-10
Phew. Fixed it:
```

sudo apt-get install libpurple0 libpurple-bin libpurple dev
sudo pidgin

```
YAY!

---

### Post by dfreer on 2007-11-10
Ok, firstly, did the compile process go smoothly? Most of the time, the important errors will show up when you do this step:
./configure
Look toward the bottom of the output for any errors, or better yet just post your ouput.

Then, the libpurple0 is in the repositories (for gutsy anyways):
```
sudo apt-get install libpurple0
```

You really don't need (or want, for that matter) to run pidgin with sudo. Aside for the security risk, all of your configuration files like login name and such will be stored under the root user's account and not yours.

---

### Post by mivo on 2007-11-10
I've been trying to do the same.

I ran ./configure and got a warning saying that I already have an old copy of Pidgin at /usr/bin/pidgin. The new copy would be installed in /usr/local/bin. Is this the desired behaviour? How would I go about "replacing" the old copy or getting the new version installed in the old copy's location?

---

### Post by robrmd9 on 2007-11-10
> **mivo said:**
> I've been trying to do the same.

I ran ./configure and got a warning saying that I already have an old copy of Pidgin at /usr/bin/pidgin. The new copy would be installed in /usr/local/bin. Is this the desired behaviour? How would I go about "replacing" the old copy or getting the new version installed in the old copy's location?

So it appears you haven't uninstalled the original version of Pidgin, so when you try and build from source, it recognizes this and proposes a new location.  That is perfectly fine, but I recommend you uninstall the old version first, so things don't get confusing:

```
sudo apt-get remove pidgin
```

Then try again.

---

### Post by robrmd9 on 2007-11-10
> **1337455 10534 said:**
> Phew. Fixed it:
```

sudo apt-get install libpurple0 libpurple-bin libpurple dev
sudo pidgin

```
YAY!

Do NOT run pidgin as root, it is not a smart idea!

---

### Post by 1337455 10534 on 2007-11-10
> 
Do NOT run pidgin as root, it is not a smart idea!

Opps. Ya, it was a one time thing to see if it would work.. Really, I could have done:
```

pidgin --help

```
It says that it is 2.2.2.

Pidgin works brilliantly!!! To replace the old one, just go to Search Files and type Pidgin.
Delete everything and compile your own!
(Use my attached script to do it.. .Most of those files and dirs are need sudo's access. The first time, it runs shred, the second, rm with the recursive -r switch that deletes directories as well (that shred doesnt))

edit>> if you distributed this script, I wouldn't mind. In fact I encourage it. A lot!

---

### Post by robrmd9 on 2007-11-10
> **1337455 10534 said:**
> Opps. Ya, it was a one time thing to see if it would work.. Really, I could have done:
```

pidgin --help

```
It says that it is 2.2.2.

Pidgin works brilliantly!!! To replace the old one, just go to Search Files and type Pidgin.
Delete everything and compile your own!
(Use my attached script to do it.. .Most of those files and dirs are need sudo's access. The first time, it runs shred, the second, rm with the recursive -r switch that deletes directories as well (that shred doesnt))

edit>> if you distributed this script, I wouldn't mind. In fact I encourage it. A lot!

To remove the old version, do:

```
sudo apt-get remove pidgin
```

Please do not give out bad advice.  Searching all files for "pidgin" and deleting them is not how it should be done.

---

### Post by 1337455 10534 on 2007-11-10
> 
sudo apt-get remove pidgin

Wow. Thats a lot smarter. *smacks myslef*

---

### Post by mivo on 2007-11-10
> **robrmd9 said:**
> So it appears you haven't uninstalled the original version of Pidgin, so when you try and build from source, it recognizes this and proposes a new location.

I've been fiddling around with this on an experimental box, just for the learning experience. :) So if Pidgin were not already installed, it would be installed to /usr/bin/pidgin by default? (I dimly recall from my FreeBSD baby steps a few years ago that not all Unix-based OSes put executables in the same place -- are there differences between the different Linux distros as well?) Besides the "untidiness", is there a practical difference between a program being installed to /usr/bin/ or /usr/local/bin/? 

I did a bit of reading and learned that manually compiling newer versions of software that is in the repos is bound to confuse apt/etc. since they won't know about the manually installed new version. So I guess my next station is to learn how to compile and make a .deb file. :)

---

### Post by dfreer on 2007-11-10
I've never been entirely sure about where executables should be placed myself. Debian has a guide as to which files should be placed where for package maintainers, unfortunately I don't have the link handy.
The main thing is if you want to launch the program simply by typing it's name in the commandline, you'll need to have it in your PATH. I'm thinking /usr/bin/, /usr/local/bin/, and /bin/ are all in your PATH by default.

---

### Post by 1337455 10534 on 2007-11-11
When anyone finds out how to;
a) get source
b) make a deb file out of it
c) feed it to apt (GDebi?)
, please, do tell us how :)!

---

### Post by 1337455 10534 on 2007-11-11
Allright, I'm gonna mark this thing as SOLVED...
But, please please please take a look at [http://ubuntuforums.org/showthread.php?t=610196](http://ubuntuforums.org/showthread.php?t=610196)
if you are familiar with making debs.

---

### Post by potentia on 2007-11-11
How do you REMOVE/UNINSTALL all installed Pidgin program files and libraries if you installed it this way (compiled it).

SOLUTION:
sudo make uninstall

---

### Post by potentia on 2007-11-12
I managed to compile Pidgin 2.2.2 (I never tried to compile anything in my life before this) but it goes auto-away (idle) even when I am working on the computer. I found out that I have to compile it **with XScreensaver support**.

But how ***exactly*** do I do that? I need all the details, as you can probably figure out!

---

### Post by 1337455 10534 on 2007-11-12
[IMG]http://i238.photobucket.com/albums/ff6/vminch/Screenshot.png[/IMG]
Hope it helps, if not, install everything related to XScreensaver from Synaptic, and then try.

This is teh Pidgin I compiled myself.

---

### Post by dfreer on 2007-11-12
You may need to pass an argument to ./configure when compiling, or (more likely), you didn't get all of the libraries installed. If you can post the results of these two commands I may be able to help you out (needs to be run in your pidgin source directory):
```
./configure
./configure --help
```

---

### Post by glennric on 2007-11-13
Instead of using 
```
sudo make install
```
to install something use
```
sudo checkinstall
```
This will create a deb which you can use to install and uninstall the program.

---

### Post by mivo on 2007-11-13
Or you can just use Bruce89's repository and install Pidgin 2.2.2 from there! [https://launchpad.net/~bruce89/+archive]("https://launchpad.net/~bruce89/+archive")  :))

---

### Post by potentia on 2007-11-14
> **mivo said:**
> Or you can just use Bruce89's repository and install Pidgin 2.2.2 from there! [https://launchpad.net/~bruce89/+archive]("https://launchpad.net/%7Ebruce89/+archive")  :))

Thanks! I will use this if compiling fails. I am one stubborn son of a diddle, so I want to win this hopeless battle with the compiler! Before this I used GetDebs respository, then Debutus repo... I can't jump from third party repo to repo :)

---

### Post by mivo on 2007-11-14
> **potentia said:**
> Thanks! I will use this if compiling fails. I am one stubborn son of a diddle, so I want to win this hopeless battle! :)

I can relate to that. :) I tried to get Pidgin to compile on my other box (that I use for experiments), and it really didn't work out, so I took the shortcut. Not generally shy of challenges (been playing with ArchLinux in the past couple days -- quite good for learning), but Pidgin's one of those programs I really need to work reliably. I hope you win this battle, though!

---

### Post by potentia on 2007-11-14
> **dfreer said:**
> You may need to pass an argument to ./configure when compiling, or (more likely), you didn't get all of the libraries installed. If you can post the results of these two commands I may be able to help you out (needs to be run in your pidgin source directory):
```
./configure
./configure --help
```

Thanks. Here we go. I ran configure like this

**./configure --enable-gnutls=yes **
(gnutls for SSL support for MSN and Google Talk)[SIZE=4][B]

Output:[/B][/SIZE]
```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
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
checking whether to build static libraries... no
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
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
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn pa pl pt_BR pt ps ro ru sk sl sq sr sr@latin sv ta te th tr uk vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for GTK... yes
checking for pango... yes
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
checking for SmcSaveYourselfDone in -lSM... yes
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for STARTUP_NOTIFICATION... no
no
checking for GTKSPELL... no
no
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for SQLITE3... no
no
checking for initscr in -lncursesw... no
checking for update_panels in -lpanelw... no
checking for initscr in -lncurses... no
checking for update_panels in -lpanel... no
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... no
no
checking for MEANWHILE... no
no
checking for AVAHI... no
no
checking avahi-client/client.h usability... no
checking avahi-client/client.h presence... no
checking for avahi-client/client.h... no
checking avahi-glib/glib-malloc.h usability... no
checking avahi-glib/glib-malloc.h presence... no
checking for avahi-glib/glib-malloc.h... no
checking for avahi_client_new in -lavahi-client... no
checking for HOWL... no
no
checking for HOWL... no
no
checking howl.h usability... no
checking howl.h presence... no
checking for howl.h... no
checking for sw_discovery_init in -lhowl... no
checking for SILC... no
no
checking for SILC... no
no
checking for SILC... no
no
checking for GADU... no
no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Wendif-labels option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-noreturn option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... yes
checking for pidgin... no
checking for dbus-binding-tool... yes
checking for DBUS... yes
checking for python... /usr/bin/python
checking location of the D-Bus services directory... /usr/share/dbus-1/services
Building with D-Bus support
checking for perl... /usr/bin/perl
checking for Perl compile flags... ok
checking for libperl... checking for perl_run... no
checking EXTERN.h usability... yes
checking EXTERN.h presence... yes
checking for EXTERN.h... yes
checking for perl.h... yes
checking for GnuTLS includes... ""
checking gnutls/gnutls.h usability... yes
checking gnutls/gnutls.h presence... yes
checking for gnutls/gnutls.h... yes
checking for GnuTLS libraries... yes
checking for Mozilla nspr4 includes in ... ""
checking nspr.h usability... no
checking nspr.h presence... no
checking for nspr.h... no
checking prio.h usability... no
checking prio.h presence... no
checking for prio.h... no
checking for Mozilla nspr4 libraries... no
checking for Mozilla nss3 includes... no
checking for Mozilla nss libraries... no
checking for tclConfig.sh... no
checking for snprintf... yes
checking for connect... (cached) yes
checking for me pot o' gold... no
checking for gethostid... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
checking for random... yes
checking for strchr... yes
checking for strerror... yes
checking for vprintf... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sgtty.h usability... yes
checking sgtty.h presence... yes
checking for sgtty.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/msgbuf.h usability... no
checking sys/msgbuf.h presence... no
checking for sys/msgbuf.h... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking for sys/utsname.h... (cached) yes
checking for sys/wait.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for struct tm.tm_zone... yes
checking for timezone external... yes
checking for altzone external... no
checking for daylight external... yes
checking for tm_gmtoff in struct tm... yes
checking for CHECK... yes
checking for doxygen... false
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Doxyfile
config.status: creating doc/Makefile
config.status: creating doc/pidgin.1
config.status: creating doc/finch.1
config.status: creating m4macros/Makefile
config.status: creating pidgin.apspec
config.status: creating pidgin/Makefile
config.status: creating pidgin/pidgin.pc
config.status: creating pidgin/pidgin-uninstalled.pc
config.status: creating pidgin/pixmaps/Makefile
config.status: creating pidgin/pixmaps/animations/Makefile
config.status: creating pidgin/pixmaps/animations/16/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/qq/Makefile
config.status: creating pidgin/pixmaps/dialogs/Makefile
config.status: creating pidgin/pixmaps/dialogs/16/Makefile
config.status: creating pidgin/pixmaps/dialogs/16/scalable/Makefile
config.status: creating pidgin/pixmaps/dialogs/64/Makefile
config.status: creating pidgin/pixmaps/dialogs/64/scalable/Makefile
config.status: creating pidgin/pixmaps/emblems/Makefile
config.status: creating pidgin/pixmaps/emblems/16/Makefile
config.status: creating pidgin/pixmaps/emblems/16/scalable/Makefile
config.status: creating pidgin/pixmaps/emotes/Makefile
config.status: creating pidgin/pixmaps/emotes/default/Makefile
config.status: creating pidgin/pixmaps/emotes/default/24/Makefile
config.status: creating pidgin/pixmaps/emotes/default/24/scalable/Makefile
config.status: creating pidgin/pixmaps/emotes/none/Makefile
config.status: creating pidgin/pixmaps/icons/Makefile
config.status: creating pidgin/pixmaps/icons/16/Makefile
config.status: creating pidgin/pixmaps/icons/16/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/22/Makefile
config.status: creating pidgin/pixmaps/icons/22/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/24/Makefile
config.status: creating pidgin/pixmaps/icons/24/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/32/Makefile
config.status: creating pidgin/pixmaps/icons/32/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/48/Makefile
config.status: creating pidgin/pixmaps/icons/48/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/Makefile
config.status: creating pidgin/pixmaps/protocols/16/Makefile
config.status: creating pidgin/pixmaps/protocols/16/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/22/Makefile
config.status: creating pidgin/pixmaps/protocols/22/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/48/Makefile
config.status: creating pidgin/pixmaps/protocols/48/scalable/Makefile
config.status: creating pidgin/pixmaps/status/Makefile
config.status: creating pidgin/pixmaps/status/11/Makefile
config.status: creating pidgin/pixmaps/status/11/scalable/Makefile
config.status: creating pidgin/pixmaps/status/11/rtl/Makefile
config.status: creating pidgin/pixmaps/status/16/Makefile
config.status: creating pidgin/pixmaps/status/16/rtl/Makefile
config.status: creating pidgin/pixmaps/status/16/scalable/Makefile
config.status: creating pidgin/pixmaps/status/22/Makefile
config.status: creating pidgin/pixmaps/status/22/rtl/Makefile
config.status: creating pidgin/pixmaps/status/22/scalable/Makefile
config.status: creating pidgin/pixmaps/status/32/Makefile
config.status: creating pidgin/pixmaps/status/32/rtl/Makefile
config.status: creating pidgin/pixmaps/status/32/scalable/Makefile
config.status: creating pidgin/pixmaps/status/48/Makefile
config.status: creating pidgin/pixmaps/status/48/rtl/Makefile
config.status: creating pidgin/pixmaps/toolbar/Makefile
config.status: creating pidgin/pixmaps/toolbar/16/Makefile
config.status: creating pidgin/pixmaps/toolbar/16/scalable/Makefile
config.status: creating pidgin/pixmaps/toolbar/22/Makefile
config.status: creating pidgin/pixmaps/toolbar/22/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/Makefile
config.status: creating pidgin/pixmaps/tray/16/Makefile
config.status: creating pidgin/pixmaps/tray/16/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/22/Makefile
config.status: creating pidgin/pixmaps/tray/22/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/32/Makefile
config.status: creating pidgin/pixmaps/tray/48/Makefile
config.status: creating pidgin/plugins/Makefile
config.status: creating pidgin/plugins/cap/Makefile
config.status: creating pidgin/plugins/gestures/Makefile
config.status: creating pidgin/plugins/gevolution/Makefile
config.status: creating pidgin/plugins/musicmessaging/Makefile
config.status: creating pidgin/plugins/perl/Makefile
config.status: creating pidgin/plugins/perl/common/Makefile.PL
config.status: creating pidgin/plugins/ticker/Makefile
config.status: creating libpurple/example/Makefile
config.status: creating libpurple/gconf/Makefile
config.status: creating libpurple/purple.pc
config.status: creating libpurple/purple-uninstalled.pc
config.status: creating libpurple/plugins/Makefile
config.status: creating libpurple/plugins/mono/Makefile
config.status: creating libpurple/plugins/mono/api/Makefile
config.status: creating libpurple/plugins/mono/loader/Makefile
config.status: creating libpurple/plugins/perl/Makefile
config.status: creating libpurple/plugins/perl/common/Makefile.PL
config.status: creating libpurple/plugins/ssl/Makefile
config.status: creating libpurple/plugins/tcl/Makefile
config.status: creating libpurple/Makefile
config.status: creating libpurple/protocols/Makefile
config.status: creating libpurple/protocols/bonjour/Makefile
config.status: creating libpurple/protocols/gg/Makefile
config.status: creating libpurple/protocols/irc/Makefile
config.status: creating libpurple/protocols/jabber/Makefile
config.status: creating libpurple/protocols/msn/Makefile
config.status: creating libpurple/protocols/myspace/Makefile
config.status: creating libpurple/protocols/novell/Makefile
config.status: creating libpurple/protocols/null/Makefile
config.status: creating libpurple/protocols/oscar/Makefile
config.status: creating libpurple/protocols/qq/Makefile
config.status: creating libpurple/protocols/sametime/Makefile
config.status: creating libpurple/protocols/silc/Makefile
config.status: creating libpurple/protocols/silc10/Makefile
config.status: creating libpurple/protocols/simple/Makefile
config.status: creating libpurple/protocols/toc/Makefile
config.status: creating libpurple/protocols/yahoo/Makefile
config.status: creating libpurple/protocols/zephyr/Makefile
config.status: creating libpurple/tests/Makefile
config.status: creating libpurple/version.h
config.status: creating share/Makefile
config.status: creating share/sounds/Makefile
config.status: creating share/ca-certs/Makefile
config.status: creating finch/finch.pc
config.status: creating finch/Makefile
config.status: creating finch/libgnt/Makefile
config.status: creating finch/libgnt/gnt.pc
config.status: creating finch/libgnt/wms/Makefile
config.status: creating finch/plugins/Makefile
config.status: creating po/Makefile.in
config.status: creating pidgin.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

pidgin 2.2.2

Build GTK+ 2.x UI............. : yes
Build console UI.............. : no
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : gg irc jabber msn myspace novell oscar qq simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : no
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : no

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.

configure complete, now type 'make'

```**./configure --help**

[SIZE=4]**Output:**[/SIZE]
```
./configure --help
`configure' configures pidgin 2.2.2 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --datarootdir=DIR      read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR          read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR          info documentation [DATAROOTDIR/info]
  --localedir=DIR        locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR           man documentation [DATAROOTDIR/man]
  --docdir=DIR           documentation root [DATAROOTDIR/doc/pidgin]
  --htmldir=DIR          html documentation [DOCDIR]
  --dvidir=DIR           dvi documentation [DOCDIR]
  --pdfdir=DIR           pdf documentation [DOCDIR]
  --psdir=DIR            ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

X features:
  --x-includes=DIR    X include files are in DIR
  --x-libraries=DIR   X library files are in DIR

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]
  --target=TARGET   configure for building compilers for TARGET [HOST]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-static[=PKGS]  build static libraries [default=no]
  --enable-shared[=PKGS]  build shared libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-largefile     omit support for large files
  --disable-gtkui         compile without GTK+ user interface
  --disable-consoleui     compile without console user interface
  --disable-screensaver   compile without X screensaver extension (used to
                          detect idleness)
  --disable-sm            compile without X session management support
  --disable-startup-notification
                          compile without startup notification support
  --disable-gtkspell      compile without GtkSpell automatic spell checking
  --disable-gevolution    compile without the Evolution plugin
  --disable-cap           compile without Contact Availability Prediction
                          plugin
  --disable-gestures      compile without the gestures plugin
  --disable-schemas-install     Disable the schemas installation
  --disable-gstreamer     compile without GStreamer audio support

  --disable-plugins       compile without plugin support
  --disable-fortify       compile without FORTIFY_SOURCE support
  --enable-dbus           enable D-Bus support
  --enable-nm             enable NetworkManager support (buggy) (requires
                          D-Bus)
  --enable-mono           compile with Mono runtime support (experimental)
  --disable-perl          compile without perl scripting
  --enable-gnutls=yes,no  attempt to use GnuTLS for SSL support (preferred) default=yes
  --enable-nss=yes,no,static    attempt to use Mozilla libnss for SSL support default=yes
  --disable-tcl           compile without Tcl scripting
  --disable-tk            compile without Tcl support for Tk
  --enable-cyrus-sasl     enable Cyrus SASL support for jabberd
  --disable-doxygen       enable documentation with doxygen
  --enable-dot            enable graphs in doxygen via 'dot'
  --enable-debug          compile with debugging support

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-pic              try to use only PIC/non-PIC objects [default=use
                          both]
  --with-tags[=TAGS]      include additional configurations [automatic]

  --with-x                use the X Window System
  --with-ncurses-headers=DIR
                          compile finch against the ncurses includes in DIR
  --with-gconf-source=sourceaddress      Config database for installing schema files.
  --with-gconf-schema-file-dir=dir        Directory for installing schema files.
  --with-avahi-client-includes=DIR
                          compile the Bonjour plugin against the Avahi Client
                          includes in DIR
  --with-avahi-client-libs=DIR
                          compile the Bonjour plugin against the Avahi Client
                          libs in DIR
  --with-howl-includes=DIR
                          compile the Bonjour plugin against the Howl includes
                          in DIR
  --with-howl-libs=DIR    compile the Bonjour plugin against the Howl libs in
                          DIR
  --with-silc-includes=DIR
                          compile the SILC plugin against includes in DIR
  --with-silc-libs=DIR    compile the SILC plugin against the SILC libs in DIR
  --with-gadu-includes=DIR
                          compile the Gadu-Gadu plugin against includes in DIR
  --with-gadu-libs=DIR    compile the Gadu-Gadu plugin against the libs in DIR
  --with-static-prpls     Link to certain protocols statically
  --with-dynamic-prpls    specify which protocols to build dynamically
  --with-krb4=PREFIX      compile Zephyr plugin with Kerberos 4 support
  --with-zephyr=PREFIX    compile Zephyr plugin against external libzephyr
  --with-python=PATH      which python interpreter to use for dbus code
                          generation
  --with-dbus-services=<dir>
                          where the D-Bus services directory is located.
  --with-perl-lib=site|vendor|DIR
                          specify where to install the Perl libraries for
                          pidgin. Default is site.
  --with-gnutls-includes=PREFIX   location of GnuTLS includes.
  --with-gnutls-libs=PREFIX
                          location of GnuTLS libraries.
  --with-nspr-includes=PREFIX
                          specify location of Mozilla nspr4 includes.
  --with-nspr-libs=PREFIX specify location of Mozilla nspr4 libs.
  --with-nss-includes=PREFIX
                          specify location of Mozilla nss3 includes.
  --with-nss-libs=PREFIX  specify location of Mozilla nss3 libs.
  --with-tclconfig=DIR    directory containing tclConfig.sh
  --with-tkconfig=DIR     directory containing tkConfig.sh
  --with-check=PATH       prefix where check is installed default=auto

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    C/C++/Objective C preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CXXCPP      C++ preprocessor
  F77         Fortran 77 compiler command
  FFLAGS      Fortran 77 compiler flags
  PKG_CONFIG  path to pkg-config utility
  GLIB_CFLAGS C compiler flags for GLIB, overriding pkg-config
  GLIB_LIBS   linker flags for GLIB, overriding pkg-config
  XMKMF       Path to xmkmf, Makefile generator for X Window System
  GTK_CFLAGS  C compiler flags for GTK, overriding pkg-config
  GTK_LIBS    linker flags for GTK, overriding pkg-config
  pango_CFLAGS
              C compiler flags for pango, overriding pkg-config
  pango_LIBS  linker flags for pango, overriding pkg-config
  X11_CFLAGS  C compiler flags for X11, overriding pkg-config
  X11_LIBS    linker flags for X11, overriding pkg-config
  STARTUP_NOTIFICATION_CFLAGS
              C compiler flags for STARTUP_NOTIFICATION, overriding pkg-config
  STARTUP_NOTIFICATION_LIBS
              linker flags for STARTUP_NOTIFICATION, overriding pkg-config
  GTKSPELL_CFLAGS
              C compiler flags for GTKSPELL, overriding pkg-config
  GTKSPELL_LIBS
              linker flags for GTKSPELL, overriding pkg-config
  EVOLUTION_ADDRESSBOOK_CFLAGS
              C compiler flags for EVOLUTION_ADDRESSBOOK, overriding
              pkg-config
  EVOLUTION_ADDRESSBOOK_LIBS
              linker flags for EVOLUTION_ADDRESSBOOK, overriding pkg-config
  SQLITE3_CFLAGS
              C compiler flags for SQLITE3, overriding pkg-config
  SQLITE3_LIBS
              linker flags for SQLITE3, overriding pkg-config
  LIBXML_CFLAGS
              C compiler flags for LIBXML, overriding pkg-config
  LIBXML_LIBS linker flags for LIBXML, overriding pkg-config
  GSTREAMER_CFLAGS
              C compiler flags for GSTREAMER, overriding pkg-config
  GSTREAMER_LIBS
              linker flags for GSTREAMER, overriding pkg-config
  MEANWHILE_CFLAGS
              C compiler flags for MEANWHILE, overriding pkg-config
  MEANWHILE_LIBS
              linker flags for MEANWHILE, overriding pkg-config
  AVAHI_CFLAGS
              C compiler flags for AVAHI, overriding pkg-config
  AVAHI_LIBS  linker flags for AVAHI, overriding pkg-config
  HOWL_CFLAGS C compiler flags for HOWL, overriding pkg-config
  HOWL_LIBS   linker flags for HOWL, overriding pkg-config
  SILC_CFLAGS C compiler flags for SILC, overriding pkg-config
  SILC_LIBS   linker flags for SILC, overriding pkg-config
  GADU_CFLAGS C compiler flags for GADU, overriding pkg-config
  GADU_LIBS   linker flags for GADU, overriding pkg-config
  DBUS_CFLAGS C compiler flags for DBUS, overriding pkg-config
  DBUS_LIBS   linker flags for DBUS, overriding pkg-config
  LIBNM_CFLAGS
              C compiler flags for LIBNM, overriding pkg-config
  LIBNM_LIBS  linker flags for LIBNM, overriding pkg-config
  MONO_CFLAGS C compiler flags for MONO, overriding pkg-config
  MONO_LIBS   linker flags for MONO, overriding pkg-config
  NSS_CFLAGS  C compiler flags for NSS, overriding pkg-config
  NSS_LIBS    linker flags for NSS, overriding pkg-config
  CHECK_CFLAGS
              C compiler flags for CHECK, overriding pkg-config
  CHECK_LIBS  linker flags for CHECK, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to <devel@pidgin.im>.
```TIA

---

### Post by dfreer on 2007-11-14
You are missing a bunch of libraries, if you notice at the end of your ./configure:
```
Build GTK+ 2.x UI............. : yes
Build console UI.............. : no
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : gg irc jabber msn myspace novell oscar qq simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : no
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

**Use XScreenSaver Extension.... : no**
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : no

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no

Print debugging messages...... : no
```

A quick way to get most of those needed libaries is to try this command for feisty:
```
sudo apt-get build-dep gaim
```
Which should grab all of the libraries needed to compile gaim, which should include most of the ones needed for pidgin. On gutsy, you should be able to do it this way:
```
sudo apt-get build-dep pidgin
```

Once you do that, try running ./configure again. In particular, since you are looking for XScreenSaver Support, you'll want to be on the lookout for the line highlighted in bold above.

---

### Post by potentia on 2007-11-14
Thank you! :KS

---

### Post by potentia on 2007-11-14
No success on Gutsy:

```
sudo apt-get build-dep pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/debian.tagancha.org_debian_dists_dapper_restricted_source_Sources - open (2 No such file or directory)

```Thanks for your help though.

---

### Post by 1337455 10534 on 2007-11-14
Apparently that file does not exist... I will post mine for you once I get on my Ubuntu box..

---

### Post by dfreer on 2007-11-15
What's your /etc/apt/sources.list look like, potentia? That error sounds like something is wrong with apt, does this command run without any problems?:
```
sudo apt-get update
```

---

### Post by potentia on 2007-11-15
```
 sudo apt-get update
Get:1 http://dk.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://dk.archive.ubuntu.com gutsy/main Translation-en_DK                  
Ign http://dk.archive.ubuntu.com gutsy/restricted Translation-en_DK            
Ign http://dk.archive.ubuntu.com gutsy/universe Translation-en_DK              
Ign http://dk.archive.ubuntu.com gutsy/multiverse Translation-en_DK            
Get:2 http://dk.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://dk.archive.ubuntu.com gutsy-updates/main Translation-en_DK          
Ign http://dk.archive.ubuntu.com gutsy-updates/restricted Translation-en_DK    
Ign http://dk.archive.ubuntu.com gutsy-updates/universe Translation-en_DK      
Ign http://dk.archive.ubuntu.com gutsy-updates/multiverse Translation-en_DK    
Get:3 http://dk.archive.ubuntu.com gutsy-security Release.gpg [191B]           
Ign http://dk.archive.ubuntu.com gutsy-security/main Translation-en_DK         
Ign http://dk.archive.ubuntu.com gutsy-security/restricted Translation-en_DK   
Ign http://dk.archive.ubuntu.com gutsy-security/universe Translation-en_DK     
Ign http://dk.archive.ubuntu.com gutsy-security/multiverse Translation-en_DK   
Get:4 http://dk.archive.ubuntu.com gutsy-backports Release.gpg [191B]          
Ign http://dk.archive.ubuntu.com gutsy-backports/main Translation-en_DK        
Ign http://dk.archive.ubuntu.com gutsy-backports/restricted Translation-en_DK  
Ign http://dk.archive.ubuntu.com gutsy-backports/universe Translation-en_DK    
Ign http://dk.archive.ubuntu.com gutsy-backports/multiverse Translation-en_DK  
Get:5 http://dk.archive.ubuntu.com gutsy Release [65,9kB]                      
Get:6 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_DK               
Get:7 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Hit http://archive.canonical.com gutsy Release                                 
Hit http://archive.ubuntu.com gutsy Release                                    
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_DK                      
Ign http://ppa.launchpad.net gutsy/universe Translation-en_DK                  
Hit http://ppa.launchpad.net gutsy Release                                     
Ign http://ppa.launchpad.net gutsy/main Packages                               
Get:8 http://www.getautomatix.com gutsy Release.gpg [189B]                     
Ign http://www.getautomatix.com gutsy/main Translation-en_DK                   
Ign http://ppa.launchpad.net gutsy/universe Packages                           
Ign http://ppa.launchpad.net gutsy/main Sources                                
Ign http://ppa.launchpad.net gutsy/universe Sources                            
Ign http://archive.canonical.com gutsy/partner Packages                        
Ign http://archive.canonical.com gutsy/partner Sources                         
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://ppa.launchpad.net gutsy/universe Packages                           
Hit http://ppa.launchpad.net gutsy/main Sources                                
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://ppa.launchpad.net gutsy/universe Sources                            
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://archive.canonical.com gutsy/partner Sources                         
Ign http://debian.tagancha.org dapper Release.gpg                              
Hit http://www.getautomatix.com gutsy Release                                  
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Hit http://www.getautomatix.com gutsy/main Packages                            
Ign http://debian.tagancha.org dapper/main Translation-en_DK                   
Ign http://getswiftfox.com unstable Release.gpg                                
Ign http://getswiftfox.com unstable/non-free Translation-en_DK                 
Ign http://debian.tagancha.org dapper/restricted Translation-en_DK             
Get:9 http://dk.archive.ubuntu.com gutsy-updates Release [58,5kB]              
Ign http://getswiftfox.com unstable Release                                    
Ign http://debian.tagancha.org dapper Release                               
Ign http://getswiftfox.com unstable/non-free Packages 
Get:10 http://dk.archive.ubuntu.com gutsy-security Release [51,2kB]            
Hit http://getswiftfox.com unstable/non-free Packages                          
Ign http://debian.tagancha.org dapper/main Packages                            
Ign http://debian.tagancha.org dapper/restricted Packages
Ign http://debian.tagancha.org dapper/main Sources                             
Get:11 http://dk.archive.ubuntu.com gutsy-backports Release [37,0kB]           
Ign http://debian.tagancha.org dapper/restricted Sources                       
Get:12 http://dk.archive.ubuntu.com gutsy-backports Release [37,0kB]           
Hit http://dk.archive.ubuntu.com gutsy/main Packages                           
Hit http://dk.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://dk.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://dk.archive.ubuntu.com gutsy/main Sources                            
Hit http://dk.archive.ubuntu.com gutsy/multiverse Sources                      
Hit http://dk.archive.ubuntu.com gutsy/universe Sources                        
Hit http://dk.archive.ubuntu.com gutsy/universe Packages                       
Hit http://dk.archive.ubuntu.com gutsy/multiverse Packages                     
Get:13 http://dk.archive.ubuntu.com gutsy-updates/main Packages [31,2kB]       
Get:14 http://dk.archive.ubuntu.com gutsy-updates/restricted Packages [4263B]  
Get:15 http://dk.archive.ubuntu.com gutsy-updates/restricted Sources [937B]    
Get:16 http://dk.archive.ubuntu.com gutsy-updates/main Sources [8963B]         
Get:17 http://dk.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]     
Get:18 http://dk.archive.ubuntu.com gutsy-updates/universe Sources [2560B]     
Get:19 http://dk.archive.ubuntu.com gutsy-updates/universe Packages [14,2kB]   
Get:20 http://dk.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]  
Get:21 http://dk.archive.ubuntu.com gutsy-security/main Packages [15,0kB]      
Get:22 http://dk.archive.ubuntu.com gutsy-security/restricted Packages [14B]   
Get:23 http://dk.archive.ubuntu.com gutsy-security/restricted Sources [14B]    
Get:24 http://dk.archive.ubuntu.com gutsy-security/main Sources [3933B]        
Get:25 http://dk.archive.ubuntu.com gutsy-security/multiverse Sources [14B]    
Get:26 http://dk.archive.ubuntu.com gutsy-security/universe Sources [1863B]    
Get:27 http://dk.archive.ubuntu.com gutsy-security/universe Packages [9744B]   
Get:28 http://dk.archive.ubuntu.com gutsy-security/multiverse Packages [599B]  
Get:29 http://dk.archive.ubuntu.com gutsy-backports/main Packages [3648B]      
Get:30 http://dk.archive.ubuntu.com gutsy-backports/restricted Packages [14B]  
Get:31 http://dk.archive.ubuntu.com gutsy-backports/universe Packages [5537B]  
Get:32 http://dk.archive.ubuntu.com gutsy-backports/multiverse Packages [14B]  
Get:33 http://dk.archive.ubuntu.com gutsy-backports/main Sources [1792B]       
Get:34 http://dk.archive.ubuntu.com gutsy-backports/restricted Sources [14B]   
Get:35 http://dk.archive.ubuntu.com gutsy-backports/universe Sources [2268B]   
Get:36 http://dk.archive.ubuntu.com gutsy-backports/multiverse Sources [14B]   
Err http://debian.tagancha.org dapper/main Packages                            
  404 Not Found
Err http://debian.tagancha.org dapper/restricted Packages
  404 Not Found
Err http://debian.tagancha.org dapper/main Sources      
  404 Not Found
Err http://debian.tagancha.org dapper/restricted Sources
  404 Not Found
Fetched 324kB in 6s (53,5kB/s)                                                 
Failed to fetch http://debian.tagancha.org/debian/dists/dapper/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://debian.tagancha.org/debian/dists/dapper/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://debian.tagancha.org/debian/dists/dapper/main/source/Sources.gz  404 Not Found
Failed to fetch http://debian.tagancha.org/debian/dists/dapper/restricted/source/Sources.gz  404 Not Found
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by dfreer on 2007-11-15
Note those errors at the bottom of the output you just posted? It seems like it mainly has to do with /etc/apt/sources.list, you'll probably need to comment out a few lines.

---

### Post by trusatori on 2007-11-15
For those running Gutsy, you may want to check out my fresh tutorial for compiling Pidgin properly.  Post any questions you have in the thread and I'll see what I can do. ;]

[http://ubuntuforums.org/showthread.php?p=3771134](http://ubuntuforums.org/showthread.php?p=3771134)

---

### Post by potentia on 2007-11-15
> **dfreer said:**
> Note those errors at the bottom of the output you just posted? It seems like it mainly has to do with /etc/apt/sources.list, you'll probably need to comment out a few lines.

Okay, thanks so much for your help. I am running 2.2.2 from the repo suggested in a previous post, but I am in the process of removing Linux entirely (just hate removing boot manager and fiddling with partitions), but your patience was appreciated.

Also thank you to trusatori, that is exactly what I needed in the first place. I wonder why HOW-TO's like this one isn't available at the Pidgin site.

---

### Post by dfreer on 2007-11-15
Generally, software developers don't list compiling procedures because the process may be different depending on the linux distro you are using, as well which architecture you have, and they should be more concerned with bugs and the software itself. 

It's generally up to the package maintainers (like those who upload packages to the debian/ubuntu repositories) to compile the source code and create packages for users. In this case, due to the "newness" of pidgin and the locking of the repositories (sometime before a release is made, the repositories are "locked" so no new packages may enter, except in certain cases like security flaws or major bug fixes), only gutsy has pidgin.

BTW, this is from my memory, so I may have missed several points.

---

### Post by ImpressMe on 2007-11-15
> **dfreer said:**
> Note those errors at the bottom of the output you just posted? It seems like it mainly has to do with /etc/apt/sources.list, you'll probably need to comment out a few lines.

@potentia
Do you have Automatix installed? It installed some line related to 'partners' on my sources.list - I disabled this particular line and the warning disappeared.

---

### Post by 1337455 10534 on 2007-11-15
Clean Install Count:
Automatix: 3
My Scipt That Does The Exact Same Thing (Almost*) Better That Is Cross-Distribution (not yet*) That has Fully Funtional Utilities but no cool name: 0

---

