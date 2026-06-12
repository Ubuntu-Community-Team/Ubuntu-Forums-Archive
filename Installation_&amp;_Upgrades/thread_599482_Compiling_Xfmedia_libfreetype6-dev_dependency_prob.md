---
title: "Compiling Xfmedia: libfreetype6-dev dependency problem"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-11-01
Hello there..! 

I'm doing my first steps in manually compiling a few things - in this case Xfmedia player 0.92.

In the install-README there's a note that the program is dependent to libxine1.0.0 (or newer?) and that one has to have the -dev version installed also.

So I checked in Synaptic and tried to install the missing libfreetype6-dev 
but it wouldn't work (due to same reason like with apt-get below). I checked the 'properties > dependencies' of that library, showing dependency conflicts:
> .
needed libfreetype6 (=2.2.1.5-ubuntu1.1)
needed libc6-dev | libc-dev
needed zlib1-dev | libz-dev

in conflict with freetype0-dev
in conflict with freetype1
in conflict with freetype1-dev

replaced freetype0-dev
replaced freetype1-dev

There were several similar issues mentioned in the forums, one suggested to do 
```
sudo apt-get update first
``` 
(which I also tried - though I can't figure the difference to 'Reload' in Synaptic) and then to do 
```
sudo apt-get install libfreetype6-dev
``` 

which produced pretty much the same dependency error like Synaptic:
> Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
libfreetype6-dev: Hängt ab: libfreetype6 (= 2.2.1-5ubuntu1.1) aber 2.3.5-1mlind1~feisty0.1 soll installiert werden

-> meaning: 'The following packets have non-fullfilled dependencies :...... depends on.....(..) but .....~...shall be installed"

Does this mean that I've got to remove freetype0-dev, freetype1 and freetype1-dev before installing libfreetype6-dev? Or is there a problem with a missing repository (though I can't believe that's the case)?

Can you give some advice on this, please?


thanks, perixx

---

### Post by perixx on 2007-11-01
Update:

I got a little farther by now; I figured out that my system was missing the zlib1g-dev version.... but now I get the following error after doing ./configure: 

> 'X Window system libraries and header files are required'


and config.log shows following errors (all I figured, that might indicate problems):


> 
/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown
...
configure:2116: checking for a BSD-compatible install
configure:2172: result: /usr/bin/install -c
configure:2183: checking whether build environment is sane
configure:2226: result: yes
configure:2291: checking for gawk
configure:2321: result: no
configure:2291: checking for mawk
configure:2307: found /usr/bin/mawk
configure:2318: result: mawk
...
configure:3633: checking dependency style of gcc
configure:3723: result: gcc3
configure:3746: checking how to run the C preprocessor
configure:3786: gcc -E  conftest.c
configure:3792: $? = 0
configure:3830: gcc -E  conftest.c
conftest.c:11:28: error: ac_nonexistent.h: No such file or directory
configure:3836: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
| #include <ac_nonexistent.h>
configure:3876: result: gcc -E
configure:3905: gcc -E  conftest.c
configure:3911: $? = 0
configure:3949: gcc -E  conftest.c
conftest.c:11:28: error: ac_nonexistent.h: No such file or directory
configure:3955: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
configure:4577: checking minix/config.h usability
configure:4594: gcc -c -g -O2  conftest.c >&5
conftest.c:54:26: error: minix/config.h: No such file or directory
configure:4600: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
| #include <minix/config.h>
configure:4631: result: no
configure:4635: checking minix/config.h presence
configure:4650: gcc -E  conftest.c
conftest.c:21:26: error: minix/config.h: No such file or directory
configure:4656: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
| #include <minix/config.h>
configure:4677: result: no
configure:4710: checking for minix/config.h
configure:4717: result: no
configure:4795: checking for gcc
configure:4822: result: gcc
configure:5060: checking for C compiler version
configure:5067: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:5070: $? = 0
configure:5077: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:5080: $? = 0
configure:5087: gcc -V >&5
gcc: '-V' option must have argument
configure:5090: $? = 1
configure:5093: checking whether we are using the GNU C compiler
configure:5162: result: yes
configure:5167: checking whether gcc accepts -g
configure:5353: result: yes
configure:5370: checking for gcc option to accept ISO C89
configure:5490: result: none needed
configure:5510: checking dependency style of gcc
configure:5600: result: gcc3
...
configure:6810: checking for C++ compiler version
configure:6817: g++ --version >&5
./configure: line 6818: g++: command not found
configure:6820: $? = 127
configure:6827: g++ -v >&5
./configure: line 6828: g++: command not found
configure:6830: $? = 127
configure:6837: g++ -V >&5
./configure: line 6838: g++: command not found
configure:6840: $? = 127
configure:6843: checking whether we are using the GNU C++ compiler
configure:6872: g++ -c   conftest.cpp >&5
./configure: line 6873: g++: command not found
configure:6878: $? = 127
configure: failed program was:
| /* confdefs.h.  */
...
configure:6912: result: no
configure:6917: checking whether g++ accepts -g
configure:6947: g++ -c -g  conftest.cpp >&5
./configure: line 6948: g++: command not found
configure:6953: $? = 127
configure: failed program was:
| /* confdefs.h.  */
...
configure:7002: g++ -c   conftest.cpp >&5
./configure: line 7003: g++: command not found
configure:7008: $? = 127
configure: failed program was:
| /* confdefs.h.  */
...
configure:7058: g++ -c -g  conftest.cpp >&5
./configure: line 7059: g++: command not found
configure:7064: $? = 127
configure: failed program was:
| /* confdefs.h.  */
...
configure:7607: checking for Fortran 77 compiler version
configure:7614:  --version >&5
./configure: line 7615: --version: command not found
configure:7617: $? = 127
configure:7624:  -v >&5
./configure: line 7625: -v: command not found
configure:7627: $? = 127
configure:7634:  -V >&5
./configure: line 7635: -V: command not found
configure:7637: $? = 127
configure:7645: checking whether we are using the GNU Fortran 77 compiler
configure:7664:  -c  conftest.F >&5
./configure: line 7665: -c: command not found
configure:7670: $? = 127
configure: failed program was:
|       program main
...
./configure: line 7728: -c: command not found
configure:7733: $? = 127
configure: failed program was:
|       program main
...
configure:8819: gcc -c -g -O2  -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option "-fno-rtti" is valid for C++/ObjC++ but not for C
...
configure:21916: gcc -c -g -O2  conftest.c >&5
In file included from conftest.c:74:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/varargs.h:4:2: error: #error "GCC no longer implements <varargs.h>."
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/varargs.h:5:2: error: #error "Revise your code to use <stdarg.h>."
configure:21922: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
| #include <varargs.h>
configure:21953: result: no
configure:21957: checking varargs.h presence
configure:21972: gcc -E  conftest.c
In file included from conftest.c:41:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/varargs.h:4:2: error: #error "GCC no longer implements <varargs.h>."
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/varargs.h:5:2: error: #error "Revise your code to use <stdarg.h>."
configure:21978: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
conftest.c:50:22: error: X11/Xlib.h: No such file or directory
...

configure:24528: result: no
...
configure:25980: error: X Window system libraries and header files are required
...
#define X_DISPLAY_MISSING 1
************(last line)**********


I have no idea, but maybe I use the wrong gcc version (4.xx instead of 3.xx)? I believe I may also miss the g++ compiler, from what the log shows... but Fortran / minix ??

Let's see, if installing g++ compiler works out...


perixx

---

### Post by perixx on 2007-11-02
Allright, I'm slowly making progress;


I was obviously right about the missing g++ compiler in the first place...

I installed it along with
```
sudo apt-get build-essential
```
which was recommended by some postings around here.

Then I still had the 'error: X Window system libraries and header files are required' issue, which I could track down to 
```
xlibs-dev
``` which contained 'x-dev', and I installed it via Synaptic.


Now I'm stuck with the following ./configure - output:
> checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.21
checking for gmodule-2.0 >= 2.6.0... not found
*** The required package gmodule-2.0 was not found on your system.
*** Please install gmodule-2.0 (atleast version 2.6.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.


I wasn't able to find a 'gmodule-2' package with Synaptic, so I'm not quite sure what's next. Updating the 'pkg-config' package?


perixx

---

### Post by perixx on 2007-11-02
Hello...

Here I am again, another compiling issue with 'libfreetype6-dev' (this time another program). From what I can read of the Synaptic dependency conflicts, I can't install libfreetype6-dev, because the installed libfreetype6 is maybe outdated...

Obviously many programs depend on these libraries, so I'll give it a try and update it... hopefully I'll get back soon :] !! 


perixx

---

