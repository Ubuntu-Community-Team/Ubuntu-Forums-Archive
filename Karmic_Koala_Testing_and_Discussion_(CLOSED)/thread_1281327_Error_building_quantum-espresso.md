---
title: "Error building quantum-espresso"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Miguel on 2009-10-03
[SIZE="5"]**SOLVED:**[/SIZE] the best solution so far is at the end of this post (2009-12-14).

Dear ubunteros,

I dist-upgraded yesterday from 64bit jaunty to karmic and, although some issues are bothering me, the most pressing issue is that I can't build quantum-espresso (a DFT package) from source. I have BLAS, ATLAS and LAPACK installed, as well as FFTW3 (with the needed -dev packages). However, after issuing "make pw", compilation stops with the following:

```

make[1]: se ingresa al directorio `/usr/local/src/espresso-4.1/clib'
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c stack.c
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c c_mkdir.c
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c cptimer.c
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c eval_infix.c
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c fft_stick.c
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c indici.c
cc -O3 -D__GFORTRAN -D__FFTW3 -D__MPI -D__PARA -I../include  -c memstat.c
In file included from /usr/include/stdio.h:907,
                 from /usr/include/malloc.h:26,
                 from memstat.c:24:
/usr/include/bits/stdio.h: In function &#8216;memstat_&#8217;:
/usr/include/bits/stdio.h:46: error: nested function &#8216;getchar&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:45: error: static declaration of &#8216;getchar&#8217; follows non-static declaration
/usr/include/stdio.h:520: note: previous declaration of &#8216;getchar&#8217; was here
/usr/include/bits/stdio.h:55: error: nested function &#8216;fgetc_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:54: error: static declaration of &#8216;fgetc_unlocked&#8217; follows non-static declaration
/usr/include/stdio.h:543: note: previous declaration of &#8216;fgetc_unlocked&#8217; was here
/usr/include/bits/stdio.h:65: error: nested function &#8216;getc_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:64: error: static declaration of &#8216;getc_unlocked&#8217; follows non-static declaration
/usr/include/stdio.h:532: note: previous declaration of &#8216;getc_unlocked&#8217; was here
/usr/include/bits/stdio.h:72: error: nested function &#8216;getchar_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:71: error: static declaration of &#8216;getchar_unlocked&#8217; follows non-static declaration
/usr/include/stdio.h:533: note: previous declaration of &#8216;getchar_unlocked&#8217; was here
/usr/include/bits/stdio.h:81: error: nested function &#8216;putchar&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:80: error: static declaration of &#8216;putchar&#8217; follows non-static declaration
/usr/include/bits/stdio.h:90: error: nested function &#8216;fputc_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:89: error: static declaration of &#8216;fputc_unlocked&#8217; follows non-static declaration
/usr/include/bits/stdio.h:100: error: nested function &#8216;putc_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:99: error: static declaration of &#8216;putc_unlocked&#8217; follows non-static declaration
/usr/include/bits/stdio.h:107: error: nested function &#8216;putchar_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:106: error: static declaration of &#8216;putchar_unlocked&#8217; follows non-static declaration
/usr/include/bits/stdio.h:127: error: nested function &#8216;feof_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:126: error: static declaration of &#8216;feof_unlocked&#8217; follows non-static declaration
/usr/include/stdio.h:809: note: previous declaration of &#8216;feof_unlocked&#8217; was here
/usr/include/bits/stdio.h:134: error: nested function &#8216;ferror_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio.h:133: error: static declaration of &#8216;ferror_unlocked&#8217; follows non-static declaration
/usr/include/stdio.h:810: note: previous declaration of &#8216;ferror_unlocked&#8217; was here
In file included from /usr/include/stdio.h:910,
                 from /usr/include/malloc.h:26,
                 from memstat.c:24:
