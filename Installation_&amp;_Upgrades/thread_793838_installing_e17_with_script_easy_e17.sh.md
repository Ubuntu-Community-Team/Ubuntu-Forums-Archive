---
title: "installing e17 with script easy_e17.sh"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by virtaava on 2008-05-14
Help installation hangs
to this error message
```
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/modules/engines/Makefile.am:3: required directory src/modules/engines/directfb does not exist
configure.in:1649: required file `src/modules/engines/directfb/Makefile.in' not found

```

---

### Post by Partyboi2 on 2008-05-14
probably easier to install the deb packages then compile. [[COLOR=Blue]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=546746") is a link to install the deb packages if you are interested. :)

---

### Post by virtaava on 2008-05-14
Right, first problem solved.

I had automake version 1.10 installed downgraded to version 1.9
Tried again and next error is down below, any help would be appreciated.

```

     
--------------------------------------------------------------------------------


--------------------------- Installing libraries (EFL) -------------------------
- imlib2 ..................... previously installed
- edb ........................ previously installed
- eet ........................ previously installed
- evas ....................... ok
- ecore ...................... ok
- efreet ..................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... SKIPPED
- engrave .................... ok
- etk ........................ ok
- etk_extra .................. ok
- ewl ........................ ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
if /bin/bash ../../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../..  -I../../../../src/lib -I../../../../src/lib -I../../../../src/bin -I../../../../src/bin -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include  -I/opt/e17/include  -Wall -MT ewl_range_test.lo -MD -MP -MF ".deps/ewl_range_test.Tpo" -c -o ewl_range_test.lo ewl_range_test.c; \
        then mv -f ".deps/ewl_range_test.Tpo" ".deps/ewl_range_test.Plo"; else rm -f ".deps/ewl_range_test.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../src/lib -I../../../../src/lib -I../../../../src/bin -I../../../../src/bin -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -Wall -MT ewl_range_test.lo -MD -MP -MF .deps/ewl_range_test.Tpo -c ewl_range_test.c  -fPIC -DPIC -o .libs/ewl_range_test.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../src/lib -I../../../../src/lib -I../../../../src/bin -I../../../../src/bin -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -Wall -MT ewl_range_test.lo -MD -MP -MF .deps/ewl_range_test.Tpo -c ewl_range_test.c -o ewl_range_test.o >/dev/null 2>&1
/bin/bash ../../../../libtool --tag=CC --mode=link gcc  -Wall  -L/opt/e17/lib -o ewl_range_test.la -rpath /opt/e17/lib/ewl/tests -module  -avoid-version ewl_range_test.lo ../../../../src/lib/libewl.la
gcc -shared  .libs/ewl_range_test.o  -Wl,--rpath -Wl,/home/virtaava/e17_cvs/e17/libs/ewl/src/lib/.libs -L/opt/e17/lib ../../../../src/lib/.libs/libewl.so  -Wl,-soname -Wl,ewl_range_test.so -o .libs/ewl_range_test.so
ar cru .libs/ewl_range_test.a  ewl_range_test.o
ranlib .libs/ewl_range_test.a
creating ewl_range_test.la
(cd .libs && rm -f ewl_range_test.la && ln -s ../ewl_range_test.la ewl_range_test.la)
make[5]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests/range'
Making all in reparent
make[5]: Entering directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests/reparent'
make[5]: *** No rule to make target `all'.  Stop.
make[5]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests/reparent'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl'
make: *** [all] Error 2
--------------------------------------------------------------------------------


```

---

### Post by Rui Pais on 2008-05-14
> **virtaava said:**
> Right, first problem solved.

I had automake version 1.10 installed downgraded to version 1.9
Tried again and next error is down below, any help would be appreciated.

```

     
--------------------------------------------------------------------------------


--------------------------- Installing libraries (EFL) -------------------------
- imlib2 ..................... previously installed
- edb ........................ previously installed
- eet ........................ previously installed
- evas ....................... ok
- ecore ...................... ok
- efreet ..................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... SKIPPED
- engrave .................... ok
- etk ........................ ok
- etk_extra .................. ok
- ewl ........................ ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
if /bin/bash ../../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../..  -I../../../../src/lib -I../../../../src/lib -I../../../../src/bin -I../../../../src/bin -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include  -I/opt/e17/include  -Wall -MT ewl_range_test.lo -MD -MP -MF ".deps/ewl_range_test.Tpo" -c -o ewl_range_test.lo ewl_range_test.c; \
        then mv -f ".deps/ewl_range_test.Tpo" ".deps/ewl_range_test.Plo"; else rm -f ".deps/ewl_range_test.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../src/lib -I../../../../src/lib -I../../../../src/bin -I../../../../src/bin -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -Wall -MT ewl_range_test.lo -MD -MP -MF .deps/ewl_range_test.Tpo -c ewl_range_test.c  -fPIC -DPIC -o .libs/ewl_range_test.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../src/lib -I../../../../src/lib -I../../../../src/bin -I../../../../src/bin -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -Wall -MT ewl_range_test.lo -MD -MP -MF .deps/ewl_range_test.Tpo -c ewl_range_test.c -o ewl_range_test.o >/dev/null 2>&1
/bin/bash ../../../../libtool --tag=CC --mode=link gcc  -Wall  -L/opt/e17/lib -o ewl_range_test.la -rpath /opt/e17/lib/ewl/tests -module  -avoid-version ewl_range_test.lo ../../../../src/lib/libewl.la
gcc -shared  .libs/ewl_range_test.o  -Wl,--rpath -Wl,/home/virtaava/e17_cvs/e17/libs/ewl/src/lib/.libs -L/opt/e17/lib ../../../../src/lib/.libs/libewl.so  -Wl,-soname -Wl,ewl_range_test.so -o .libs/ewl_range_test.so
ar cru .libs/ewl_range_test.a  ewl_range_test.o
ranlib .libs/ewl_range_test.a
creating ewl_range_test.la
(cd .libs && rm -f ewl_range_test.la && ln -s ../ewl_range_test.la ewl_range_test.la)
make[5]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests/range'
Making all in reparent
make[5]: Entering directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests/reparent'
make[5]: *** No rule to make target `all'.  Stop.
make[5]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests/reparent'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin/tests'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/virtaava/e17_cvs/e17/libs/ewl'
make: *** [all] Error 2
--------------------------------------------------------------------------------


```

Hi,
as Partyboi2 already mentioned, it's better to use my method to have e17 via easy_e17 script (my deb it's a sane wrapper for it... ). 
It's completely compatible with you existent (partial) e17 installation. 

Your issue looks a typical problem with incorrect paths (or it's ewl need of repetition again?...)
Again those are all solved by e17-cvs deb :)

---

