---
title: "Error occurs when installing Octave 3.4.0 on ubuntu_12.04 (32-bit)"
date: 2015-07-07
forum: Installation &amp; Upgrades
---

### Post by janis9 on 2015-07-07
Hi,

I am trying to install Octave 3.4.0 on my laptop, but when I proceed to the step 'make', the following errors always show. I've already searched for many solutions, but still the case. Could anyone help? Thank you.

```
[COLOR=#000000][FONT=Ubuntu Mono]In file included from oct-alloc.cc:29:0:oct-alloc.h:32:28: error: expected ')' before 'item_sz'[/FONT][/COLOR]oct-alloc.h:39:9: error: expected ';' at end of member declaration
oct-alloc.h:39:23: error: expected ')' before 'size'
oct-alloc.h:42:23: error: 'size_t' has not been declared
oct-alloc.h:57:3: error: 'size_t' does not name a type
oct-alloc.cc:32:26: error: 'void* octave_allocator::alloc' is not a static member of 'class octave_allocator'
oct-alloc.cc:32:26: error: 'size_t' was not declared in this scope
oct-alloc.cc:32:26: note: suggested alternative:
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:155:26: note:   'std::size_t'
oct-alloc.cc:33:1: error: expected ',' or ';' before '{' token
make[3]: *** [liboctave_la-oct-alloc.lo] Error 1
make[3]: Leaving directory `/home/janis/TLD/octave-3.4.0/liboctave'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/janis/TLD/octave-3.4.0/liboctave'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/janis/TLD/octave-3.4.0' [COLOR=#000000][FONT=Ubuntu Mono]make: *** [all] Error 2[/FONT][/COLOR]
```

---

### Post by steeldriver on 2015-07-07
You seem to be using gcc-4.6: if so, you may be bumping up against one of the gcc-4.6 C++ Language Issues mentioned here --> [https://gcc.gnu.org/gcc-4.6/porting_to.html](https://gcc.gnu.org/gcc-4.6/porting_to.html)

It may actually be less trouble to revert to gcc-4.5 (which should be available from the 12.04 repository) - see [http://oz123.github.io/writings/2011-05-24-building-octave-34-on-debian-sid/](http://oz123.github.io/writings/2011-05-24-building-octave-34-on-debian-sid/)

---

### Post by janis9 on 2015-07-07
Thank you. I've tried as you suggested, but still the case.:cry: The errors are little different from the former one maybe because I change to another download version of Octave 3.4.

```
In file included from oct-alloc.cc:29:0:oct-alloc.h:32:28: error: expected ')' before 'item_sz'
oct-alloc.h:39:9: error: expected ';' at end of member declaration
oct-alloc.h:39:23: error: expected ')' before 'size'
oct-alloc.h:42:23: error: 'size_t' has not been declared
oct-alloc.h:57:3: error: 'size_t' does not name a type
oct-alloc.cc:32:26: error: 'void* octave_allocator::alloc' is not a static member of 'class octave_allocator'
oct-alloc.cc:32:26: error: 'size_t' was not declared in this scope
oct-alloc.cc:32:26: note: suggested alternative:
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:155:26: note:   'std::size_t'
oct-alloc.cc:33:1: error: expected ',' or ';' before '{' token
make[3]: *** [liboctave_la-oct-alloc.lo] Error 1
make[3]: Leaving directory `/home/janis/TLD/octave-3.4.0/liboctave'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/janis/TLD/octave-3.4.0/liboctave'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/janis/TLD/octave-3.4.0'
make: *** [all] Error 2



```

---

### Post by steeldriver on 2015-07-07
Hmm... are you sure you are exporting the CC and CXX variables correctly? it still appears to be using files from 4.6

```

/usr/include/c++/**4.6**/i686-linux-gnu/./bits/c++config.h:155:26: note:   'std::size_t'

```

---

### Post by janis9 on 2015-07-08
Thanks. I tried again and the problems above were solved but a new one occurs. I searched online and used [COLOR=#000000]configure flag --without-curl makes the build process work, but I am not sure whether this would affect the function of Octave.[/COLOR]

```
DLD-FUNCTIONS/urlwrite.cc:55:24: fatal error: curl/types.h: No such file or directorycompilation terminated.
make[3]: *** [DLD-FUNCTIONS/DLD_FUNCTIONS_urlwrite_la-urlwrite.lo] Error 1
make[3]: Leaving directory `/home/janis/TLD/octave-3.4.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/janis/TLD/octave-3.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/janis/TLD/octave-3.4.0'
make: *** [all] Error 2



```

---

### Post by steeldriver on 2015-07-08
Did you try running it yet?
```

./run-octave

```

IIRC `./configure` should have checked for curl.h and disabled curl support automatically: I'm not sure why that didn't happen for you. But yes, octave has a number of "optional" components that the build will generally skip if the corresponding development libraries / headers are missing from your system at build time: you may find that functions such as `urlread` and `urlwrite` are unavailable.

FWIW I configured a 32-bit Lubuntu VM and was able to build a minimal (non-graphic) version of octave-3.4.0 with just the addition of

```

libopenblas-dev liblapack-dev libreadline-dev libncurses5-dev

```

With the default gcc/g++/gfortran 4.6 (as installed via `build-essential` and `gfortran`) I initially got the same size_t errors as you, however after

```

sudo apt-get install gcc-4.5 g++-4.5 gfortran-4.5

```

I was able to build successfully using just

```

make clean

make "CC=gcc-4.5" "CXX=g++-4.5" "F77=gfortran-4.5"

```

without re-configuring or even exporting the environment variables: however for consistency I'd recommend starting over and exporting the variables before running ./configure - or passing them on the ./configure command line e.g.

```

CC=gcc-4.5 CXX=g++-4.5 F77=gfortran-4.5 ./configure

```

---

### Post by janis9 on 2015-07-08
Thanks a lot. Finally, I downloaded a different version of Octave 3.4.3 instead of 3.4.0 and installed it as steps shown in the following thread:
[HTML]http://ubuntuforums.org/showthread.php?t=1890412[/HTML]

Finally, it works!

---

