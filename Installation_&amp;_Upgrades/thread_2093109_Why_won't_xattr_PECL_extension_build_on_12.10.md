---
title: "Why won't xattr PECL extension build on 12.10?"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by dan000 on 2012-12-09
I was using the xattr pecl extension in 12.04 (in fact, I think since 10.04) without problem. Not surprisingly, I had to reinstall it after upgrading to 12.10 because of the new version of PHP.

But now it fails to build, and I can't figure out why. Other PECL extensions have built fine. And I have libattr1 and libattr1-dev installed.

Here's the output from the build:

```
downloading xattr-1.1.0.tgz ...
Starting to download xattr-1.1.0.tgz (5,204 bytes)
.....done: 5,204 bytes
3 source files, building
running: phpize
Configuring for:
PHP Api Version:         20100412
Zend Module Api No:      20100525
Zend Extension Api No:   220100525
libattr library installation dir? [autodetect] : building in /tmp/pear/temp/pear-build-rootdSMx0G/xattr-1.1.0
running: /tmp/pear/temp/xattr/configure --with-xattr
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
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
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20100525
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... re2c
checking for re2c version... 0.13.5 (ok)
checking for gawk... gawk
checking for xattr support... yes, shared
checking for xattr files in default path... found in /usr
checking for attr_get in -lattr... yes
checking how to print strings... printf
checking for a sed that does not truncate output... (cached) /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by cc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking for gawk... (cached) gawk
checking command to parse /usr/bin/nm -B output from cc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if cc supports -fno-rtti -fno-exceptions... no
checking for cc option to produce PIC... -fPIC -DPIC
checking if cc PIC flag -fPIC -DPIC works... yes
checking if cc static flag -static works... yes
checking if cc supports -c -o file.o... yes
checking if cc supports -c -o file.o... (cached) yes
checking whether the cc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating ./config.status
config.status: creating config.h
config.status: executing libtool commands
running: make
/bin/bash /tmp/pear/temp/pear-build-rootdSMx0G/xattr-1.1.0/libtool --mode=compile cc  -I. -I/tmp/pear/temp/xattr -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootdSMx0G/xattr-1.1.0/include -I/tmp/pear/temp/pear-build-rootdSMx0G/xattr-1.1.0/main -I/tmp/pear/temp/xattr -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/xattr/xattr.c -o xattr.lo
libtool: compile:  cc -I. -I/tmp/pear/temp/xattr -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootdSMx0G/xattr-1.1.0/include -I/tmp/pear/temp/pear-build-rootdSMx0G/xattr-1.1.0/main -I/tmp/pear/temp/xattr -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/xattr/xattr.c  -fPIC -DPIC -o .libs/xattr.o
/tmp/pear/temp/xattr/xattr.c:50:1: error: unknown type name 'function_entry'
/tmp/pear/temp/xattr/xattr.c:51:2: warning: braces around scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: (near initialization for 'xattr_functions[0]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: initialization makes integer from pointer without a cast [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: (near initialization for 'xattr_functions[0]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: error: initializer element is not computable at load time
/tmp/pear/temp/xattr/xattr.c:51:2: error: (near initialization for 'xattr_functions[0]')
/tmp/pear/temp/xattr/xattr.c:51:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: (near initialization for 'xattr_functions[0]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: (near initialization for 'xattr_functions[0]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: (near initialization for 'xattr_functions[0]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:51:2: warning: (near initialization for 'xattr_functions[0]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: braces around scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: (near initialization for 'xattr_functions[1]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: initialization makes integer from pointer without a cast [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: (near initialization for 'xattr_functions[1]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: error: initializer element is not computable at load time
/tmp/pear/temp/xattr/xattr.c:52:2: error: (near initialization for 'xattr_functions[1]')
/tmp/pear/temp/xattr/xattr.c:52:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: (near initialization for 'xattr_functions[1]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: (near initialization for 'xattr_functions[1]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: (near initialization for 'xattr_functions[1]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:52:2: warning: (near initialization for 'xattr_functions[1]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: braces around scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: (near initialization for 'xattr_functions[2]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: initialization makes integer from pointer without a cast [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: (near initialization for 'xattr_functions[2]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: error: initializer element is not computable at load time
/tmp/pear/temp/xattr/xattr.c:53:2: error: (near initialization for 'xattr_functions[2]')
/tmp/pear/temp/xattr/xattr.c:53:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: (near initialization for 'xattr_functions[2]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: (near initialization for 'xattr_functions[2]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: (near initialization for 'xattr_functions[2]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:53:2: warning: (near initialization for 'xattr_functions[2]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: braces around scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: (near initialization for 'xattr_functions[3]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: initialization makes integer from pointer without a cast [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: (near initialization for 'xattr_functions[3]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: error: initializer element is not computable at load time
/tmp/pear/temp/xattr/xattr.c:54:2: error: (near initialization for 'xattr_functions[3]')
/tmp/pear/temp/xattr/xattr.c:54:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: (near initialization for 'xattr_functions[3]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: (near initialization for 'xattr_functions[3]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: (near initialization for 'xattr_functions[3]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:54:2: warning: (near initialization for 'xattr_functions[3]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: braces around scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: (near initialization for 'xattr_functions[4]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: initialization makes integer from pointer without a cast [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: (near initialization for 'xattr_functions[4]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: error: initializer element is not computable at load time
/tmp/pear/temp/xattr/xattr.c:55:2: error: (near initialization for 'xattr_functions[4]')
/tmp/pear/temp/xattr/xattr.c:55:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: (near initialization for 'xattr_functions[4]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: (near initialization for 'xattr_functions[4]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: (near initialization for 'xattr_functions[4]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:55:2: warning: (near initialization for 'xattr_functions[4]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: braces around scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: (near initialization for 'xattr_functions[5]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: initialization makes integer from pointer without a cast [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: (near initialization for 'xattr_functions[5]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: (near initialization for 'xattr_functions[5]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: excess elements in scalar initializer [enabled by default]
/tmp/pear/temp/xattr/xattr.c:56:2: warning: (near initialization for 'xattr_functions[5]') [enabled by default]
/tmp/pear/temp/xattr/xattr.c:67:2: warning: initialization from incompatible pointer type [enabled by default]
/tmp/pear/temp/xattr/xattr.c:67:2: warning: (near initialization for 'xattr_module_entry.functions') [enabled by default]
/tmp/pear/temp/xattr/xattr.c: In function 'zif_xattr_set':
/tmp/pear/temp/xattr/xattr.c:122:49: error: 'struct _php_core_globals' has no member named 'safe_mode'
/tmp/pear/temp/xattr/xattr.c:122:92: error: 'CHECKUID_DISALLOW_FILE_NOT_EXISTS' undeclared (first use in this function)
/tmp/pear/temp/xattr/xattr.c:122:92: note: each undeclared identifier is reported only once for each function it appears in
/tmp/pear/temp/xattr/xattr.c: In function 'zif_xattr_get':
/tmp/pear/temp/xattr/xattr.c:171:49: error: 'struct _php_core_globals' has no member named 'safe_mode'
/tmp/pear/temp/xattr/xattr.c:171:92: error: 'CHECKUID_DISALLOW_FILE_NOT_EXISTS' undeclared (first use in this function)
/tmp/pear/temp/xattr/xattr.c:187:2: warning: passing argument 4 of 'attr_get' from incompatible pointer type [enabled by default]
In file included from /tmp/pear/temp/xattr/xattr.c:37:0:
/usr/include/attr/attributes.h:122:12: note: expected 'int *' but argument is of type 'size_t *'
/tmp/pear/temp/xattr/xattr.c:198:3: warning: passing argument 4 of 'attr_get' from incompatible pointer type [enabled by default]
In file included from /tmp/pear/temp/xattr/xattr.c:37:0:
/usr/include/attr/attributes.h:122:12: note: expected 'int *' but argument is of type 'size_t *'
/tmp/pear/temp/xattr/xattr.c: In function 'zif_xattr_supported':
/tmp/pear/temp/xattr/xattr.c:243:49: error: 'struct _php_core_globals' has no member named 'safe_mode'
/tmp/pear/temp/xattr/xattr.c:243:92: error: 'CHECKUID_DISALLOW_FILE_NOT_EXISTS' undeclared (first use in this function)
/tmp/pear/temp/xattr/xattr.c: In function 'zif_xattr_remove':
/tmp/pear/temp/xattr/xattr.c:288:49: error: 'struct _php_core_globals' has no member named 'safe_mode'
/tmp/pear/temp/xattr/xattr.c:288:92: error: 'CHECKUID_DISALLOW_FILE_NOT_EXISTS' undeclared (first use in this function)
/tmp/pear/temp/xattr/xattr.c: In function 'zif_xattr_list':
/tmp/pear/temp/xattr/xattr.c:337:49: error: 'struct _php_core_globals' has no member named 'safe_mode'
/tmp/pear/temp/xattr/xattr.c:337:92: error: 'CHECKUID_DISALLOW_FILE_NOT_EXISTS' undeclared (first use in this function)
make: *** [xattr.lo] Error 1
ERROR: `make' failed
```
There seem to be a few errors, but I can't make heads or tails of them.

Does this just not work properly in 12.10? That would be a big problem for me.

---

