---
title: "xgrafix configure: error: X11 includes not found"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by hMeU on 2013-11-16
Hi!

I was trying to install xgrafix 2.70.2 but I have run into trouble. I will write down the steps I followed:

[LIST=1]
[*]Downloaded xgrafix 2.70.2 from [http://ptsg.egr.msu.edu/pub/codes/xgrafix/](http://ptsg.egr.msu.edu/pub/codes/xgrafix/) (The Plasma Theory and Simulation Group).
[*]Extracted the tar archive and went through the README file.
[*]Installed the dependencies using the following command:
```
sudo aptitude install gcc g++ build-essential automake tk-dev imagemagick bison libx11-dev libxpm-dev libpng-dev fftw-dev  libfftw3-dev h5utils hdf5-tools libhdf5-serial-*

```
[*]aptitude was unable to install libhdf5-serial-* so I installed those with apt-get. Also, libpng12-dev was installed instead of libpng-dev.
[*]Did "sudo apt-get update" and "sudo apt-get upgrade" and rebooted.
[*]Did ./configure from the xgrafix folder.
[*]Error!
[/LIST]

Output upon executing ./configure -q
```

Using C++ compiler g++
Using C compiler gcc
Setting the flags per system and C++ compiler: g++
Serial C++ compiler is `g++'
configure: WARNING: Caution: version  is not known to work.
Serial C compiler is `gcc'
configure: WARNING: Fortran libraries will be invalid.
configure: WARNING: x11.m4 is obsolete.  Please use AC_PATH_X or AC_PATH_XTRA.
configure: error: X11 includes not found in /usr/X11R6/include:/usr/X11/include:/usr/include:/usr/local/include:/loc/include:/usr/openwin/include:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games.  Use --with-X11-include to set the location of X11/Xlib.h.

```

Output upon executing ./configure
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
Using C++ compiler g++
Using C compiler gcc
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking whether time.h and sys/time.h may both be included... yes
checking for BSD-compatible nm... 
/usr/bin/nm -B
Setting the flags per system and C++ compiler: g++
checking for g++... /usr/bin/g++
Serial C++ compiler is `g++'
checking g++ version... g++
configure: WARNING: Caution: version  is not known to work.
checking for -fsquangle... no
checking how to build libraries... with ar cr  
checking for gcc... /usr/bin/gcc
Serial C compiler is `gcc'
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether c++ compiler supports exception handling... yes
checking whether c++ compiler supports typename... yes
checking whether c++ compiler can explicitly instantiate templates... yes
checking whether c++ compiler supports RTTI... yes
checking whether c++ compiler supports namespaces... yes
checking whether c++ compiler has complex in the namespace std... yes
checking whether c++ compiler has streams in the namespace std... yes
checking whether c++ compiler can overload const type conversions... yes
checking whether c++ compiler knows mutable... yes
checking whether template friends need brackets... yes
checking whether nontype template operators are allowed... no
checking whether static variables can be declared generally... yes
configure: WARNING: Fortran libraries will be invalid.
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking for ranlib... ranlib
checking what the library suffix is... .a
checking how to install libraries... with ${INSTALL} -m 644
configure: WARNING: x11.m4 is obsolete.  Please use AC_PATH_X or AC_PATH_XTRA.
checking for X11/Xlib.h... no
configure: error: X11 includes not found in /usr/X11R6/include:/usr/X11/include:/usr/include:/usr/local/include:/loc/include:/usr/openwin/include:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games.  Use --with-X11-include to set the location of X11/Xlib.h.

```

[B]But, the file "Xlib.h" is not missing. It is there in "/usr/include/X11". What probably could be causing the problem ?
[/B]
My system specifications:
Device Name: Dell-XPS-L501X
Memory: 3.6 GB
Processor: Intel® Core™ i5 CPU M 480 @ 2.67GHz × 4
Graphics: Intel® Ironlake Mobile (I also have nVidia GeForce GT 420M, but it doesn't show anywhere.)
OS Type: 64-bit

Dual Boot
Ubuntu 13.10: Fresh install. Updated.
Windows 7: Home Premium

---

### Post by dhakarocker on 2014-07-07
I am having exactly the same problem. Have you found anyway to solve this problem?

---

