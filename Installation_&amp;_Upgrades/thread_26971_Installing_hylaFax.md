---
title: "Installing hylaFax"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by Hasanudin on 2005-04-14
./configure

Configuring HylaFAX (tm) (aka FlexFAX) 4.2.1.

If configure does the wrong thing, check the file config.log for
information that may help you understand what went wrong.

Reading site-wide parameters from ./config.site.
Wow, you've got a i686-pc-linux-gnu system!
Using /usr/bin/gcc for a C compiler (set CC to override).
Looks like /usr/bin/gcc supports the -g option.
Using " -g" for C compiler options.
Looks like /usr/bin/gcc has an ANSI C preprocessor.
... but __ANSI_CPP__ is not automatically defined, will compensate.
Looks like /usr/bin/gcc supports the -M option for generating make dependencies.
Cannot locate a suitable C++ compiler.

We attempted to compile the following test program:

----------------------------------------------------------
class foo {
public:
    struct bar {
        int a;
        bar();
    };
    foo();
};
foo::bar::bar() { a = 0; }
foo::foo() { bar x; }
int main() { foo t; return 0; }
----------------------------------------------------------

with these compilers:

     g++ gcc CC NCC DCC gcc2 xlC

but none of them were successful.

To build this software you need a C++ compiler that supports a
reasonably modern version of C++.  In particular the compiler must
support nested types and process temporary variables according to the
ANSI Reference Manual (the ARM).

If such a compiler is in a non-standard location, you can specify its
location in several ways:

    o set the environment variable CXX
    o create a config.local or config.site file that includes a
      definition for CXX
    o supply it on the command line using -with-CXX=<pathname>

If you are trying to use GNU gcc, but you do not have version 2.6.1
or newer, then you must update your compiler (and probably libg++ as
well) before you can compile this software.  Consult the documentation
for information about obtaining an up-to-date version of gcc.

Unrecoverable error!  Once you've corrected the problem rerun this script.



===============

somebody help me? plz  :?

---

### Post by Hasanudin on 2005-04-15
[QUOTE=Hasanudin]./configure

Configuring HylaFAX (tm) (aka FlexFAX) 4.2.1.

If configure does the wrong thing, check the file config.log for
information that may help you understand what went wrong.

Reading site-wide parameters from ./config.site.
Wow, you've got a i686-pc-linux-gnu system!
Using /usr/bin/gcc for a C compiler (set CC to override).
Looks like /usr/bin/gcc supports the -g option.
Using " -g" for C compiler options.
Looks like /usr/bin/gcc has an ANSI C preprocessor.
... but __ANSI_CPP__ is not automatically defined, will compensate.
Looks like /usr/bin/gcc supports the -M option for generating make dependencies.
Cannot locate a suitable C++ compiler.

We attempted to compile the following test program:

----------------------------------------------------------
class foo {
public:
    struct bar {
        int a;
        bar();
    };
    foo();
};
foo::bar::bar() { a = 0; }
foo::foo() { bar x; }
int main() { foo t; return 0; }
----------------------------------------------------------

with these compilers:

     g++ gcc CC NCC DCC gcc2 xlC

but none of them were successful.

To build this software you need a C++ compiler that supports a
reasonably modern version of C++.  In particular the compiler must
support nested types and process temporary variables according to the
ANSI Reference Manual (the ARM).

If such a compiler is in a non-standard location, you can specify its
location in several ways:

    o set the environment variable CXX
    o create a config.local or config.site file that includes a
      definition for CXX
    o supply it on the command line using -with-CXX=<pathname>

If you are trying to use GNU gcc, but you do not have version 2.6.1
or newer, then you must update your compiler (and probably libg++ as
well) before you can compile this software.  Consult the documentation
for information about obtaining an up-to-date version of gcc.

Unrecoverable error!  Once you've corrected the problem rerun this script.



===============

somebody help me? plz  :?[/QUOTE]
 hello...?