/usr/include/bits/stdio2.h:33: error: nested function &#8216;sprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:32: error: static declaration of &#8216;sprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:46: error: nested function &#8216;vsprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:44: error: static declaration of &#8216;vsprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:64: error: nested function &#8216;snprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:62: error: static declaration of &#8216;snprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:77: error: nested function &#8216;vsnprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:75: error: static declaration of &#8216;vsnprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:97: error: nested function &#8216;fprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:96: error: static declaration of &#8216;fprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:104: error: nested function &#8216;printf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:103: error: static declaration of &#8216;printf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:116: error: nested function &#8216;vprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:115: error: static declaration of &#8216;vprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:127: error: nested function &#8216;vfprintf&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:125: error: static declaration of &#8216;vfprintf&#8217; follows non-static declaration
/usr/include/bits/stdio2.h:227: error: nested function &#8216;gets&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:226: error: static declaration of &#8216;gets&#8217; follows non-static declaration
/usr/include/stdio.h:612: note: previous declaration of &#8216;gets&#8217; was here
/usr/include/bits/stdio2.h:246: error: nested function &#8216;fgets&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:245: error: static declaration of &#8216;fgets&#8217; follows non-static declaration
/usr/include/stdio.h:604: note: previous declaration of &#8216;fgets&#8217; was here
/usr/include/bits/stdio2.h:276: error: nested function &#8216;fread&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:274: error: static declaration of &#8216;fread&#8217; follows non-static declaration
/usr/include/stdio.h:682: note: previous declaration of &#8216;fread&#8217; was here
/usr/include/bits/stdio2.h:337: error: nested function &#8216;fread_unlocked&#8217; declared &#8216;extern&#8217;
/usr/include/bits/stdio2.h:335: error: static declaration of &#8216;fread_unlocked&#8217; follows non-static declaration
/usr/include/stdio.h:710: note: previous declaration of &#8216;fread_unlocked&#8217; was here
make[1]: *** [memstat.o] Error 1
make[1]: se sale del directorio `/usr/local/src/espresso-4.1/clib'
make: *** [libs] Error 2

```

This worked perfectly fine in Jaunty. I suspected it was caused by the switch to gcc 4.4, so I installed gfortran-4.3 (together with gcc and cpp), but I still got the same error. Furthermore, the code compiles OK in Debian testing using version 4.4. Any idea?

Also, if any of you could try if this works on your computer, I'd be grateful. You can download quantum-espresso [here](http://www.quantum-espresso.org/download.php) (it's GPL)



*EDIT:* I'm adding the best **solution** so far, because I've already received two PMs asking for the solution and I know from at least two mates who had issues compiling this.

The real issue with quantum-Espresso is a nonstandard "include" statement in ioctl. Because Karmic's gcc and gfortran are much stricter (gcc becomes stricter and stricter with every release), they refuse to compile something that worked on the past. 

In order to get Q-E compiled, go to espresso/clib (espresso is where you unzipped q-e) and edit file memstat.c. There, you must cut line 24:

#include <malloc.h>

and paste it right after the other include in line 9. The file should end up looking like this:
```

/*
  Copyright (C) 2002 FPMD group
  This file is distributed under the terms of the
  GNU General Public License. See the file `License'
  in the root directory of the present distribution,
  or http://www.gnu.org/copyleft/gpl.txt .
*/

#include "c_defs.h"
#include <malloc.h>

/* 
  This function return the numer of kilobytes allocated
  by the calling process. 
  Auhor: Carlo Cavazzoni.
*/

