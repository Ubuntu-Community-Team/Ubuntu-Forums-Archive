---
title: "Trouble installing Ktaglib in LAMPP"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by bluIT on 2011-04-23
I have been racking my brains trying to install Ktaglib-0.2.0 (PHP Module) into my LAMPP installation. I have tried both using through the PECL command (sudo /opt/lampp/bin/pecl install channel://pecl.php.net/KTaglib-0.2.0.tgz). Also through the phpize, ./configure, make and Sudo make install method also and alwasy end with the same result

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ktaglib.so' - /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ktaglib.so: wrong ELF class: ELFCLASS64 in Unknown on line 0

Warning: PHP Startup: Unable to load dynamic library '/opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ktaglib.so' - /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ktaglib.so: wrong ELF class: ELFCLASS64 in Unknown on line 0
bogus test name tests/

```I have spent a couple of days on this and really getting under my skin. I have reinstalled libtools and updated automake, but to no  avail. Below is the output of the manual installation commands.

phpize

```
blu@blu-desktop:~/Desktop/KTaglib-0.2.0/KTaglib-0.2.0$ /opt/lampp/bin/phpize
Configuring for:
PHP Api Version:         20090626
Zend Module Api No:      20090626
Zend Extension Api No:   220090626
configure.in:150: warning: AC_CACHE_VAL(lt_prog_compiler_static_works, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
aclocal.m4:3555: AC_LIBTOOL_LINKER_OPTION is expanded from...
aclocal.m4:5493: _LT_AC_LANG_C_CONFIG is expanded from...
aclocal.m4:5492: AC_LIBTOOL_LANG_C_CONFIG is expanded from...
aclocal.m4:2972: AC_LIBTOOL_SETUP is expanded from...
aclocal.m4:2952: _AC_PROG_LIBTOOL is expanded from...
aclocal.m4:2915: AC_PROG_LIBTOOL is expanded from...
configure.in:150: the top level
configure.in:150: warning: AC_CACHE_VAL(lt_prog_compiler_pic_works, ...): suspicious cache-id, must contain _cv_ to be cached
aclocal.m4:3510: AC_LIBTOOL_COMPILER_OPTION is expanded from...
aclocal.m4:7620: AC_LIBTOOL_PROG_COMPILER_PIC is expanded from...
configure.in:150: warning: AC_CACHE_VAL(lt_prog_compiler_pic_works_CXX, ...): suspicious cache-id, must contain _cv_ to be cached
aclocal.m4:5606: _LT_AC_LANG_CXX_CONFIG is expanded from...
aclocal.m4:5605: AC_LIBTOOL_LANG_CXX_CONFIG is expanded from...
aclocal.m4:4641: _LT_AC_TAGCONFIG is expanded from...
configure.in:150: warning: AC_CACHE_VAL(lt_prog_compiler_static_works, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
aclocal.m4:3555: AC_LIBTOOL_LINKER_OPTION is expanded from...
aclocal.m4:5493: _LT_AC_LANG_C_CONFIG is expanded from...
aclocal.m4:5492: AC_LIBTOOL_LANG_C_CONFIG is expanded from...
aclocal.m4:2972: AC_LIBTOOL_SETUP is expanded from...
aclocal.m4:2952: _AC_PROG_LIBTOOL is expanded from...
aclocal.m4:2915: AC_PROG_LIBTOOL is expanded from...
configure.in:150: the top level
configure.in:150: warning: AC_CACHE_VAL(lt_prog_compiler_pic_works, ...): suspicious cache-id, must contain _cv_ to be cached
aclocal.m4:3510: AC_LIBTOOL_COMPILER_OPTION is expanded from...
aclocal.m4:7620: AC_LIBTOOL_PROG_COMPILER_PIC is expanded from...
configure.in:150: warning: AC_CACHE_VAL(lt_prog_compiler_pic_works_CXX, ...): suspicious cache-id, must contain _cv_ to be cached
aclocal.m4:5606: _LT_AC_LANG_CXX_CONFIG is expanded from...
aclocal.m4:5605: AC_LIBTOOL_LANG_CXX_CONFIG is expanded from...
aclocal.m4:4641: _LT_AC_TAGCONFIG is expanded from...

```
./configure --with-php-config=/opt/lampp/bin/php-config

```
blu@blu-desktop:~/Desktop/KTaglib-0.2.0/KTaglib-0.2.0$ ./configure --with-php-config=/opt/lampp/bin/php-config
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /opt/lampp
checking for PHP includes... -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib
checking for PHP extension directory... /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626
checking for PHP installed headers prefix... /opt/lampp/include/php
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking This extension requires the KDE TagLib Library version 1.4
      or above and a working pkg-config installation.... yes, shared
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for pkg-config... /usr/bin/pkg-config
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
checking taglib.h usability... yes
checking taglib.h presence... yes
checking for taglib.h... yes
checking fileref.h usability... yes
checking fileref.h presence... yes
checking for fileref.h... yes
checking tag.h usability... yes
checking tag.h presence... yes
checking for tag.h... yes
checking tstring.h usability... yes
checking tstring.h presence... yes
checking for tstring.h... yes
checking mpegfile.h usability... yes
checking mpegfile.h presence... yes
checking for mpegfile.h... yes
checking tfile.h usability... yes
checking tfile.h presence... yes
checking for tfile.h... yes
checking id3v1tag.h usability... yes
checking id3v1tag.h presence... yes
checking for id3v1tag.h... yes
checking id3v2tag.h usability... yes
checking id3v2tag.h presence... yes
checking for id3v2tag.h... yes
checking speexfile.h usability... yes
checking speexfile.h presence... yes
checking for speexfile.h... yes
checking vorbisfile.h usability... yes
checking vorbisfile.h presence... yes
checking for vorbisfile.h... yes
checking xiphcomment.h usability... yes
checking xiphcomment.h presence... yes
checking for xiphcomment.h... yes
checking for ld used by cc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from cc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if cc static flag  works... yes
checking if cc supports -fno-rtti -fno-exceptions... no
checking for cc option to produce PIC... -fPIC
checking if cc PIC flag -fPIC works... yes
checking if cc supports -c -o file.o... yes
checking whether the cc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no

creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
configure: creating ./config.status
config.status: creating config.h

```make

```
blu@blu-desktop:~/Desktop/KTaglib-0.2.0/KTaglib-0.2.0$ make
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib.cpp -o ktaglib.lo 
mkdir .libs
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib.cpp  -fPIC -DPIC -o .libs/ktaglib.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib.cpp:260: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp -o ktaglib_mpeg.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp  -fPIC -DPIC -o .libs/ktaglib_mpeg.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp: In function 'void zim_KTaglib_MPEG_File___construct(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp:46: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp:62: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp:73: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp: In function 'void zim_KTaglib_MPEG_File_getID3v1Tag(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp:86: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp: In function 'void zim_KTaglib_MPEG_File_getID3v2Tag(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg.cpp:119: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp -o ktaglib_tag.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp  -fPIC -DPIC -o .libs/ktaglib_tag.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setTitle(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:111: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setArtist(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:125: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setAlbum(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:139: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setComment(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:153: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setGenre(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:167: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setYear(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:180: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp: In function 'void zim_KTaglib_Tag_setTrack(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_tag.cpp:193: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v1_tag.cpp -o ktaglib_id3v1_tag.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v1_tag.cpp  -fPIC -DPIC -o .libs/ktaglib_id3v1_tag.o
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_tag.cpp -o ktaglib_id3v2_tag.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_tag.cpp  -fPIC -DPIC -o .libs/ktaglib_id3v2_tag.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_tag.cpp: In function 'void zim_KTaglib_ID3v2_Tag_addFrame(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_tag.cpp:77: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_frame.cpp -o ktaglib_id3v2_frame.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_frame.cpp  -fPIC -DPIC -o .libs/ktaglib_id3v2_frame.o
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp -o ktaglib_id3v2_attachedpictureframe.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp  -fPIC -DPIC -o .libs/ktaglib_id3v2_attachedpictureframe.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp: In function 'int attachedpicture_set_picture(TagLib::ID3v2::AttachedPictureFrame*, char*)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:47: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp: In function 'void zim_KTaglib_ID3v2_AttachedPictureFrame___construct(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:68: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp: In function 'void zim_KTaglib_ID3v2_AttachedPictureFrame_setPicture(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:89: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp: In function 'void zim_KTaglib_ID3v2_AttachedPictureFrame_setMimeType(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:124: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp: In function 'void zim_KTaglib_ID3v2_AttachedPictureFrame_setType(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:137: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp: In function 'void zim_KTaglib_ID3v2_AttachedPictureFrame_savePicture(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:163: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_attachedpictureframe.cpp:169: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp -o ktaglib_id3v2_commentsframe.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp  -fPIC -DPIC -o .libs/ktaglib_id3v2_commentsframe.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp: In function 'void zim_KTaglib_ID3v2_CommentsFrame___construct(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp:46: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp: In function 'void zim_KTaglib_ID3v2_CommentsFrame_setDescription(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp:94: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp: In function 'void zim_KTaglib_ID3v2_CommentsFrame_setText(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp:109: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp: In function 'void zim_KTaglib_ID3v2_CommentsFrame_setLanguage(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_id3v2_commentsframe.cpp:124: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg_audioproperties.cpp -o ktaglib_mpeg_audioproperties.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg_audioproperties.cpp  -fPIC -DPIC -o .libs/ktaglib_mpeg_audioproperties.o
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg_header.cpp -o ktaglib_mpeg_header.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_mpeg_header.cpp  -fPIC -DPIC -o .libs/ktaglib_mpeg_header.o
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp -o ktaglib_ogg_vorbis.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp  -fPIC -DPIC -o .libs/ktaglib_ogg_vorbis.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp: In function 'void zim_KTaglib_Ogg_Vorbis_File___construct(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp:45: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp:61: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp:75: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis.cpp:80: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis_audioproperties.cpp -o ktaglib_ogg_vorbis_audioproperties.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_vorbis_audioproperties.cpp  -fPIC -DPIC -o .libs/ktaglib_ogg_vorbis_audioproperties.o
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=compile g++  -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp -o ktaglib_ogg_tag.lo 
 g++ -I. -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib -DHAVE_CONFIG_H -g -O2 -c /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp  -fPIC -DPIC -o .libs/ktaglib_ogg_tag.o
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setTitle(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:54: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setArtist(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:81: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setAlbum(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:108: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setComment(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:135: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setGenre(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:162: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setTrack(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:188: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_setYear(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:214: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_addField(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:243: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_removeField(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:275: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_contains(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:297: warning: deprecated conversion from string constant to 'char*'
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp: In function 'void zim_KTaglib_Ogg_Tag_getField(int, zval*, zval**, zval*, int)':
/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/ktaglib_ogg_tag.cpp:319: warning: deprecated conversion from string constant to 'char*'
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=link cc -DPHP_ATOM_INC -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/include -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/main -I/home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0 -I/opt/lampp/include/php -I/opt/lampp/include/php/main -I/opt/lampp/include/php/TSRM -I/opt/lampp/include/php/Zend -I/opt/lampp/include/php/ext -I/opt/lampp/include/php/ext/date/lib -I/usr/include/taglib  -DHAVE_CONFIG_H  -g -O2   -o ktaglib.la -export-dynamic -avoid-version -prefer-pic -module -rpath /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/modules  ktaglib.lo ktaglib_mpeg.lo ktaglib_tag.lo ktaglib_id3v1_tag.lo ktaglib_id3v2_tag.lo ktaglib_id3v2_frame.lo ktaglib_id3v2_attachedpictureframe.lo ktaglib_id3v2_commentsframe.lo ktaglib_mpeg_audioproperties.lo ktaglib_mpeg_header.lo ktaglib_ogg_vorbis.lo ktaglib_ogg_vorbis_audioproperties.lo ktaglib_ogg_tag.lo -lstdc++ -ltag
cc -shared  .libs/ktaglib.o .libs/ktaglib_mpeg.o .libs/ktaglib_tag.o .libs/ktaglib_id3v1_tag.o .libs/ktaglib_id3v2_tag.o .libs/ktaglib_id3v2_frame.o .libs/ktaglib_id3v2_attachedpictureframe.o .libs/ktaglib_id3v2_commentsframe.o .libs/ktaglib_mpeg_audioproperties.o .libs/ktaglib_mpeg_header.o .libs/ktaglib_ogg_vorbis.o .libs/ktaglib_ogg_vorbis_audioproperties.o .libs/ktaglib_ogg_tag.o  -lstdc++ -ltag  -Wl,-soname -Wl,ktaglib.so -o .libs/ktaglib.so
creating ktaglib.la
(cd .libs && rm -f ktaglib.la && ln -s ../ktaglib.la ktaglib.la)
/bin/bash /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/libtool --mode=install cp ./ktaglib.la /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/modules
cp ./.libs/ktaglib.so /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/modules/ktaglib.so
cp ./.libs/ktaglib.lai /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/modules/ktaglib.la
PATH="$PATH:/sbin" ldconfig -n /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/modules
----------------------------------------------------------------------
Libraries have been installed in:
   /home/blu/Desktop/KTaglib-0.2.0/KTaglib-0.2.0/modules

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------

Build complete.
Don't forget to run 'make test'.
```
Any help would be greatly appreciated

---

