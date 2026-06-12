---
title: "Installing package"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by spacerocket on 2014-04-07
Hello!

I tried to compile C program from source, and this is the message I get:

configure: error: Package requirements ( cairo >= 1.2.0 librsvg-2.0 >= 2.14.0 ) were not met:

No package 'cairo' found
No package 'librsvg-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CAIRO_CFLAGS
and CAIRO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Now I want to install **librsvg-2.0** and went to terminal window:

 **apt-get update**
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[B]
apt-get install librsvg2-bin[/B]
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What should I do?

---

### Post by 23dornot23d on 2014-04-07
Just put **sudo** infront - you are trying to run the command as normal user 


**sudo** [B]apt-get update

sudo [/B][B][B]apt-get install librsvg2-bin


[/B][/B]You are probably better off not compiling things from source - if there is a better alternative ........

what is it you are compiling[B] ?
[/B]

---

### Post by spacerocket on 2014-04-08
XBoard. 

Now after


**sudo** [B]apt-get update

sudo [/B][B][B]apt-get install librsvg2-bin                          
[/B][/B]
when I "cd" to the correct directory(XB) and type ./configure

configure: error: Package requirements ( cairo >= 1.2.0 librsvg-2.0 >= 2.14.0 ) were not met:

No package 'cairo' found
No package 'librsvg-2.0' found

