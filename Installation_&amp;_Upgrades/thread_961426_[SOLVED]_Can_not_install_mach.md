---
title: "[SOLVED] Can not install mach"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by fdnj on 2008-10-28
Hello!

I am new to ubuntu and I am having problems to install a program called mach-1.0.16, which I need to use for genetic analysis. I downloaded the tar.gz and tried the make install command, but I get this:

fab@fab:/usr/local/src/mach-1.0.16$ make install
g++ -O2 -I./libsrc -I./mach1 -D__ZLIB_AVAILABLE__  -D_FILE_OFFSET_BITS=64  -o libsrc/FortranFormat.o -c libsrc/FortranFormat.cpp -DVERSION=\"1.0.16\"
In file included from libsrc/StringBasics.h:32,
                 from libsrc/FortranFormat.h:21,
                 from libsrc/FortranFormat.cpp:18:
libsrc/InputFile.h:29:18: error: zlib.h: No such file or directory
In file included from libsrc/StringBasics.h:32,
                 from libsrc/FortranFormat.h:21,
                 from libsrc/FortranFormat.cpp:18:
libsrc/InputFile.h:38: error: ‘gzFile’ does not name a type
libsrc/InputFile.h:70: error: ‘gzFile’ has not been declared
libsrc/InputFile.h: In member function ‘IFILE::operator void*()’:
libsrc/InputFile.h:51: error: ‘gzHandle’ was not declared in this scope
libsrc/InputFile.h: In member function ‘IFILE IFILE::operator=(const IFILE&)’:
libsrc/InputFile.h:56: error: ‘gzHandle’ was not declared in this scope
libsrc/InputFile.h:56: error: ‘const class IFILE’ has no member named ‘gzHandle’
libsrc/InputFile.h: In member function ‘IFILE IFILE::operator=(int&)’:
libsrc/InputFile.h:73: error: ‘gzHandle’ was not declared in this scope
libsrc/InputFile.h: In member function ‘bool IFILE::operator==(void*)’:
libsrc/InputFile.h:81: error: ‘gzHandle’ was not declared in this scope
libsrc/InputFile.h: In function ‘int ifclose(IFILE&)’:
libsrc/InputFile.h:89: error: ‘class IFILE’ has no member named ‘gzHandle’
libsrc/InputFile.h:89: error: ‘gzclose’ was not declared in this scope
libsrc/InputFile.h: In function ‘int ifgetc(IFILE&)’:
libsrc/InputFile.h:92: error: ‘class IFILE’ has no member named ‘gzHandle’
libsrc/InputFile.h:92: error: ‘gzgetc’ was not declared in this scope
libsrc/InputFile.h: In function ‘void ifrewind(IFILE&)’:
libsrc/InputFile.h:95: error: ‘class IFILE’ has no member named ‘gzHandle’
libsrc/InputFile.h:95: error: ‘gzrewind’ was not declared in this scope
libsrc/InputFile.h: In function ‘int ifeof(IFILE&)’:
libsrc/InputFile.h:98: error: ‘class IFILE’ has no member named ‘gzHandle’
libsrc/InputFile.h:98: error: ‘gzeof’ was not declared in this scope
make: *** [libsrc/FortranFormat.o] Error 1

Someone has an idea on how I could resolve this?

Thank you in advance, 

Fab.

---

### Post by fdnj on 2008-10-28
Hi!
It's ok , I solved it: it does not have to be unpacked, I used ./mach1 to start it... also I think this thread was in the wrong place. Sorry for this.
Fab.

---

