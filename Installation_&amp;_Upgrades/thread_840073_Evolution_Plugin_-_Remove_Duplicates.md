---
title: "Evolution Plugin - Remove Duplicates"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by geoffatmk on 2008-06-25
Recently upgraded to HH and lost my usefule remove duplicates plugin for evolution that identified and removed duplicated emails.

Have tried to reinstall remove-duplicates-plugin_0.0.4-1_i386.deb but it does not appear in the plugins list any more so I guess the upgrade has broken a link somewhere.

Has anyone got this to work or is there a plan to release an Ubuntu version of this really useful tool?

Geoff

---

### Post by ulysses222 on 2008-07-03
Same here. I found the deb actually, but it doesn't work for me.

[http://ubuntuforums.org/attachment.php?attachmentid=75479&d=1214575866](http://ubuntuforums.org/attachment.php?attachmentid=75479&d=1214575866)

---

### Post by tgehrig on 2008-07-30
The package posted in the link above is compiled against a older version of evolution. Thus the plugin is installed in a directory that evolution is not looking for plugins in. I have attached a package build against the current version of evolution in Hardy.

---

### Post by gasilva on 2009-05-11
I have install the .deb package, the evolution is showing the remove duplicates option but when I try to run it, the evolution crashes and closes.
 I am using jaunty.

---

### Post by frogotronic on 2009-10-29
Here's for Intrepid, for Jaunty you'll need to convert from Fedora 11

```
sudo alien <rpm_package>
```

---

### Post by JBAGroup on 2009-11-02
Here's the fix.  Use System=>Adminitration=>Synaptic Package Manager to install evolution-dev and required components.  Then, download the version-appropriate plugin from [this site]("http://www.gnome.org/%7Ecarlosg/stuff/evolution/").  Unzip the archive in a convenient location on the host machine.  Read and follow the simple instructions contained in the INSTALL file found in the unzipped package.  Restart your Evolution client.  Select a block of emails, right click and select "Remove Duplicates".  Wait a few seconds (longer if block is large).  Click the Delete key when duplicate report appears.  Works like a dream!

---

### Post by toobaz on 2009-12-09
Those having the same issue may be interested in:
[https://launchpad.net/~toobaz/+archive/toobaz/+packages](https://launchpad.net/~toobaz/+archive/toobaz/+packages)

bye

Pietro

---

### Post by conchyliferous on 2009-12-10
Thank you so much for that .deb!

I was looking for a way to install the duplicate remover yesterday and was really turned down when realizing that I needed evolution-dev and a million dependicies. 

And today, problem solved!

A plugin shouldn't really be necessary. Couldn't be so hard for Evolution to check for duplicates when grabbing e-mails. Guess that could be fixed soon by pure awesomeness of the community!

---

### Post by geoffatmk on 2009-12-15
Thanks Pietro that works fine for me too in Karmic

---

### Post by chitragurung on 2009-12-16
I have been using evolution since last couple of months. Now I got lots of duplicate mails when I import from Ms Outlook. I found remove duplicates from Gnome site and downloaded it in my computer and also extracted and try to install it never successful. Also some forum advised to add some applications from Synapic software manager. I did some time but still could not fix it. Which file or application should add from Synapic ?

Also how to install remove duplicates ? which version should I use ?

When I try to configure I got the following
chitra@chitra:~$ cd remove-duplicates-plugin-0.0.4
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for intltool >= 0.29... 0.36.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for ANSI C header files... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for REMOVE_DUPLICATES_PLUGIN... configure: error: Package requirements (
          evolution-plugin >= 2.3.2
          ) were not met:

No package 'evolution-plugin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables REMOVE_DUPLICATES_PLUGIN_CFLAGS
and REMOVE_DUPLICATES_PLUGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

chitra@chitra:~/remove-duplicates-plugin-0.0.4$ 
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ 

Than I did the make install and got the result as follows
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ make install
make: *** No rule to make target `install'.  Stop.
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ chitra@chitra:~/remove-duplicates-plugin-0.0.4$ 
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ make install
make: *** No rule to make target `install'.  Stop.
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ install
install: missing file operand
Try `install --help' for more information.
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ sudo install
[sudo] password for chitra: 
install: missing file operand
Try `install --help' for more information.
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ sudo make install
make: *** No rule to make target `install'.  Stop.
chitra@chitra:~/remove-duplicates-plugin-0.0.4$

---

### Post by geoffatmk on 2009-12-16
Chitragurung, what version of ubuntu are you using (I assume you are using ubunut as you are on the ubuntu forum)?

What version of evolution are you using?

If you post these we will try to help you.

---

### Post by chitragurung on 2009-12-16
how to find what version is it ?

---

### Post by chitragurung on 2009-12-16
it says ubuntu 8.04 I think

---

### Post by geoffatmk on 2009-12-16
Try

# uname -a

and

# cat /etc/issue

Then post both results

---

### Post by chitragurung on 2009-12-16
here is the result

chitra@chitra:~$ # uname -a
chitra@chitra:~$ # cat /etc/issue
chitra@chitra:~$ sudo uname -a
[sudo] password for chitra: 
Linux chitra 2.6.24-24-lpia #1 SMP Wed May 6 17:43:36 UTC 2009 i686 GNU/Linux
chitra@chitra:~$ sudo cat /etc/issue
Ubuntu 8.04.2 \n \l

chitra@chitra:~$

---

### Post by geoffatmk on 2009-12-17
You are running the long term support Hardy Heron.  You need to find the plugin that works for this version as evolution keeps moing the plugins folder so one version does not always work with the plugin build for another.  Best to try from the source file not a .deb.

Take a look here

[http://georgia.ubuntuforums.org/showthread.php?p=8059339](http://georgia.ubuntuforums.org/showthread.php?p=8059339)

and here (I am not sure but I think this should work with Hardy)

[http://www.gnome.org/~carlosg/stuff/evolution/](http://www.gnome.org/~carlosg/stuff/evolution/)

The alternative would be to upgrade to Karmic Koala.  Have you nto considered that?

Anyway, good luck and let us know how you get on.

---

### Post by chitragurung on 2009-12-17
I think almost there but still not complete.

I have the following result

Fetched 15.4MB in 21min16s (12.1kB/s)                                          
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 105640 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.11-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.4-1_lpia.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.3-1_lpia.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-2_lpia.deb) ...
Selecting previously deselected package libpthread-stubs0.
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.1-2_lpia.deb) ...
Selecting previously deselected package libpthread-stubs0-dev.
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.1-2_lpia.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-2_lpia.deb) ...
Selecting previously deselected package libxcb1-dev.
Unpacking libxcb1-dev (from .../libxcb1-dev_1.1-1ubuntu1_lpia.deb) ...
Selecting previously deselected package libxcb-xlib0-dev.
Unpacking libxcb-xlib0-dev (from .../libxcb-xlib0-dev_1.1-1ubuntu1_lpia.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.2-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.4-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.3-1ubuntu2_lpia.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-2ubuntu1_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.3-2_lpia.deb) ...
Selecting previously deselected package x11proto-composite-dev.
Unpacking x11proto-composite-dev (from .../x11proto-composite-dev_1%3a0.4-2_all.deb) ...
Selecting previously deselected package libxcomposite-dev.
Unpacking libxcomposite-dev (from .../libxcomposite-dev_1%3a0.4.0-1_lpia.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.3-2_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.4-1_lpia.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.9-1_lpia.deb) ...
Selecting previously deselected package x11proto-damage-dev.
Unpacking x11proto-damage-dev (from .../x11proto-damage-dev_1%3a1.1.0-2build1_all.deb) ...
Selecting previously deselected package libxdamage-dev.
Unpacking libxdamage-dev (from .../libxdamage-dev_1%3a1.1.1-3_lpia.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-2build1_lpia.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_2.0.1-0ubuntu1_lpia.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-7ubuntu1_lpia.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.3.5-1ubuntu4.8.04.2_lpia.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.5.0-2ubuntu3_lpia.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-2ubuntu5_lpia.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.3-1_lpia.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.2-1build1_lpia.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-2_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.2.2-1_lpia.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.16.6-0ubuntu1.1netbook1_lpia.deb) ...
Selecting previously deselected package libidl-dev.
Unpacking libidl-dev (from .../libidl-dev_0.8.10-0.1_lpia.deb) ...
Selecting previously deselected package liborbit2-dev.
Unpacking liborbit2-dev (from .../liborbit2-dev_1%3a2.14.12-0.1_lpia.deb) ...
Selecting previously deselected package libpopt-dev.
Unpacking libpopt-dev (from .../libpopt-dev_1.10-3build1_lpia.deb) ...
Selecting previously deselected package libbonobo2-dev.
Unpacking libbonobo2-dev (from .../libbonobo2-dev_2.22.0-0ubuntu1_lpia.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.22.0-0ubuntu1_lpia.deb) ...
Selecting previously deselected package libpixman-1-dev.
Unpacking libpixman-1-dev (from .../libpixman-1-dev_0.10.0-0ubuntu1_lpia.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-3ubuntu0.1_lpia.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.6.0-0ubuntu2_lpia.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.20.5-0ubuntu1.1_lpia.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.12.9-3ubuntu5_lpia.deb) ...
Selecting previously deselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.6.31.dfsg-2ubuntu1.3_lpia.deb) ...
Selecting previously deselected package libglade2-dev.
Unpacking libglade2-dev (from .../libglade2-dev_1%3a2.6.2-1_lpia.deb) ...
Selecting previously deselected package libaudiofile-dev.
Unpacking libaudiofile-dev (from .../libaudiofile-dev_0.2.6-7ubuntu1_lpia.deb) ...
Selecting previously deselected package libesd0-dev.
Unpacking libesd0-dev (from .../libesd0-dev_0.2.40-0ubuntu1~netbook1_lpia.deb) ...
Selecting previously deselected package libgconf2-dev.
Unpacking libgconf2-dev (from .../libgconf2-dev_2.22.0-0ubuntu3_lpia.deb) ...
Selecting previously deselected package libavahi-common-dev.
Unpacking libavahi-common-dev (from .../libavahi-common-dev_0.6.22-2ubuntu4.1netbook0build1_lpia.deb) ...
Selecting previously deselected package libdbus-1-dev.
Unpacking libdbus-1-dev (from .../libdbus-1-dev_1.1.20-1ubuntu3.2netbook0build1_lpia.deb) ...
Selecting previously deselected package libavahi-client-dev.
Unpacking libavahi-client-dev (from .../libavahi-client-dev_0.6.22-2ubuntu4.1netbook0build1_lpia.deb) ...
Selecting previously deselected package libavahi-glib-dev.
Unpacking libavahi-glib-dev (from .../libavahi-glib-dev_0.6.22-2ubuntu4.1netbook0build1_lpia.deb) ...
Selecting previously deselected package libgpg-error-dev.
Unpacking libgpg-error-dev (from .../libgpg-error-dev_1.4-2ubuntu7_lpia.deb) ...
Selecting previously deselected package libgcrypt11-dev.
Unpacking libgcrypt11-dev (from .../libgcrypt11-dev_1.2.4-2ubuntu7_lpia.deb) ...
Selecting previously deselected package libgnutlsxx13.
Unpacking libgnutlsxx13 (from .../libgnutlsxx13_2.0.4-1ubuntu2.3netbook0build1_lpia.deb) ...
Selecting previously deselected package liblzo2-dev.
Unpacking liblzo2-dev (from .../liblzo2-dev_2.02-3_lpia.deb) ...
Selecting previously deselected package libopencdk10-dev.
Unpacking libopencdk10-dev (from .../libopencdk10-dev_0.6.6-1ubuntu1_lpia.deb) ...
Selecting previously deselected package libtasn1-3-dev.
Unpacking libtasn1-3-dev (from .../libtasn1-3-dev_1.1-1_lpia.deb) ...
Selecting previously deselected package libgnutls-dev.
Unpacking libgnutls-dev (from .../libgnutls-dev_2.0.4-1ubuntu2.3netbook0build1_lpia.deb) ...
Selecting previously deselected package libsepol1-dev.
Unpacking libsepol1-dev (from .../libsepol1-dev_2.0.20-0ubuntu3_lpia.deb) ...
Selecting previously deselected package libselinux1-dev.
Unpacking libselinux1-dev (from .../libselinux1-dev_2.0.55-0ubuntu4_lpia.deb) ...
Selecting previously deselected package libgnomevfs2-dev.
Unpacking libgnomevfs2-dev (from .../libgnomevfs2-dev_1%3a2.22.0-2ubuntu1_lpia.deb) ...
Selecting previously deselected package libgnome2-dev.
Unpacking libgnome2-dev (from .../libgnome2-dev_2.22.0-0ubuntu1netbook1_lpia.deb) ...
Selecting previously deselected package libart-2.0-dev.
Unpacking libart-2.0-dev (from .../libart-2.0-dev_2.3.20-1_lpia.deb) ...
Selecting previously deselected package libgail-dev.
Unpacking libgail-dev (from .../libgail-dev_1.22.1-0ubuntu1_lpia.deb) ...
Selecting previously deselected package libgnomecanvas2-dev.
Unpacking libgnomecanvas2-dev (from .../libgnomecanvas2-dev_2.20.1.1-1_lpia.deb) ...
Selecting previously deselected package libbonoboui2-dev.
Unpacking libbonoboui2-dev (from .../libbonoboui2-dev_2.21.90-1_lpia.deb) ...
Selecting previously deselected package libnspr4-dev.
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.5-0ubuntu0.8.04.1_lpia.deb) ...
Selecting previously deselected package libedataserver1.2-dev.
Unpacking libedataserver1.2-dev (from .../libedataserver1.2-dev_2.22.3-0ubuntu3netbook1_lpia.deb) ...
Selecting previously deselected package libcamel1.2-dev.
Unpacking libcamel1.2-dev (from .../libcamel1.2-dev_2.22.3-0ubuntu3netbook1_lpia.deb) ...
Selecting previously deselected package libgnome-keyring-dev.
Unpacking libgnome-keyring-dev (from .../libgnome-keyring-dev_2.22.2-0ubuntu1_lpia.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-14_lpia.deb) ...
Selecting previously deselected package libgnomeui-dev.
Unpacking libgnomeui-dev (from .../libgnomeui-dev_2.22.1.0-0ubuntu2_lpia.deb) ...
Selecting previously deselected package evolution-dev.
Unpacking evolution-dev (from .../evolution-dev_2.22.3.1-0ubuntu1netbook9_lpia.deb) ...
Setting up x11proto-core-dev (7.0.11-1) ...
Setting up libice-dev (2:1.0.4-1) ...
Setting up libsm-dev (2:1.0.3-1) ...
Setting up libxau-dev (1:1.0.3-2) ...
Setting up libpthread-stubs0 (0.1-2) ...
Setting up libpthread-stubs0-dev (0.1-2) ...
Setting up libxdmcp-dev (1:1.0.2-2) ...
Setting up libxcb1-dev (1.1-1ubuntu1) ...
Setting up libxcb-xlib0-dev (1.1-1ubuntu1) ...
Setting up x11proto-input-dev (1.4.2-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.4-1) ...
Setting up libx11-dev (2:1.1.3-1ubuntu2) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up x11proto-fixes-dev (1:4.0-2ubuntu1) ...
Setting up libxfixes-dev (1:4.0.3-2) ...
Setting up x11proto-composite-dev (1:0.4-2) ...
Setting up libxcomposite-dev (1:0.4.0-1) ...
Setting up x11proto-render-dev (2:0.9.3-2) ...
Setting up libxrender-dev (1:0.9.4-1) ...
Setting up libxcursor-dev (1:1.1.9-1) ...
Setting up x11proto-damage-dev (1:1.1.0-2build1) ...
Setting up libxdamage-dev (1:1.1.1-3) ...
Setting up libxext-dev (2:1.0.3-2build1) ...
Setting up libexpat1-dev (2.0.1-0ubuntu1) ...

Setting up zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.2) ...

Setting up libfontconfig1-dev (2.5.0-2ubuntu3) ...

Setting up libxft-dev (2.1.12-2ubuntu5) ...
Setting up libxi-dev (2:1.1.3-1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up libxinerama-dev (2:1.0.2-1build1) ...
Setting up x11proto-randr-dev (1.2.1-2) ...
Setting up libxrandr-dev (2:1.2.2-1) ...
Setting up libglib2.0-dev (2.16.6-0ubuntu1.1netbook1) ...
Setting up libidl-dev (0.8.10-0.1) ...
Setting up liborbit2-dev (1:2.14.12-0.1) ...
Setting up libpopt-dev (1.10-3build1) ...
Setting up libbonobo2-dev (2.22.0-0ubuntu1) ...
Setting up libatk1.0-dev (1.22.0-0ubuntu1) ...
Setting up libpixman-1-dev (0.10.0-0ubuntu1) ...
Setting up libpng12-dev (1.2.15~beta5-3ubuntu0.1) ...
Setting up libcairo2-dev (1.6.0-0ubuntu2) ...
Setting up libpango1.0-dev (1.20.5-0ubuntu1.1) ...
Setting up libgtk2.0-dev (2.12.9-3ubuntu5) ...
Setting up libxml2-dev (2.6.31.dfsg-2ubuntu1.3) ...
Setting up libglade2-dev (1:2.6.2-1) ...

Setting up libaudiofile-dev (0.2.6-7ubuntu1) ...
Setting up libesd0-dev (0.2.40-0ubuntu1~netbook1) ...
Setting up libgconf2-dev (2.22.0-0ubuntu3) ...

Setting up libavahi-common-dev (0.6.22-2ubuntu4.1netbook0build1) ...
Setting up libdbus-1-dev (1.1.20-1ubuntu3.2netbook0build1) ...
Setting up libavahi-client-dev (0.6.22-2ubuntu4.1netbook0build1) ...
Setting up libavahi-glib-dev (0.6.22-2ubuntu4.1netbook0build1) ...
Setting up libgpg-error-dev (1.4-2ubuntu7) ...
Setting up libgcrypt11-dev (1.2.4-2ubuntu7) ...
Setting up libgnutlsxx13 (2.0.4-1ubuntu2.3netbook0build1) ...

Setting up liblzo2-dev (2.02-3) ...
Setting up libopencdk10-dev (0.6.6-1ubuntu1) ...

Setting up libtasn1-3-dev (1.1-1) ...

Setting up libgnutls-dev (2.0.4-1ubuntu2.3netbook0build1) ...
Setting up libsepol1-dev (2.0.20-0ubuntu3) ...
Setting up libselinux1-dev (2.0.55-0ubuntu4) ...
Setting up libgnomevfs2-dev (1:2.22.0-2ubuntu1) ...
Setting up libgnome2-dev (2.22.0-0ubuntu1netbook1) ...
Setting up libart-2.0-dev (2.3.20-1) ...
Setting up libgail-dev (1.22.1-0ubuntu1) ...
Setting up libgnomecanvas2-dev (2.20.1.1-1) ...
Setting up libbonoboui2-dev (2.21.90-1) ...
Setting up libnspr4-dev (4.7.5-0ubuntu0.8.04.1) ...
Setting up libedataserver1.2-dev (2.22.3-0ubuntu3netbook1) ...
Setting up libcamel1.2-dev (2.22.3-0ubuntu3netbook1) ...
Setting up libgnome-keyring-dev (2.22.2-0ubuntu1) ...
Setting up libjpeg62-dev (6b-14) ...
Setting up libgnomeui-dev (2.22.1.0-0ubuntu2) ...
Setting up evolution-dev (2.22.3.1-0ubuntu1netbook9) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
chitra@chitra:~$ cd remove-duplicates-plugin-0.0.4
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for intltool >= 0.29... 0.36.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for ANSI C header files... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for REMOVE_DUPLICATES_PLUGIN... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
chitra@chitra:~/remove-duplicates-plugin-0.0.4$ make install
Making install in src
make[1]: Entering directory `/home/chitra/remove-duplicates-plugin-0.0.4/src'
sed -e 's|\@PLUGINDIR\@|/usr/lib/evolution/2.22/plugins|' org-gnome-remove-duplicates.eplug.in > org-gnome-remove-duplicates.eplug
LC_ALL=C ../intltool-merge -x -u /tmp org-gnome-remove-duplicates.error.xml org-gnome-remove-duplicates.error
Merging translations into org-gnome-remove-duplicates.error.
CREATED org-gnome-remove-duplicates.error
make  install-am
make[2]: Entering directory `/home/chitra/remove-duplicates-plugin-0.0.4/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DORBIT2=1 -pthread -I/usr/include/evolution-2.22 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/evolution-data-server-2.22 -I/usr/include/libxml2 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT remove-duplicates.lo -MD -MP -MF .deps/remove-duplicates.Tpo -c -o remove-duplicates.lo remove-duplicates.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DORBIT2=1 -pthread -I/usr/include/evolution-2.22 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/evolution-data-server-2.22 -I/usr/include/libxml2 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT remove-duplicates.lo -MD -MP -MF .deps/remove-duplicates.Tpo -c remove-duplicates.c  -fPIC -DPIC -o .libs/remove-duplicates.o
 gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DORBIT2=1 -pthread -I/usr/include/evolution-2.22 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/evolution-data-server-2.22 -I/usr/include/libxml2 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT remove-duplicates.lo -MD -MP -MF .deps/remove-duplicates.Tpo -c remove-duplicates.c -o remove-duplicates.o >/dev/null 2>&1
mv -f .deps/remove-duplicates.Tpo .deps/remove-duplicates.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -module -avoid-version  -o liborg-gnome-remove-duplicates.la -rpath /usr/lib/evolution/2.22/plugins remove-duplicates.lo  
gcc -shared  .libs/remove-duplicates.o   -Wl,-soname -Wl,liborg-gnome-remove-duplicates.so -o .libs/liborg-gnome-remove-duplicates.so
ar cru .libs/liborg-gnome-remove-duplicates.a  remove-duplicates.o
ranlib .libs/liborg-gnome-remove-duplicates.a
creating liborg-gnome-remove-duplicates.la
(cd .libs && rm -f liborg-gnome-remove-duplicates.la && ln -s ../liborg-gnome-remove-duplicates.la liborg-gnome-remove-duplicates.la)
make[3]: Entering directory `/home/chitra/remove-duplicates-plugin-0.0.4/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/evolution/2.22/errors" || /bin/mkdir -p "/usr/share/evolution/2.22/errors"
 /usr/bin/install -c -m 644 'org-gnome-remove-duplicates.error' '/usr/share/evolution/2.22/errors/org-gnome-remove-duplicates.error'
/usr/bin/install: cannot create regular file `/usr/share/evolution/2.22/errors/org-gnome-remove-duplicates.error': Permission denied
make[3]: *** [install-errorDATA] Error 1
make[3]: Leaving directory `/home/chitra/remove-duplicates-plugin-0.0.4/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/chitra/remove-duplicates-plugin-0.0.4/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/chitra/remove-duplicates-plugin-0.0.4/src'
make: *** [install-recursive] Error 1
chitra@chitra:~/remove-duplicates-plugin-0.0.4$

---

### Post by chitragurung on 2009-12-17
Finally, I got install remove duplicates plugin in evolution. But I do not know how it work ? I selected some message and click on remove duplicates menu but nothing happen. 

If any body want to install this plug in 

Step 1

install evolution deb file can be found at [http://georgia.ubuntuforums.org/show....php?p=8059339]("http://georgia.ubuntuforums.org/showthread.php?p=8059339")

then

locate your extracted plugin and

do

 ./configure

than 

make install

it install the plugin but I am looking how it work ? May be it may work in your computer.

---

### Post by geoffatmk on 2009-12-18
First, you must make sure you have the right version for your evolution and ubuntu.  As I explained earlier, the plugins folder moves from one version to another and although the plug in installs, it can install the plugin in a directory that evolution does not recognise.

Second, if you go to Edit:Plugins you should see Remove duplicated mails listed.  If not, the version is wrong.  If it is, make sure it is ticked then close and reopen evolution.

Third, highlight a group of mails, right click and you will see a Remove duplicates option.  It takes time, absorbs CPU but works.

Geoff

---

### Post by chitragurung on 2009-12-18
Hello,

I have found that remove duplicates plugin is listed and marked. When I selected some messages and click on remove but no actions found. So, I am not sure whether it worked or not ?

---

### Post by geoffatmk on 2009-12-18
Find two EXACT duplicate emails.  Same text, subject, date, time etc.

Highlight them both.

Righ click and remove duplicates.  See if one disappears.

You might find it easier to insert a new folder copy an email to it twice then do the test so you can easily see the results.

---

### Post by chitragurung on 2009-12-18
Really, it does not work. I did what you mentioned in the post. But it does not work. I do not which one should download from GNOME site. I mean which remove duplicate is suitable for my PC. I found there are 4 options in GNOME site I downloaded last one.

---

### Post by toobaz on 2009-12-18
If someone needs the package for some other Ubuntu version, I can prepare it and upload it, no problem. But I noticed the plugin doesn't work an all duplicates. It may remove some, but to remove them all I had to follow the procedure found at 
[http://www.len.ro/2009/01/remove-duplicate-mails/](http://www.len.ro/2009/01/remove-duplicate-mails/)

**please remember to backup** the folder you're running it on

Pietro

---

### Post by chitragurung on 2009-12-22
Still does not solved the problem

---

### Post by toobaz on 2009-12-23
> **chitragurung said:**
> Still does not solved the problem

If you want someone to help you, you should probably say exactly what you did and what (doesn't) happens.

---

### Post by toobaz on 2009-12-23
Oh, I forgot to mention: I did create packages also for intrepid, jaunty and lucid, but unfortunately not for hardy, since a dependency (debhelper 7) is missing.

---

### Post by chitragurung on 2009-12-23
I want to remove duplicate emails from Evolution. I install a plug in call remove duplicates plug in from GNOME. It is installed successfully. But it does not work what it supposed to be.

---

### Post by toobaz on 2009-12-24
> **chitragurung said:**
> I want to remove duplicate emails from Evolution. I install a plug in call remove duplicates plug in from GNOME. It is installed successfully. But it does not work what it supposed to be.


See [comment 23]("http://ubuntuforums.org/showpost.php?p=8520626&postcount=23").

---

### Post by chitragurung on 2009-12-25
> **chitragurung said:**
> Finally, I got install remove duplicates plugin in evolution. But I do not know how it work ? I selected some message and click on remove duplicates menu but nothing happen. 

If any body want to install this plug in 

Step 1

install evolution deb file can be found at [http://georgia.ubuntuforums.org/show....php?p=8059339]("http://georgia.ubuntuforums.org/showthread.php?p=8059339")

then

locate your extracted plugin and

do

 ./configure

than 

make install

it install the plugin but I am looking how it work ? May be it may work in your computer.

Finally, it worked though above procedure and now I can remove my duplicates.

---

### Post by toobaz on 2010-09-07
Since I've been asked privately, I write here an update: unfortunately, the current code of the plugin doesn't build against the last version of evolution (2.30, present in Ubuntu Lucid).

As a consequence (or, strictly speaking, as a consequence of my scarce experience with C and in particular of my lack of time to deal with Evolution code) I'm unable to produce new packages of the plugin.

I wrote to Carlos, the author of the plugin, in July asking if he plans to release an updated version, but I still had no reply.

Pietro

---

### Post by toobaz on 2010-09-07
> **toobaz said:**
> Since I've been asked privately, I write here an update: unfortunately, the current code of the plugin doesn't build against the last version of evolution

In case someone is curious, this is the error in compilation:

```

make[1]: Entering directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb'
make  all-recursive
make[2]: Entering directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb'
Making all in src
make[3]: Entering directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb/src'
sed -e 's|\@PLUGINDIR\@|/usr/lib/evolution/2.30/plugins|'
org-gnome-remove-duplicates.eplug.in > org-gnome-remove-duplicates.eplug
LC_ALL=C ../intltool-merge -x -u /tmp
org-gnome-remove-duplicates.error.xml org-gnome-remove-duplicates.error
Merging translations into org-gnome-remove-duplicates.error.
CREATED org-gnome-remove-duplicates.error
make  all-am
make[4]: Entering directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.
-I.. -I.. -DORBIT2=1 -pthread -I/usr/include/evolution-2.30
-I/usr/include/evolution-data-server-2.30 -I/usr/include/libxml2
-I/usr/include/unique-1.0 -I/usr/include/libgtkhtml-3.14
-I/usr/include/libgtkhtml-3.14/editor -I/usr/include/libgnomecanvas-2.0
-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/nss
-I/usr/include/nspr -I/usr/include/gconf/2 -I/usr/include/libsoup-2.4
-I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0
-I/usr/lib/dbus-1.0/include -I/usr/include/gtk-2.0
-I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo
-I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/
-I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12
-I/usr/include/enchant -I/usr/include/gail-1.0 -I/usr/include/libart-2.0
-g -O2 -c -o remove-duplicates.lo remove-duplicates.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DORBIT2=1 -pthread
-I/usr/include/evolution-2.30 -I/usr/include/evolution-data-server-2.30
-I/usr/include/libxml2 -I/usr/include/unique-1.0
-I/usr/include/libgtkhtml-3.14 -I/usr/include/libgtkhtml-3.14/editor
-I/usr/include/libgnomecanvas-2.0 -I/usr/include/glib-2.0
-I/usr/lib/glib-2.0/include -I/usr/include/nss -I/usr/include/nspr
-I/usr/include/gconf/2 -I/usr/include/libsoup-2.4
-I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0
-I/usr/lib/dbus-1.0/include -I/usr/include/gtk-2.0
-I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo
-I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/
-I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12
-I/usr/include/enchant -I/usr/include/gail-1.0 -I/usr/include/libart-2.0
-g -O2 -c remove-duplicates.c  -fPIC -DPIC -o .libs/remove-duplicates.o
remove-duplicates.c:23:27: error: mail/em-popup.h: No such file or
directory
remove-duplicates.c:25:28: error: e-util/e-error.h: No such file or
directory
remove-duplicates.c:159: error: expected ')' before '*' token
remove-duplicates.c:162: error: expected ')' before '*' token
make[4]: *** [remove-duplicates.lo] Error 1
make[4]: Leaving directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb/src'
make[3]: *** [all] Error 2
make[3]: Leaving directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb'
make[1]: *** [all] Error 2
make[1]: Leaving directory
`/home/nobackup/Software/evolution/remove-duplicates-plugin_deb'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
```

---

### Post by pmorton on 2010-12-13
Working with Evolution  2.80 on Ubutu 10.04.

Get tarball from [http://people.gnome.org/~carlosg/stuff/evolution/](http://people.gnome.org/~carlosg/stuff/evolution/)

Install evolution-dev:

sudo apt-get install evolution-dev

Go into extract directory say ~/Downloads/remove-duplicates-plugin-0.0.4 and:

./configure
sudo make install

In Evolution do 'Ctrl-A' to select all files in a folder; right click and select the menu entry 'Remove Duplicates'

The capers involved in getting a remove duplicate function in Evolution has been going on for years. It's the single biggest drawback to using Evolution rather than Thunderbird (although Thunderbird seem to be on its last legs as a development project. You wonder if no-one has told Red Hat what a drag it is not having this as a built-in.

---

### Post by apoapo on 2010-12-13
Im using 2.30.3 evolution. The option is not available anymore.


Will it comeback then? :(

---

### Post by toobaz on 2010-12-14
> **pmorton said:**
> Working with Evolution  2.80 on Ubutu 10.04.


It is Evolution 2.28

> **pmorton said:**
> 

Get tarball from [http://people.gnome.org/~carlosg/stuff/evolution/](http://people.gnome.org/~carlosg/stuff/evolution/)
Install evolution-dev:

sudo apt-get install evolution-dev

Go into extract directory say ~/Downloads/remove-duplicates-plugin-0.0.4 and:

./configure
sudo make install

In Evolution do 'Ctrl-A' to select all files in a folder; right click and select the menu entry 'Remove Duplicates'

The capers involved in getting a remove duplicate function in Evolution has been going on for years. It's the single biggest drawback to using Evolution rather than Thunderbird (although Thunderbird seem to be on its last legs as a development project. You wonder if no-one has told Red Hat what a drag it is not having this as a built-in.

Or: install the package from my PPA:
[https://launchpad.net/~toobaz/+archive/toobaz/](https://launchpad.net/~toobaz/+archive/toobaz/)

(package which, just to be clear again, is **not** available for Maverick and **won't** be as long as the plugin code isn't updated for Evolution 2.30 - and I'm not expert in evolution internals, so I'm not able to do that).

bye

Pietro

---

### Post by malapradej on 2011-08-03
> **toobaz said:**
> It is Evolution 2.28



Or: install the package from my PPA:
[https://launchpad.net/~toobaz/+archive/toobaz/]("https://launchpad.net/%7Etoobaz/+archive/toobaz/")

(package which, just to be clear again, is **not** available for Maverick and **won't** be as long as the plugin code isn't updated for Evolution 2.30 - and I'm not expert in evolution internals, so I'm not able to do that).

bye

Pietro

For those who have a bit of python experience this would be a piece of pie. For those that don't I'll try and give the steps. But please don't blame me if this doesn't work. It works on my Ubuntu Natty with evolution v2.32.2.

See the link:

[http://www.len.ro/2009/01/remove-duplicate-mails/](http://www.len.ro/2009/01/remove-duplicate-mails/)

I have changed the folders slightly to fit with newer version of evolution. Saves mail in different folders.

What I did:

Close evolution.

Install the python3.2 idle through Ubuntu software centre or in the terminal: sudo apt-get -i idle-python3.2

backup your ~/.local/share/evolution/mail/local/Inbox.ok file and also the ~/.evolution/mail/local/Inbox file.

open the python3.2 idle : Applications > Programming > Idle...3.2

Choose File > New Window. Copy the text starting with[SIZE=2] 
[/SIZE][SIZE=2][COLOR=Blue]#!/usr/bin/env python [/COLOR][/SIZE]and ending with [COLOR=Blue]marshall.dump[/COLOR] into the new window(see link above), save the file in your home folder as cleanupmbox.py.

Open a terminal and enter the following: (need to be in home folder)

python cleanupmbox.py -i ~/.local/share/evolution/mail/local/Inbox  -o ~/.evolution/mail/local/Inbox.ok -h inbox.h

Let me know if it works.

Good luck.

---

### Post by Šašek on 2011-08-21
Hi malapradej,
everything worked, but had no result. I end up having an empty inbox.ok file (0 byte), and the duplicates remain.

what did Len mean in the post you refer to, when he says "Of course evolution has to be stopped and then the Inbox.ok copied onto the Inbox file." ? I did close evo as you wrote it, too, but what to do after letting work the command line you finish your description with?

Thaaaaanx!
Šašek

---

