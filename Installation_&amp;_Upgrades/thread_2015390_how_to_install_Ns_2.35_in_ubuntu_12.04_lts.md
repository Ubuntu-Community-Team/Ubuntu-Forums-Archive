---
title: "how to install Ns 2.35 in ubuntu 12.04 lts"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by muthu kumar on 2012-07-03
how to install ns 2.35 allinone package in ubuntu 12.04...

i did:

tar zxvf ns-allinone-2.35.tar.gz
cd ns-allinone-2.35
./install

but still i got an error related to libxmu-dev package...

help me guys..

---

### Post by raja.genupula on 2012-07-03
> but still i got an error related to libxmu-dev package...

whats that error you need to say us , then only we can understand what exactly causing the problem . paste here the terminal lines you got and wrap it in code tags .

---

### Post by cipherboy_loc on 2012-07-03
Off the website, there is a link on common installation errors, [here]("http://www.isi.edu/nsnam/ns/ns-problems.html"). While we need more information, it looks to me it is trying to compile libxmu-dev, but failing (as part of a dependency problem maybe?). 


Cipherboy

---

### Post by muthu kumar on 2012-07-03
[U][B]i followed:
[/B][/U]**Install NS2 (ns-allinone-2.35) on Ubuntu 11.04 for beginners**

#########################
 