---

### Post by McLogic on 2006-04-12
Did you make sure you have the compilers installed?

```

sudo apt-get install build-essential

```

Don't Panic!

:-k

---

### Post by fsloke on 2008-07-20
Ya McLogic,

You are correct...

Now I having next error...

> 
henry@ubuntu01:~/Desktop/hylafax-4.4.4$ ./configure

Configuring HylaFAX (tm) (aka FlexFAX) 4.4.4.

If configure does the wrong thing, check the file config.log for
information that may help you understand what went wrong.

Reading site-wide parameters from ./config.site.
Hmm, looks like a i686-pc-linux-gnu system.
Using /usr/bin/gcc for a C compiler (set CC to override).
Looks like /usr/bin/gcc supports the -g option.
... but not together with the -O option, not using it.
Looks like /usr/bin/gcc has an ANSI C preprocessor.
... but __ANSI_CPP__ is not automatically defined, will compensate.
Looks like /usr/bin/gcc supports the -M option for generating make dependencies.
Using /usr/bin/g++ for a C++ compiler (set CXX to override).
Looks like /usr/bin/g++ supports the -g option.
Using " -g" for C++ compiler options.
Looks like /usr/bin/g++ has an ANSI C preprocessor.
... but __ANSI_CPP__ is not automatically defined, will compensate.
Using /usr/bin/make to configure the software.
Using "include file" syntax for Makefiles.
Looks like make supports "sinclude" for conditional includes.
Using /bin/bash to process command scripts.
Checking for PAM (Pluggable Authentication Module) support
... not found. Disabling PAM support
Checking for JBIG library support
... not found. Disabling JBIG support
Looks like -lcrypt is needed for crypt.
Looks like -lutil is needed for wtmp file logging.

Creating port.h with necessary definitions.
... open FIFO files read+write to avoid select bug
... using call-by-reference for TIOCMBIS ioctl
... constrain client IDs to be <= 60002
... configure use of <stdint.h>
... configure use of <sys/select.h>
... use (sig_t) for sigaction handler type
... use (sig_t) for signal handler type
... configure use of mmap for memory-mapped files
... configure use of sysconf
... configure use of ulimit
... configure use of getdtablesize
... add #define for howmany
... configure use of fchown
... configure use of fchmod
... configure use of <locale.h> (internationalization support)
... configure use of <paths.h>
... configure use of logwtmp (BSD-style wtmp logging)
... configure use of logout (BSD-style utmp support)
... configure use of <utmp.h> (normal utmp interface)
... configure use of extended exit status in utmp
... configure use of POSIX realtime process control interface
... configure use of <crypt.h>
... checking TIFF library version

Missing TIFF Library.

Compilation of the following test program failed:

----------------------------------------------------------
#include <stdio.h>
#include "tiffio.h"
main()
{
    printf( "header_ver=%d lib_ver=%s", TIFFLIB_VERSION, TIFFGetVersion() );
    exit(0);
}
----------------------------------------------------------

TIFFINC=/usr/local/include
LIBTIFF=-L/usr/local/lib -ltiff

Verify that you have the TIFFINC and LIBTIFF configuration parameters
set correctly for your system (see above) and that any environment
variables are setup that are needed to locate a libtiff DSO at runtime
(e.g. LD_LIBRARY_PATH). Also be sure that any relative pathnames are
made relative to the top of the build area.

Unrecoverable error!  Once you've corrected the problem rerun this script.



I think this error cause by I not set the TIFFINC and LIBTIFF libarry yet...

Is it correct?

Thank

P/S: Life is learning curver... Don't panic!!!

---

### Post by fsloke on 2008-07-21
Forgot about this just use the Ubuntu Synaptic Package Manager to get all the HylaFax server and client without build it by yourself.

I also encounter a lot of error during the build and installation of HylaFax..

Now the problem is how can I test the server?

Haiz....

Thank

---