I found this: [http://cairographics.org/download/](http://cairographics.org/download/)  and [http://askubuntu.com/questions/108662/how-to-install-cairo-1-8-10](http://askubuntu.com/questions/108662/how-to-install-cairo-1-8-10)     I tried 
sudo apt-get build-dep cairo

This just makes sure that cairos build depencies are installed? How can I download and unpack the newest version of cairo/[B][B] librsvg2-bin

   
[/B][/B][URL="http://cairographics.org/releases/"]http://cairographics.org/releases/

Then maybe  
export PKG_CONFIG_PATH=$HOME/prefix/lib/pkgconfig[/URL]

---

### Post by steeldriver on 2014-04-08
You shouldn't need the build-deps **for** cairo (you are not trying to build cairo)

Probably what's missing are the development libraries and headers **of** cairo (and librsvg-2.0)

```
sudo apt-get install libcairo2**-dev** librsvg2**-dev**
```

---

### Post by spacerocket on 2014-04-08
Now worked. Thanks. Then there is another issue:

checking for IceConnectionNumber in -lICE... yes
checking X11/Intrinsic.h usability... yes
checking X11/Intrinsic.h presence... yes
checking for X11/Intrinsic.h... yes
checking X11/Xaw/Dialog.h usability... no
checking X11/Xaw/Dialog.h presence... no
checking for X11/Xaw/Dialog.h... no
configure: error: Xaw headers not found. Please install the Xaw package and headers.

---

### Post by steeldriver on 2014-04-08
You should probably just install the **xorg-dev** metapackage - that should pull in the appropriate libxaw development library plus related X headers + libs

Unless your system is severely short of disk space that's often easier than chasing down each prerequisite package individually

---

### Post by spacerocket on 2014-04-08
Maybe with this command: 

sudo apt-get install texi2html texinfo xserver-xorg-dev libxt-dev xaw3dg xaw3dg-dev libxaw7 libxaw7-dev fairymax

---

### Post by spacerocket on 2014-04-08
Now I typed this and then make:

sudo apt-get install texi2html texinfo xserver-xorg-dev libxt-dev xaw3dg xaw3dg-dev libxaw7 libxaw7-dev fairymax 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxaw7 is already the newest version.
libxt-dev is already the newest version.
texinfo is already the newest version.
The following extra packages will be installed:
  libdrm-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libkms1
  libmirclient-dev libmirclient3 libmirprotobuf-dev libmirprotobuf0
  libpciaccess-dev libprotobuf-dev libprotobuf-lite7 libxkbfile-dev libxmu-dev
  libxmu-headers libxpm-dev mesa-common-dev mircommon-dev x11proto-dri2-dev
  x11proto-fonts-dev x11proto-gl-dev x11proto-randr-dev x11proto-resource-dev
  x11proto-scrnsaver-dev x11proto-video-dev x11proto-xf86dri-dev
  x11proto-xinerama-dev
Suggested packages:
  libxaw-doc latex2html
The following NEW packages will be installed:
  fairymax libdrm-dev libkms1 libmirclient-dev libmirclient3
  libmirprotobuf-dev libmirprotobuf0 libpciaccess-dev libprotobuf-dev
  libprotobuf-lite7 libxaw7-dev libxkbfile-dev libxmu-dev libxmu-headers
  libxpm-dev mesa-common-dev mircommon-dev texi2html x11proto-dri2-dev
  x11proto-fonts-dev x11proto-gl-dev x11proto-randr-dev x11proto-resource-dev
  x11proto-scrnsaver-dev x11proto-video-dev x11proto-xf86dri-dev
  x11proto-xinerama-dev xaw3dg xaw3dg-dev xserver-xorg-dev
The following packages will be upgraded:
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2
4 upgraded, 30 newly installed, 0 to remove and 255 not upgraded.
Need to get 3 532 kB of archives.
After this operation, 15,3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main libdrm2 amd64 2.4.46-1ubuntu1 [26,7 kB]
Get:2 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main libdrm-intel1 amd64 2.4.46-1ubuntu1 [63,0 kB]
Get:3 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main libdrm-nouveau2 amd64 2.4.46-1ubuntu1 [15,1 kB]
Get:4 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main libdrm-radeon1 amd64 2.4.46-1ubuntu1 [26,3 kB]
Get:5 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main libkms1 amd64 2.4.46-1ubuntu1 [9 258 B]
Get:6 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libmirprotobuf0 amd64 0.0.15+13.10.20131014-0ubuntu1 [77,3 kB]
Get:7 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libmirclient3 amd64 0.0.15+13.10.20131014-0ubuntu1 [171 kB]
Get:8 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main xaw3dg amd64 1.5+E-18.2 [174 kB]
Get:9 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main libdrm-dev amd64 2.4.46-1ubuntu1 [214 kB]
Get:10 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libprotobuf-lite7 amd64 2.4.1-3ubuntu2 [61,9 kB]
Get:11 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libprotobuf-dev amd64 2.4.1-3ubuntu2 [623 kB]
Get:12 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libmirprotobuf-dev amd64 0.0.15+13.10.20131014-0ubuntu1 [4 602 B]
Get:13 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main mircommon-dev amd64 0.0.15+13.10.20131014-0ubuntu1 [20,0 kB]
Get:14 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libmirclient-dev amd64 0.0.15+13.10.20131014-0ubuntu1 [7 462 B]
Get:15 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libxmu-headers all 2:1.1.1-1 [62,0 kB]
Get:16 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libxmu-dev amd64 2:1.1.1-1 [60,3 kB]
Get:17 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libxpm-dev amd64 1:3.5.10-1 [94,2 kB]
Get:18 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libxaw7-dev amd64 2:1.0.11-1 [298 kB]
Get:19 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libxkbfile-dev amd64 1:1.0.8-1 [89,4 kB]
Get:20 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main mesa-common-dev amd64 9.2.1-1ubuntu3 [249 kB]
Get:21 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main texi2html all 1.82+dfsg1-3 [403 kB]
Get:22 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-dri2-dev all 2.8-2 [12,6 kB]
Get:23 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-fonts-dev all 2.1.2-1 [69,7 kB]
Get:24 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-gl-dev all 1.4.16-2 [22,0 kB]
Get:25 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-randr-dev all 1.4.0+git20120101.is.really.1.4.0-0ubuntu1 [32,9 kB]
Get:26 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-resource-dev all 1.2.0-3 [10,7 kB]
Get:27 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-scrnsaver-dev all 1.2.2-1 [25,0 kB]
Get:28 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-video-dev all 2.3.1-2 [17,0 kB]
Get:29 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-xf86dri-dev all 2.1.1-2 [5 630 B]
Get:30 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main x11proto-xinerama-dev all 1.2.1-2 [4 966 B]
Get:31 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main xaw3dg-dev amd64 1.5+E-18.2 [248 kB]
Get:32 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/main libpciaccess-dev amd64 0.13.2-1 [23,6 kB]
Get:33 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy-updates/main xserver-xorg-dev amd64 2:1.14.5-1ubuntu2~saucy1 [272 kB]
Get:34 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/universe fairymax amd64 4.8q-2 [39,3 kB]
Fetched 3 532 kB in 8s (441 kB/s)                                              
Extracting templates from packages: 100%
(Reading database ... 199333 files and directories currently installed.)
Preparing to replace libdrm2:amd64 2.4.46-1 (using .../libdrm2_2.4.46-1ubuntu1_amd64.deb) ...
Unpacking replacement libdrm2:amd64 ...
Preparing to replace libdrm-intel1:amd64 2.4.46-1 (using .../libdrm-intel1_2.4.46-1ubuntu1_amd64.deb) ...
Unpacking replacement libdrm-intel1:amd64 ...
Preparing to replace libdrm-nouveau2:amd64 2.4.46-1 (using .../libdrm-nouveau2_2.4.46-1ubuntu1_amd64.deb) ...
Unpacking replacement libdrm-nouveau2:amd64 ...
Preparing to replace libdrm-radeon1:amd64 2.4.46-1 (using .../libdrm-radeon1_2.4.46-1ubuntu1_amd64.deb) ...
Unpacking replacement libdrm-radeon1:amd64 ...
Selecting previously unselected package libkms1:amd64.
Unpacking libkms1:amd64 (from .../libkms1_2.4.46-1ubuntu1_amd64.deb) ...
Selecting previously unselected package libmirprotobuf0:amd64.
Unpacking libmirprotobuf0:amd64 (from .../libmirprotobuf0_0.0.15+13.10.20131014-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libmirclient3:amd64.
Unpacking libmirclient3:amd64 (from .../libmirclient3_0.0.15+13.10.20131014-0ubuntu1_amd64.deb) ...
Selecting previously unselected package xaw3dg:amd64.
Unpacking xaw3dg:amd64 (from .../xaw3dg_1.5+E-18.2_amd64.deb) ...
Selecting previously unselected package libdrm-dev:amd64.
Unpacking libdrm-dev:amd64 (from .../libdrm-dev_2.4.46-1ubuntu1_amd64.deb) ...
Selecting previously unselected package libprotobuf-lite7.
Unpacking libprotobuf-lite7 (from .../libprotobuf-lite7_2.4.1-3ubuntu2_amd64.deb) ...
Selecting previously unselected package libprotobuf-dev.
Unpacking libprotobuf-dev (from .../libprotobuf-dev_2.4.1-3ubuntu2_amd64.deb) ...
Selecting previously unselected package libmirprotobuf-dev:amd64.
Unpacking libmirprotobuf-dev:amd64 (from .../libmirprotobuf-dev_0.0.15+13.10.20131014-0ubuntu1_amd64.deb) ...
Selecting previously unselected package mircommon-dev:amd64.
Unpacking mircommon-dev:amd64 (from .../mircommon-dev_0.0.15+13.10.20131014-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libmirclient-dev:amd64.
Unpacking libmirclient-dev:amd64 (from .../libmirclient-dev_0.0.15+13.10.20131014-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libxmu-headers.
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.1.1-1_all.deb) ...
Selecting previously unselected package libxmu-dev:amd64.
Unpacking libxmu-dev:amd64 (from .../libxmu-dev_2%3a1.1.1-1_amd64.deb) ...
Selecting previously unselected package libxpm-dev:amd64.
Unpacking libxpm-dev:amd64 (from .../libxpm-dev_1%3a3.5.10-1_amd64.deb) ...
Selecting previously unselected package libxaw7-dev:amd64.
Unpacking libxaw7-dev:amd64 (from .../libxaw7-dev_2%3a1.0.11-1_amd64.deb) ...
Selecting previously unselected package libxkbfile-dev:amd64.
Unpacking libxkbfile-dev:amd64 (from .../libxkbfile-dev_1%3a1.0.8-1_amd64.deb) ...
Selecting previously unselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_9.2.1-1ubuntu3_amd64.deb) ...
Selecting previously unselected package texi2html.
Unpacking texi2html (from .../texi2html_1.82+dfsg1-3_all.deb) ...
Selecting previously unselected package x11proto-dri2-dev.
Unpacking x11proto-dri2-dev (from .../x11proto-dri2-dev_2.8-2_all.deb) ...
Selecting previously unselected package x11proto-fonts-dev.
Unpacking x11proto-fonts-dev (from .../x11proto-fonts-dev_2.1.2-1_all.deb) ...
Selecting previously unselected package x11proto-gl-dev.
Unpacking x11proto-gl-dev (from .../x11proto-gl-dev_1.4.16-2_all.deb) ...
Selecting previously unselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.4.0+git20120101.is.really.1.4.0-0ubuntu1_all.deb) ...
Selecting previously unselected package x11proto-resource-dev.
Unpacking x11proto-resource-dev (from .../x11proto-resource-dev_1.2.0-3_all.deb) ...
Selecting previously unselected package x11proto-scrnsaver-dev.
Unpacking x11proto-scrnsaver-dev (from .../x11proto-scrnsaver-dev_1.2.2-1_all.deb) ...
Selecting previously unselected package x11proto-video-dev.
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.3.1-2_all.deb) ...
Selecting previously unselected package x11proto-xf86dri-dev.
Unpacking x11proto-xf86dri-dev (from .../x11proto-xf86dri-dev_2.1.1-2_all.deb) ...
Selecting previously unselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.2.1-2_all.deb) ...
Selecting previously unselected package xaw3dg-dev:amd64.
Unpacking xaw3dg-dev:amd64 (from .../xaw3dg-dev_1.5+E-18.2_amd64.deb) ...
Selecting previously unselected package libpciaccess-dev:amd64.
Unpacking libpciaccess-dev:amd64 (from .../libpciaccess-dev_0.13.2-1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-dev.
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.14.5-1ubuntu2~saucy1_amd64.deb) ...
Selecting previously unselected package fairymax.
Unpacking fairymax (from .../fairymax_4.8q-2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Processing triggers for install-info ...
Setting up libdrm2:amd64 (2.4.46-1ubuntu1) ...
Setting up libdrm-intel1:amd64 (2.4.46-1ubuntu1) ...
Setting up libdrm-nouveau2:amd64 (2.4.46-1ubuntu1) ...
Setting up libdrm-radeon1:amd64 (2.4.46-1ubuntu1) ...
Setting up libkms1:amd64 (2.4.46-1ubuntu1) ...
Setting up libmirprotobuf0:amd64 (0.0.15+13.10.20131014-0ubuntu1) ...
Setting up libmirclient3:amd64 (0.0.15+13.10.20131014-0ubuntu1) ...
Setting up xaw3dg:amd64 (1.5+E-18.2) ...
Setting up libdrm-dev:amd64 (2.4.46-1ubuntu1) ...
Setting up libprotobuf-lite7 (2.4.1-3ubuntu2) ...
Setting up libprotobuf-dev (2.4.1-3ubuntu2) ...
Setting up libmirprotobuf-dev:amd64 (0.0.15+13.10.20131014-0ubuntu1) ...
Setting up mircommon-dev:amd64 (0.0.15+13.10.20131014-0ubuntu1) ...
Setting up libmirclient-dev:amd64 (0.0.15+13.10.20131014-0ubuntu1) ...
Setting up libxmu-headers (2:1.1.1-1) ...
Setting up libxmu-dev:amd64 (2:1.1.1-1) ...
Setting up libxpm-dev:amd64 (1:3.5.10-1) ...
Setting up libxaw7-dev:amd64 (2:1.0.11-1) ...
Setting up libxkbfile-dev:amd64 (1:1.0.8-1) ...
Setting up mesa-common-dev (9.2.1-1ubuntu3) ...
Setting up texi2html (1.82+dfsg1-3) ...
Setting up x11proto-dri2-dev (2.8-2) ...
Setting up x11proto-fonts-dev (2.1.2-1) ...
Setting up x11proto-gl-dev (1.4.16-2) ...
Setting up x11proto-randr-dev (1.4.0+git20120101.is.really.1.4.0-0ubuntu1) ...
Setting up x11proto-resource-dev (1.2.0-3) ...
Setting up x11proto-scrnsaver-dev (1.2.2-1) ...
Setting up x11proto-video-dev (2.3.1-2) ...
Setting up x11proto-xf86dri-dev (2.1.1-2) ...
Setting up x11proto-xinerama-dev (1.2.1-2) ...
Setting up xaw3dg-dev:amd64 (1.5+E-18.2) ...
Setting up libpciaccess-dev:amd64 (0.13.2-1) ...
Setting up xserver-xorg-dev (2:1.14.5-1ubuntu2~saucy1) ...
Setting up fairymax (4.8q-2) ...
Processing triggers for libc-bin ...
user@user-MS-7817:~$ Downloads/xboard-4.7.3/configure/./
bash: Downloads/xboard-4.7.3/configure/./: Not a directory
kimon@kimon-MS-7817:~$ Downloads/xboard-4.7.3/./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for library containing strerror... none required
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for remsh... no
checking for rsh... rsh
checking for makeinfo... makeinfo
checking for nroff... nroff -man
checking for awk... /usr/bin/awk
checking for perl... /usr/bin/perl
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking return type of signal handlers... void
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking stropts.h usability... yes
checking stropts.h presence... yes
checking for stropts.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/systeminfo.h usability... no
checking sys/systeminfo.h presence... no
checking for sys/systeminfo.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for _getpty... no
checking for grantpt... yes
checking for setitimer... yes
checking for usleep... yes
checking for gettimeofday... yes
checking for random... yes
checking for gethostname... yes
checking for setlocale... yes
checking for getpseudotty in -lseq... no
checking whether compiler understands -Wall -Wno-parentheses... yes
checking for pkg-config... pkg-config
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for CAIRO... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking X11/Intrinsic.h usability... yes
checking X11/Intrinsic.h presence... yes
checking for X11/Intrinsic.h... yes
checking X11/Xaw/Dialog.h usability... yes
checking X11/Xaw/Dialog.h presence... yes
checking for X11/Xaw/Dialog.h... yes
checking X11/xpm.h usability... yes
checking X11/xpm.h presence... yes
checking for X11/xpm.h... yes
checking for XpmReadFileToPixmap in -lXpm... yes
checking whether ptys or pipes should be used... pipes
checking for xdg-mime... /usr/bin/xdg-mime
checking for xdg-desktop-menu... /usr/bin/xdg-desktop-menu
checking for xdg-icon-resource... /usr/bin/xdg-icon-resource
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating cmail
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing test-stamp-h commands
config.status: executing chmod-cmail commands

 Configurations summary:

        prefix:          /usr/local       
        datarootdir:     ${prefix}/share  
        datadir:         ${datarootdir}   (icons will go in $datadir/icons/hicolor/...)
                                    (bitmaps will go in $datadir/games/xboard/...)
        infodir:         ${datarootdir}/info   (info files will go here)
        sysconfdir:      ${prefix}/etc   (xboard.conf will go here)

        update mimedb:   yes

        NLS support:     yes

        GTK:             no
        Xaw3d:           no
        Xaw:             yes

        xpm:             yes
        ptys:            pipes
        zippy:           no
        sigint:          yes
user@user-MS-7817:~$ make
make  all-recursive
make[1]: Entering directory `/home/user'
Making all in po
make[2]: Entering directory `/home/user/po'
make[2]: Leaving directory `/home/user/po'
make[2]: Entering directory `/home/user'
  CC       backend.o
Downloads/xboard-4.7.3/./backend.c: In function &#8216;read_from_ics&#8217;:
Downloads/xboard-4.7.3/./backend.c:3905:21: warning: variable &#8216;blackname&#8217; set but not used [-Wunused-but-set-variable]
   char *whitename, *blackname, *why, *endtoken;
                     ^
Downloads/xboard-4.7.3/./backend.c:3905:9: warning: variable &#8216;whitename&#8217; set but not used [-Wunused-but-set-variable]
   char *whitename, *blackname, *why, *endtoken;
         ^
  CC       book.o
  CC       childio.o
  CC       gamelist.o
  CC       ngamelist.o
  CC       lists.o
  CC       moves.o
  CC       parser.o
  CC       pgntags.o
  CC       uci.o
  CC       board.o
  CC       draw.o
In file included from Downloads/xboard-4.7.3/./draw.c:59:0:
/usr/include/librsvg-2.0/librsvg/rsvg-cairo.h:27:2: warning: #warning "Including <librsvg/rsvg-cairo.h> directly is deprecated." [-Wcpp]
 #warning "Including <librsvg/rsvg-cairo.h> directly is deprecated."
  ^
Downloads/xboard-4.7.3/./draw.c: In function &#8216;ScaleOnePiece&#8217;:
Downloads/xboard-4.7.3/./draw.c:276:3: warning: &#8216;g_type_init&#8217; is deprecated (declared at /usr/include/glib-2.0/gobject/gtype.h:669) [-Wdeprecated-declarations]
   g_type_init ();
   ^
  CC       dialogs.o
  CC       engineoutput.o
  CC       nengineoutput.o
  CC       evalgraph.o
  CC       nevalgraph.o
  CC       history.o
  CC       nhistory.o
  CC       menus.o
  CC       usounds.o
  CC       usystem.o
  CC       xaw/xboard.o
  CC       xaw/xengineoutput.o
  CC       xaw/xgamelist.o
  CC       xaw/xhistory.o
  CC       xaw/xoptions.o
  CCLD     xboard
  GEN    xboard.conf
make[2]: Leaving directory `/home/user
make[1]: Leaving directory `/home/user

Is xboard now compiled and ready? Where can I find it?

---

### Post by 23dornot23d on 2014-04-08
You have done the first part ....... is there a readme in the folder you downloaded .......

They usually explain in detail how to set things up ....... 

usually configure make then sudo make install 

```

You also need code wrappers around all that text to save people having to scroll right through it
all to get to here ....

code ..... text ..... /code 

both start and end commands - in square brackets [] ........


```
But I have no idea what you are trying to do here ...... and you could be breaking your own system
or causing it problems in the future ......

---

### Post by spacerocket on 2014-04-08
xboard -fcp -ics -icshost chessclub.com
The program 'xboard' is currently not installed. You can install it by typing:
sudo apt-get install xboard
user@user-MS-7817:~$ sudo apt-get install xboard
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xfonts-100dpi
The following NEW packages will be installed:
  xboard xfonts-100dpi
0 upgraded, 2 newly installed, 0 to remove and 255 not upgraded.
Need to get 4 935 kB of archives.
After this operation, 7 563 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/universe xboard amd64 4.7.1-1 [1 027 kB]
Get:2 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) saucy/universe xfonts-100dpi all 1:1.0.3 [3 908 kB]
Fetched 4 935 kB in 7s (661 kB/s)                                              
Selecting previously unselected package xboard.
(Reading database ... 200265 files and directories currently installed.)
Unpacking xboard (from .../xboard_4.7.1-1_amd64.deb) ...
Selecting previously unselected package xfonts-100dpi.
Unpacking xfonts-100dpi (from .../xfonts-100dpi_1%3a1.0.3_all.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Processing triggers for install-info ...
Processing triggers for fontconfig ...
Setting up xboard (4.7.1-1) ...
Setting up xfonts-100dpi (1:1.0.3) ...

Now I have build the program from source? (xboard-4.7.3)

---

### Post by steeldriver on 2014-04-08
I don't know what xboard is either :)

However the convention for these things is that **make **just builds everything in your local directory, and there is usually an additional **make install** step to copy the relevant files into the appropriate system directories (this will need root permissions i.e. **sudo make install**)

You may want to look in the README or INSTALL file for specific instructions - there may also be some tests that you can run locally before committing to the install.

You may want to look at the **checkinstall **program which intercepts the installer and keeps everything under the control of the package management system (if you did ./configure **--prefix=/usr/local** it's not so quite so important though)

---

### Post by 23dornot23d on 2014-04-08
ah ninja'd ..... ;) ( as above )

Nope .... you have done a proper install from the repos ..... which is better .......

But I can now see what you were trying to do ........

( when compiling things - they need running from where the binary file was placed ........ )

But you never got that far ....... which is probably safest ........

But at least you have a version installed now ....... Setting up xboard (4.7.1-1) ...

___________________________________________________

Does that version now work and is it what you wanted ?

---

### Post by spacerocket on 2014-04-08
Yes but I have gone wrong! I still want to install that 4.7.3 from source and made configure and make successfully. How can I uninstall xboard 4.7.1-1?

and more importantly how can I continue running 4.7.3 from source

---

### Post by spacerocket on 2014-04-08
Now I continued to read the xboard documentation which says "**make install**":

make install
Making install in po
make[1]: Entering directory `/home/user/po'
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/da/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/da.gmo as /usr/local/share/locale/da/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/de/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/de.gmo as /usr/local/share/locale/de/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/es/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/es.gmo as /usr/local/share/locale/es/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/it/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/it.gmo as /usr/local/share/locale/it/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/ru/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/tr/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/tr.gmo as /usr/local/share/locale/tr/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/uk/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/vi/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/zh_CN/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/zh_HK/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/zh_HK.gmo as /usr/local/share/locale/zh_HK/LC_MESSAGES/xboard.mo
/bin/mkdir: cannot create directory &#8216;/usr/local/share/locale&#8217;: Permission denied
/usr/bin/install: cannot create regular file &#8216;/usr/local/share/locale/zh_TW/LC_MESSAGES/xboard.mo&#8217;: No such file or directory
installing ../Downloads/xboard-4.7.3/./po/zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/xboard.mo
if test "xboard" = "gettext-tools"; then \
      /bin/mkdir -p /usr/local/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ../Downloads/xboard-4.7.3/./po/$file \
                /usr/local/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/local/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/home/user/po'
make[1]: Entering directory `/home/user'
make[2]: Entering directory `/home/user'
 /bin/mkdir -p '/usr/local/bin'
  /usr/bin/install -c xboard '/usr/local/bin'
/usr/bin/install: cannot create regular file &#8216;/usr/local/bin/xboard&#8217;: Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/user'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/user'
make: *** [install-recursive] Error 1

---

### Post by spacerocket on 2014-04-08
OK. Now I have xboard 4.7.3 so are you 100% sure I have compiled it from source?

Thanks

---

### Post by 23dornot23d on 2014-04-08
You have to remove the previous version doing

**sudo apt-get remove xboard**

Before you can go any further .........

Note that you got permission denied here for a reason

> 
/bin/mkdir -p '/usr/local/bin'
  /usr/bin/install -c xboard '/usr/local/bin'
[COLOR=#ff0000]**/usr/bin/install: cannot create regular file &#8216;/usr/local/bin/xboard&#8217;: Permission denied**[/COLOR]


To get permission to write into some places and do certain tasks - you need sudo .......

[B]Make sure you have removed your previous install - ( otherwise it could mix all the files - old & new )



Then you can try again by doing this >>>

sudo make install

( note there is no easy way out if you should screw your system up by doing it this way )
[/B]

---

### Post by spacerocket on 2014-04-08
Thanks for your answer

sudo apt-get remove xboard worked.

Then ->

  **sudo make install**
[sudo] password for user: 
Making install in po
make[1]: Entering directory `/home/user/po'
installing ../Downloads/xboard-4.7.3/./po/da.gmo as /usr/local/share/locale/da/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/de.gmo as /usr/local/share/locale/de/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/es.gmo as /usr/local/share/locale/es/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/it.gmo as /usr/local/share/locale/it/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/tr.gmo as /usr/local/share/locale/tr/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/zh_HK.gmo as /usr/local/share/locale/zh_HK/LC_MESSAGES/xboard.mo
installing ../Downloads/xboard-4.7.3/./po/zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/xboard.mo
if test "xboard" = "gettext-tools"; then \
      /bin/mkdir -p /usr/local/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ../Downloads/xboard-4.7.3/./po/$file \
                /usr/local/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/local/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/home/user/po'
make[1]: Entering directory `/home/user'
make[2]: Entering directory `/home/user'
 /bin/mkdir -p '/usr/local/bin'
  /usr/bin/install -c xboard '/usr/local/bin'
 /bin/mkdir -p '/usr/local/etc'
 /usr/bin/install -c -m 644 xboard.conf '/usr/local/etc'
 /bin/mkdir -p '/usr/local/share/applications'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./xboard.desktop Downloads/xboard-4.7.3/./xboard-fen-viewer.desktop Downloads/xboard-4.7.3/./xboard-pgn-viewer.desktop Downloads/xboard-4.7.3/./xboard-tourney.desktop Downloads/xboard-4.7.3/./xboard-config.desktop '/usr/local/share/applications'
 /bin/mkdir -p '/usr/local/share/icons/hicolor/48x48/apps'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./xboard.png '/usr/local/share/icons/hicolor/48x48/apps'
 /bin/mkdir -p '/usr/local/share/games/xboard/pixmaps/textures'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./pixmaps/cross32.xpm Downloads/xboard-4.7.3/./pixmaps/cross48.xpm Downloads/xboard-4.7.3/./pixmaps/board32.xpm Downloads/xboard-4.7.3/./pixmaps/board48.xpm Downloads/xboard-4.7.3/./pixmaps/ini32.xpm Downloads/xboard-4.7.3/./pixmaps/ini48.xpm '/usr/local/share/games/xboard/pixmaps/textures'
 /bin/mkdir -p '/usr/local/share/games/xboard/themes/textures'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./png/hatch.png Downloads/xboard-4.7.3/./png/wood_d.png Downloads/xboard-4.7.3/./png/wood_l.png Downloads/xboard-4.7.3/./png/xqboard.png '/usr/local/share/games/xboard/themes/textures'
 /bin/mkdir -p '/usr/local/share/games/xboard/themes/shogi'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./themes/shogi/WhiteGold.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteCrownedBishop.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteBishop.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteKing.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteKnight.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteGoldKnight.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteLance.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteGoldLance.svg Downloads/xboard-4.7.3/./themes/shogi/WhitePawn.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteGoldPawn.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteRook.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteCrownedRook.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteAdvisor.svg Downloads/xboard-4.7.3/./themes/shogi/WhiteGoldSilver.svg Downloads/xboard-4.7.3/./themes/shogi/BlackGold.svg Downloads/xboard-4.7.3/./themes/shogi/BlackCrownedBishop.svg Downloads/xboard-4.7.3/./themes/shogi/BlackBishop.svg Downloads/xboard-4.7.3/./themes/shogi/BlackKing.svg Downloads/xboard-4.7.3/./themes/shogi/BlackKnight.svg Downloads/xboard-4.7.3/./themes/shogi/BlackGoldKnight.svg Downloads/xboard-4.7.3/./themes/shogi/BlackLance.svg Downloads/xboard-4.7.3/./themes/shogi/BlackGoldLance.svg Downloads/xboard-4.7.3/./themes/shogi/BlackPawn.svg Downloads/xboard-4.7.3/./themes/shogi/BlackGoldPawn.svg Downloads/xboard-4.7.3/./themes/shogi/BlackRook.svg Downloads/xboard-4.7.3/./themes/shogi/BlackCrownedRook.svg Downloads/xboard-4.7.3/./themes/shogi/BlackAdvisor.svg Downloads/xboard-4.7.3/./themes/shogi/BlackGoldSilver.svg '/usr/local/share/games/xboard/themes/shogi'
 /bin/mkdir -p '/usr/local/share/games/xboard/sounds'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./sounds/cymbal.wav Downloads/xboard-4.7.3/./sounds/pop2.wav Downloads/xboard-4.7.3/./sounds/slap.wav Downloads/xboard-4.7.3/./sounds/ding1.wav Downloads/xboard-4.7.3/./sounds/laser.wav Downloads/xboard-4.7.3/./sounds/woodthunk.wav Downloads/xboard-4.7.3/./sounds/gong.wav Downloads/xboard-4.7.3/./sounds/penalty.wav Downloads/xboard-4.7.3/./sounds/honkhonk.wav Downloads/xboard-4.7.3/./sounds/phone.wav '/usr/local/share/games/xboard/sounds'
 /bin/mkdir -p '/usr/local/share/games/xboard/themes/default'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./svg/icon_white.svg Downloads/xboard-4.7.3/./svg/icon_black.svg Downloads/xboard-4.7.3/./svg/BlackAdvisor.svg Downloads/xboard-4.7.3/./svg/WhiteAdvisor.svg Downloads/xboard-4.7.3/./svg/BlackArchbishop.svg Downloads/xboard-4.7.3/./svg/WhiteArchbishop.svg Downloads/xboard-4.7.3/./svg/BlackBishop.svg Downloads/xboard-4.7.3/./svg/WhiteBishop.svg Downloads/xboard-4.7.3/./svg/BlackCanon.svg Downloads/xboard-4.7.3/./svg/WhiteCanon.svg Downloads/xboard-4.7.3/./svg/BlackChancellor.svg Downloads/xboard-4.7.3/./svg/WhiteChancellor.svg Downloads/xboard-4.7.3/./svg/BlackCobra.svg Downloads/xboard-4.7.3/./svg/WhiteCobra.svg Downloads/xboard-4.7.3/./svg/BlackCommoner.svg Downloads/xboard-4.7.3/./svg/WhiteCommoner.svg Downloads/xboard-4.7.3/./svg/BlackCrownedBishop.svg Downloads/xboard-4.7.3/./svg/WhiteCrownedBishop.svg Downloads/xboard-4.7.3/./svg/BlackCrownedRook.svg Downloads/xboard-4.7.3/./svg/WhiteCrownedRook.svg Downloads/xboard-4.7.3/./svg/BlackElephant.svg Downloads/xboard-4.7.3/./svg/WhiteElephant.svg Downloads/xboard-4.7.3/./svg/BlackGoldKnight.svg Downloads/xboard-4.7.3/./svg/WhiteGoldKnight.svg Downloads/xboard-4.7.3/./svg/BlackGoldLance.svg Downloads/xboard-4.7.3/./svg/WhiteGoldLance.svg Downloads/xboard-4.7.3/./svg/BlackGoldPawn.svg Downloads/xboard-4.7.3/./svg/WhiteGoldPawn.svg Downloads/xboard-4.7.3/./svg/BlackGoldSilver.svg Downloads/xboard-4.7.3/./svg/WhiteGoldSilver.svg Downloads/xboard-4.7.3/./svg/BlackGold.svg Downloads/xboard-4.7.3/./svg/WhiteGold.svg Downloads/xboard-4.7.3/./svg/BlackHawk.svg Downloads/xboard-4.7.3/./svg/WhiteHawk.svg Downloads/xboard-4.7.3/./svg/BlackKing.svg Downloads/xboard-4.7.3/./svg/WhiteKing.svg Downloads/xboard-4.7.3/./svg/BlackKnight.svg Downloads/xboard-4.7.3/./svg/WhiteKnight.svg Downloads/xboard-4.7.3/./svg/BlackLance.svg Downloads/xboard-4.7.3/./svg/WhiteLance.svg '/usr/local/share/games/xboard/themes/default'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./svg/BlackMarshall.svg Downloads/xboard-4.7.3/./svg/WhiteMarshall.svg Downloads/xboard-4.7.3/./svg/BlackNightrider.svg Downloads/xboard-4.7.3/./svg/WhiteNightrider.svg Downloads/xboard-4.7.3/./svg/BlackPawn.svg Downloads/xboard-4.7.3/./svg/WhitePawn.svg Downloads/xboard-4.7.3/./svg/BlackPrincess.svg Downloads/xboard-4.7.3/./svg/WhitePrincess.svg Downloads/xboard-4.7.3/./svg/BlackQueen.svg Downloads/xboard-4.7.3/./svg/WhiteQueen.svg Downloads/xboard-4.7.3/./svg/BlackRook.svg Downloads/xboard-4.7.3/./svg/WhiteRook.svg Downloads/xboard-4.7.3/./svg/BlackUnicorn.svg Downloads/xboard-4.7.3/./svg/WhiteUnicorn.svg Downloads/xboard-4.7.3/./svg/eo_Analyzing.svg Downloads/xboard-4.7.3/./svg/eo_Black.svg Downloads/xboard-4.7.3/./svg/eo_Clear.svg Downloads/xboard-4.7.3/./svg/eo_Ponder.svg Downloads/xboard-4.7.3/./svg/eo_Thinking.svg Downloads/xboard-4.7.3/./svg/eo_Unknown.svg Downloads/xboard-4.7.3/./svg/eo_White.svg '/usr/local/share/games/xboard/themes/default'
 /bin/mkdir -p '/usr/local/share/icons/hicolor/scalable/apps'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./xboard.svg '/usr/local/share/icons/hicolor/scalable/apps'
 /bin/mkdir -p '/usr/local/share/games/xboard/themes/xiangqi'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./themes/xiangqi/BlackAdvisor.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhiteAdvisor.svg Downloads/xboard-4.7.3/./themes/xiangqi/BlackCanon.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhiteCanon.svg Downloads/xboard-4.7.3/./themes/xiangqi/BlackElephant.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhiteElephant.svg Downloads/xboard-4.7.3/./themes/xiangqi/BlackKnight.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhiteKnight.svg Downloads/xboard-4.7.3/./themes/xiangqi/BlackGold.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhiteGold.svg Downloads/xboard-4.7.3/./themes/xiangqi/BlackPawn.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhitePawn.svg Downloads/xboard-4.7.3/./themes/xiangqi/BlackRook.svg Downloads/xboard-4.7.3/./themes/xiangqi/WhiteRook.svg '/usr/local/share/games/xboard/themes/xiangqi'
 /bin/mkdir -p '/usr/local/share/info'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./xboard.info '/usr/local/share/info'
 install-info --info-dir='/usr/local/share/info' '/usr/local/share/info/xboard.info'
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
 /bin/mkdir -p '/usr/local/share/man/man6'
 /usr/bin/install -c -m 644 'Downloads/xboard-4.7.3/./xboard.man' '/usr/local/share/man/man6/xboard.6'
 /bin/mkdir -p '/usr/local/share/mime/packages'
 /usr/bin/install -c -m 644 Downloads/xboard-4.7.3/./xboard.xml '/usr/local/share/mime/packages'
make  install-data-hook
make[3]: Entering directory `/home/kimon'
if test -z "" -a -n "/usr/bin/xdg-mime" -a -n "/usr/bin/xdg-desktop-menu" -a -n "/usr/bin/xdg-icon-resource" ; then \
        /usr/bin/xdg-mime install --mode system --novendor xboard.xml ;\
        /usr/bin/xdg-desktop-menu install --mode system --novendor xboard-pgn-viewer.desktop;\
        /usr/bin/xdg-desktop-menu install --mode system --novendor xboard-fen-viewer.desktop;\
        /usr/bin/xdg-desktop-menu install --mode system --novendor xboard-tourney.desktop;\
        /usr/bin/xdg-desktop-menu install --mode system --novendor xboard-config.desktop;\
        /usr/bin/xdg-icon-resource install --context mimetypes --size 32 pixmaps/board32.xpm application-x-chess-pgn;\
        /usr/bin/xdg-icon-resource install --context mimetypes --size 32 pixmaps/cross32.xpm application-x-xboard-trn;\
        /usr/bin/xdg-icon-resource install --context mimetypes --size 32 pixmaps/ini32.xpm application-x-xboard-opt;\
        /usr/bin/xdg-icon-resource install --context mimetypes --size 48 pixmaps/board48.xpm application-x-chess-pgn;\
        /usr/bin/xdg-icon-resource install --context mimetypes --size 48 pixmaps/cross48.xpm application-x-xboard-trn;\
        /usr/bin/xdg-icon-resource install --context mimetypes --size 48 pixmaps/ini48.xpm application-x-xboard-opt;\
    fi
xdg-mime: file 'xboard.xml' does not exist
xdg-desktop-menu: file 'xboard-pgn-viewer.desktop' does not exist
xdg-desktop-menu: file 'xboard-fen-viewer.desktop' does not exist
xdg-desktop-menu: file 'xboard-tourney.desktop' does not exist
xdg-desktop-menu: file 'xboard-config.desktop' does not exist
xdg-icon-resource: file 'pixmaps/board32.xpm' does not exist
xdg-icon-resource: file 'pixmaps/cross32.xpm' does not exist
xdg-icon-resource: file 'pixmaps/ini32.xpm' does not exist
xdg-icon-resource: file 'pixmaps/board48.xpm' does not exist
xdg-icon-resource: file 'pixmaps/cross48.xpm' does not exist
xdg-icon-resource: file 'pixmaps/ini48.xpm' does not exist
make[3]: [install-mime-database] Error 2 (ignored)
make[3]: Leaving directory `/home/user'
make[2]: Leaving directory `/home/user'
make[1]: Leaving directory `/home/user'

Something missing?

---

### Post by 23dornot23d on 2014-04-08
Yes something is missing .......

> 
**[COLOR=#ff0000]xdg-mime: file 'xboard.xml' does not exist[/COLOR]**
xdg-desktop-menu: file 'xboard-pgn-viewer.desktop' does not exist
xdg-desktop-menu: file 'xboard-fen-viewer.desktop' does not exist
xdg-desktop-menu: file 'xboard-tourney.desktop' does not exist
xdg-desktop-menu: file 'xboard-config.desktop' does not exist
xdg-icon-resource: file 'pixmaps/board32.xpm' does not exist
xdg-icon-resource: file 'pixmaps/cross32.xpm' does not exist
xdg-icon-resource: file 'pixmaps/ini32.xpm' does not exist
xdg-icon-resource: file 'pixmaps/board48.xpm' does not exist
xdg-icon-resource: file 'pixmaps/cross48.xpm' does not exist
xdg-icon-resource: file 'pixmaps/ini48.xpm' does not exist
**[COLOR=#ff0000]make[3]: [install-mime-database] Error 2 (ignored)[/COLOR]**


But it ignored it and carried on any way ........ the xml file is missing .... for some reason.
check the notes on this or do a search online to see if others have had the same problem
often answers can be found if its a piece of software used a lot ....... as others may have
done something similar ......

[https://github.com/shauncassingham/xboard/blob/master/xboard.xml](https://github.com/shauncassingham/xboard/blob/master/xboard.xml)

[http://raditha.com/blog/archives/chess-on-linux.html](http://raditha.com/blog/archives/chess-on-linux.html)

Have you looked at the other games of chess - I use dreamchess and brutal chess ..... but they are large installs

---

### Post by spacerocket on 2014-04-08
Hi,

Yes sometimes chess 960. I think xboard can play this if correctly set. 


I have no idea where to get [COLOR=#ff0000]xboard.xml[/COLOR]

I asked H.G.Muller maybe he knows.

I don`t.

---

### Post by 23dornot23d on 2014-04-08
This is the actual file that you are looking for in this link ....... 

( but how you make use of it is the question - it needs saving and putting in the right place )

[https://github.com/shauncassingham/xboard/blob/master/xboard.xml](https://github.com/shauncassingham/xboard/blob/master/xboard.xml)

---

### Post by spacerocket on 2014-04-08
Yep! 

It is quite interesting that now  I can open xboard even though I deleted it with **sudo apt-get remove xboard**. It is green and says: xboard 4.7.3. Maybe my system has mixed up something.

---

### Post by 23dornot23d on 2014-04-08
You have got a partially installed xboard ... unless you have added that last file .......

its said its installed what it could - except for one file .... is that file now in place and being used ?

You removed all the other version before we started - so things should not be mixed up - unless since then

you have then added the older one back to see what happens ( which would probably cause a mix up of old and new )

---

### Post by spacerocket on 2014-04-09
Hi,


No I don`t know what to do with this file. I asked H.G.Muller. I have fairymax (engine on xboard) do you know how can I remove it? I could also consider building xboard 4.7.2 from source....

Anyway now I have 4.7.3 and that should work as a communication protocol with me and the chess engine I`m going to program. [https://chessprogramming.wikispaces.com/Getting+Started](https://chessprogramming.wikispaces.com/Getting+Started)

 The **very first step** to writing a chess engine is to write a complete, [bug]("https://chessprogramming.wikispaces.com/Engine+Testing#bugs") free board representation that knows **every** rule of chess

Now  I have no idea how to implement this in practise but what I do know is that I can`t start from writing a chess engine. I need to learn plain C first and then maybe C++.

**First step**. I go to text editor and write: 

#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}

Then I save it in **my documents** with the name hello.c

Then I go to terminal window and type:

 gcc Documents/hello.c
Documents/hello.c:1:20: fatal error:  stdio.h: No such file or directory
 #include < stdio.h>
                    ^
compilation terminated.

---

### Post by steeldriver on 2014-04-09
Make sure you have installed the build-essential metapackage

Make sure you **don't** have a space before the header file name i.e.

```
#include <stdio.h>
```
not
```
#include < stdio.h>
```

---

### Post by 23dornot23d on 2014-04-09
You may want to look here too for specific questions relating to Xboard but its too old by the looks
but has a lot of frequently asked questions 

will see if there is anything better this is the main page - [http://www.gnu.org/software/xboard/](http://www.gnu.org/software/xboard/) 

 and this is just for history ... 

[URL="http://www.gnu.org/software/xboard/FAQ.html"]http://www.gnu.org/software/xboard/FAQ.html


[/URL]

---

### Post by spacerocket on 2014-04-09
Hello!

Save the code in the file hello.c, then [compile]("http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/compile.html") it by typing:  	gcc hello.c
  This creates an *executable* file a.out, which is then executed simply by typing its name. The result is that the characters `` Hello World'' are printed out, preceded by an empty line.  

Ok. I typed   **gcc Documents/hello.c** (gcc hello.c does not work, I specified the full path) -> nothing. [COLOR=#ff0000]This creates an *executable* file a.out, which is then executed simply by typing its name[/COLOR]

**OK**  Now when I type** gcc hello.c** -> 

gcc: error: hello.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.

[COLOR=#ff0000]The result is that the characters `` Hello World'' are printed out, preceded by an empty line.   [/COLOR]Not for me. I missed something?

Thanks for your time.

---