[LIST=1]
[*]Part I: Introduction
[/LIST]
 #########################
 This installation guide is on Linux **Ubuntu 11.04 **(download from [here]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Natty-Narwhal-62881.shtml")), and  uses **ns-allinone-2.35** source  file for NS2. I assume that you have the skill to install Ubuntu,  so I skip this process, and focus on the installation of NS2  (step-by-step with commands).
 #########################
 
[LIST=1]
[*]Part II: Install
[/LIST]
 #########################
 [Step 1]
 Before install NS2, you have to install some essential softwares:
 [COLOR=#008000]sudo apt-get install tcl8.5-dev tk8.5-dev[/COLOR] [COLOR=#008000]sudo apt-get install build-essential autoconf automake [/COLOR] [COLOR=#008000]sudo apt-get install perl xgraph libxt-dev libx11-dev libxmu-dev[/COLOR] [Step 2]
 Download NS2 source file  from from [here]("http://sourceforge.net/projects/nsnam/files/allinone/ns-allinone-2.35/ns-allinone-2.35.tar.gz/download").
Then you will get a file named &#8220;[COLOR=#0000ff]ns-allinone-2.35.tar.gz[/COLOR]&#8220;
 [Step 3]
 Unpack ns-allinone-2.35.tar.gz to your home directory. (*/home/stan* is my home directory, you SHOULD change it to your own!)
 [COLOR=#008000]tar -zxvf ns-allinone-2.35.tar.gz -C /home/stan[/COLOR] [Step 4]
 4.1) Modify the makefile (NOTICE: I use &#8220;vi&#8221; for an editor, you can use &#8220;gedit&#8221; instead)
 [COLOR=#008000]vi /home/stan/ns-allinone-2.35/otcl-1.14/Makefile.in[/COLOR] 4.2) Change [COLOR=#ff00ff]CC = @CC@[/COLOR] to [COLOR=#ff00ff]CC = @CC@ -V 4.5[/COLOR]
 (For changing this because the gcc complier in Ubuntu 11.04 is version 4.5, however NS2 only supports gcc-4.3 below. NOTICE the [COLOR=#ff00ff]V[/COLOR] is capital.)
 [Step 5]
 Install NS2:
 [COLOR=#008000]cd /home/stan/ns-allinone-2.35[/COLOR] [COLOR=#008000]sudo ./install[/COLOR]
_**terminal lines:**_

* Build Tk8.5.10
============================================================
rm -f *.a *.o libtk* core errs *~ \#* TAGS *.E a.out \
        errors wish tktest lib.exp Tk *.rsrc
rm -rf Makefile config.status config.cache config.log tkConfig.sh \
        SCRPtk.* prototype tkConfig.h *.plist Tk.framework
./install: 439: ./install: autoconf: not found
checking for Tcl configuration... found /home/dante/ns-allinone-2.35/tcl8.5.10/unix/tclConfig.sh
checking for existence of /home/dante/ns-allinone-2.35/tcl8.5.10/unix/tclConfig.sh... loading
checking for tclsh... /home/dante/ns-allinone-2.35/bin/tclsh8.5
checking for tclsh in Tcl build directory... /home/dante/ns-allinone-2.35/tcl8.5.10/unix/tclsh
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking if the compiler understands -pipe... yes
checking for building with threads... no (default)
checking how to build libraries... static
checking for ranlib... ranlib
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking if compiler supports visibility "hidden"... yes
checking if rpath support is requested... yes
checking system version... Linux-3.2.0-23-generic-pae
checking for dlopen in -ldl... yes
checking for ar... ar
checking for build with symbols... no
checking for required early compiler flags...  _LARGEFILE64_SOURCE
checking for 64-bit integer type... long long
checking for struct dirent64... no
checking for struct stat64... yes
checking for open64... yes
checking for lseek64... yes
checking for off64_t... yes
checking whether byte ordering is bigendian... no
checking for fd_set in sys/types... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for strtod... yes
checking for Solaris2.4/Tru64 strtod bugs... ok
checking for mode_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for intptr_t... yes
checking for uintptr_t... yes
checking pw_gecos in struct pwd... yes
checking for X... no
checking for X11 header files... couldn't find any!
checking for X11 libraries... checking for XCreateWindow in -lXwindow... no
could not find any!  Using -lX11.
checking for main in -lXbsd... no
checking whether to try to use XScreenSaver... no
checking whether to use xft... no
checking whether char is unsigned... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating tkConfig.sh
gcc -c -O2  -pipe  -Wall -fPIC -I/home/dante/ns-allinone-2.35/tk8.5.10/unix/../unix -I/home/dante/ns-allinone-2.35/tk8.5.10/unix/../generic -I/home/dante/ns-allinone-2.35/tk8.5.10/unix/../bitmaps -I/home/dante/ns-allinone-2.35/tcl8.5.10/generic -I/home/dante/ns-allinone-2.35/tcl8.5.10/unix  -DPACKAGE_NAME=\"tk\" -DPACKAGE_TARNAME=\"tk\" -DPACKAGE_VERSION=\"8.5\" -DPACKAGE_STRING=\"tk\ 8.5\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1 -DSTATIC_BUILD=1 -DMODULE_SCOPE=extern\ __attribute__\(\(__visibility__\(\"hidden\"\)\)\) -DTCL_SHLIB_EXT=\".so\" -DTCL_CFG_OPTIMIZED=1 -DTCL_CFG_DEBUG=1 -D_LARGEFILE64_SOURCE=1 -DTCL_WIDE_INT_TYPE=long\ long -DHAVE_STRUCT_STAT64=1 -DHAVE_OPEN64=1 -DHAVE_LSEEK64=1 -DHAVE_TYPE_OFF64_T=1 -DHAVE_SYS_TIME_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_INTPTR_T=1 -DHAVE_UINTPTR_T=1 -DHAVE_PW_GECOS=1      -DTCL_NO_DEPRECATED    /home/dante/ns-allinone-2.35/tk8.5.10/unix/../generic/tk3d.c
In file included from /home/dante/ns-allinone-2.35/tk8.5.10/unix/../generic/tkInt.h:19:0,
                 from /home/dante/ns-allinone-2.35/tk8.5.10/unix/../generic/tk3d.c:14:
/home/dante/ns-allinone-2.35/tk8.5.10/unix/../generic/tk.h:76:23: fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make: *** [tk3d.o] Error 1
tk8.5.10 make failed! Exiting ...
For problems with Tcl/Tk see [http://www.scriptics.com](http://www.scriptics.com)

---

### Post by raja.genupula on 2012-07-04
```
libx11-dev 
```

open your synaptic package manager and look for the installation status of the above package .

---

### Post by madhavpandhare on 2013-04-04
I facing the problem to install the ns2 12.04. When the command i type i.e.  " bash : ./install " it gives the error as permission denied.
please give the solution for that...

---

