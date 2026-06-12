---
title: "install software from source"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Thropcat on 2007-11-07
heya,

i have been trying all day to install different software from the source and not had much luck, so i've decided its time to ask for help.

i installed build-essential, right clicked on the folder (i had already extracted it) and clicked "open terminal here"  then i put ./configure  which then came witha message saying that it can't find the pkg config, well i download that and installed it and now i get a message saying it still cant find it. 

Thanks a lot,
Ned

---

### Post by Pumalite on 2007-11-07
Compiling is not recommended for a newbie. But here is a link:

[http://www.kolab.org/pipermail/kolab-users/2007-October/006927.html](http://www.kolab.org/pipermail/kolab-users/2007-October/006927.html)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=527292](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=527292)

Good luck.

---

### Post by Thropcat on 2007-11-08
i know its not the easiest way to do it but i can't get an internet connection on the laptop or find the any .deb.

it says that PKG-config is not in the path?  do i need to move it or type it or what?

Cheers

---

### Post by taurus on 2007-11-08
Can you post the whole error message?  What are you trying to build from source anyway?

---

### Post by Thropcat on 2007-11-08
throp@Thropcat:~/Desktop/rhythmbox-0.10.1$ sh ./configure
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
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking whether byte ordering is bigendian... no
checking for long... yes
checking size of long... 4
checking for GNU extension fwrite_unlocked... yes
checking for mkdtemp... yes
checking for g_utf8_collate_key_for_filename in -lglib-2.0... no
checking for g_mapped_file_new in -lglib-2.0... no
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for RB_CLIENT... configure: error: Package requirements (gnome-vfs-2.0 >= 2.7.4) were not met:

Package gnome-vfs-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-vfs-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RB_CLIENT_CFLAGS
and RB_CLIENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

throp@Thropcat:~/Desktop/rhythmbox-0.10.1$ 




im trying to install rhythmbox, listen, and a maze game

Cheers

---

### Post by taurus on 2007-11-08
As you can see from the error message, configure is looking for gnome-vfs so you need to go into synaptic and Search for that package.  You probably need the dev package. 

Any reason why you want to build rhythmbox from source besides getting a good practice of building something from source since it's available in the repos?

---

### Post by Thropcat on 2007-11-08
i've found it in synaptic but what do i do now? it says i've go the latest version.

the only reason i didn't get a binary version is cos i had other things to install from the source and it was the first one that came up in google.

Cheers

---

### Post by Thropcat on 2007-11-08
Please?

---

### Post by erginemr on 2007-11-08
> **Thropcat said:**
> Please?

Hello there. 

Come on bro, you really don't need to install Rhythmbox from the source, it is the default audio player in Ubuntu. And if you don't already have it under the "Sound & Video" menu, that is, if you have deliberately uninstalled it, the repositories already have a working copy of Rhythmbox, which is even a later version than the one you are trying to install. (I am writing all this, assuming that you are using Gutsy:)

So, believe me, it really is not worth the effort. Just a plain:
sudo aptitude install rhythmbox 
will do the trick.

P.S. Alternatively, you may try listen with:
sudo aptitude install listen
with, IMHO, is even better than Rhythmbox in terms of usability and features.

---

### Post by erginemr on 2007-11-08
> **Thropcat said:**
> i've found it in synaptic but what do i do now? it says i've go the latest version.

the only reason i didn't get a binary version is cos i had other things to install from the source and it was the first one that came up in google.

Cheers

By the way, when installing from source, kindly note that the source package needs the development libraries (*-devs in short), not the normal packages that your system is already using. So, say if any package you are trying to install cries for some libgnome-vfs, it actually needs its development package: libgnome-vfs-dev to build the program.

This was just for your information.

---