void F77_FUNC(memstat,MEMSTAT)(int *kilobytes)
{
#if defined (__SVR4) && defined (__sun)
#define SUN_MALLINFO
#endif

#if defined(HAVE_MALLINFO) && !defined(__QK_USER__) && !defined(SUN__MALLINFO) 
  struct mallinfo info;  
  info = mallinfo();

#if defined(__AIX)
  *kilobytes = (info.arena) / 1024 ;
#else
  *kilobytes = (info.arena + info.hblkhd) / 1024 ;
#endif

#else
  *kilobytes = -1;
#endif
}
```

---

### Post by dinxter on 2009-10-03
i seem to remember something about not defining HAVE_MALLINFO, i'll check it out

---

### Post by dinxter on 2009-10-03
commenting out 
$as_echo "#define HAVE_MALLINFO 1" >>confdefs.h
in configure does indeed allow expresso to build on the current gfortran-4.4 fine.
Better to find out what test is going wrong in the build script generators if you've got the time but the above will work for the moment

---

### Post by Miguel on 2009-10-03
Thank you very much for the tip, dinxter. That seems to work. I'll get in touch with the devs and see what can be done.

As a side note, do you have any clues about what changes might make the compilation work in debian testing and fail in karmic?

---

### Post by dinxter on 2009-10-03
sorry, i really couldnt say, i only have karmic installed which doesnt help comparison. itll be easier for the developers to work that one out than it will be for me no doubt, i'm more of a 'basic set of skills with autotools' type of person :)

---

### Post by dinxter on 2009-10-03
in case it helps, the test thats passing and adding the define that doesnt work is,

configure.ac
```
AC_CHECK_MEMBER([struct mallinfo.arena],
                [AC_DEFINE(HAVE_MALLINFO)],
                ,
                [#include <malloc.h>])

```heres the output of the debug mode
```
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
+ ac_fn_c_check_member 4245 'struct mallinfo' arena ac_cv_member_struct_mallinfo_arena '#include <malloc.h>
'
+ as_lineno=4245
+ as_lineno_stack=as_lineno_stack=
+ printf '%s\n' 'configure:4245: checking for struct mallinfo.arena'
+ printf %s 'checking for struct mallinfo.arena... '
checking for struct mallinfo.arena... + as_var=ac_cv_member_struct_mallinfo_arena
+ eval 'test "${ac_cv_member_struct_mallinfo_arena+set}" = set'
++ test '' = set
+ cat confdefs.h -
+ ac_fn_c_try_compile 1895
+ as_lineno=4245
+ as_lineno_stack=as_lineno_stack=as_lineno_stack=
+ rm -f conftest.o
+ ac_try='$CC -c $CFLAGS $CPPFLAGS conftest.$ac_ext >&5'
+ case "(($ac_try" in
+ ac_try_echo='$CC -c $CFLAGS $CPPFLAGS conftest.$ac_ext >&5'
+ eval 'ac_try_echo="$as_me:4245: $CC -c $CFLAGS $CPPFLAGS conftest.$ac_ext >&5"'
++ ac_try_echo='configure:4245: cc -c -g -O2  conftest.c >&5'
+ printf '%s\n' 'configure:4245: cc -c -g -O2  conftest.c >&5'
+ ac_status=0
+ test -s conftest.err
+ grep -v '^ *+' conftest.err
+ cat conftest.er1
+ mv -f conftest.er1 conftest.err
+ printf '%s\n' 'configure:4245: $? = 0'
+ test 0 = 0
+ test -z ''
+ test -s conftest.o
+ :
+ ac_retval=0
+ eval as_lineno_stack=as_lineno_stack=
++ as_lineno_stack=as_lineno_stack=
+ test xas_lineno_stack= = x
+ return 0
+ :
+ eval ac_cv_member_struct_mallinfo_arena=yes
++ ac_cv_member_struct_mallinfo_arena=yes
+ rm -f core conftest.err conftest.o conftest.c
+ eval 'ac_res=$ac_cv_member_struct_mallinfo_arena'
++ ac_res=yes
+ printf '%s\n' 'configure:4245: result: yes'
+ printf '%s\n' yes
yes
+ eval as_lineno_stack=
++ as_lineno_stack=
+ test x = x
+ as_lineno=
+ unset as_lineno
+ test xyes = xyes
+ :
+ printf '%s\n' '#define HAVE_MALLINFO 1'
+ set +x

```might help when it comes to nailing the problem down

---

### Post by dinxter on 2009-10-03
just to finally add, the malloc.h provided by libc6-dev 2.10.1-0ubuntu13 thats included in karmic does indeed have struct mallinfo and indeed mallinfo.arena so the above test should pass, as it does, and the define HAVE_MALLINFO  should indeed be inserted, as it is. so i dont know where the build process is going wrong

---

### Post by Miguel on 2009-10-03
That's a ton of useful info, thanks again. I'll make the best use I can of it.

---

