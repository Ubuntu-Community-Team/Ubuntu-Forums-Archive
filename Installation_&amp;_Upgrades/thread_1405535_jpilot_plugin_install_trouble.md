---
title: "jpilot plugin install trouble"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by rudygrabmore on 2010-02-12
I am using an x86-64 architecture machine, running 9.10.  I am working on getting my palm centro phone to sync up with jpilot.  Trying to install this plugin [http://sourceforge.net/projects/picsnvideos](http://sourceforge.net/projects/picsnvideos) so I can extract my picture files from the phone.  I tried to install from the .deb file using GDebi, but the .deb file is designed for i386, so that didn't work.  When compiling from the tarball I get this error:

configure:3675: error: cannot run /bin/bash ./config.sub

I've been using ubuntu since Dapper, but only learning what I need to get by, so please excuse my ignorance, but I don't know what to do next.  

Any advice would be much appreciated,  Thanks!

---

### Post by Satoru-san on 2010-02-12
I believe you need build essential in ubuntu, I guess the cd didn't have enough room to fit it and not very many people are going to install from source, and also people should only install from source as a last result.

So go ahead and apt-get install build-esential

---

### Post by rudygrabmore on 2010-02-13
Thank you for your reply, Satoru-san, but that didn't fix it.  I thought I had already done that, but sure enough, build-essential installed.  No change though, still the same error.  Below is the relevant output from the config.log file in the folder for the picsnvideos plugin:

## ----------- ##
## Core tests. ##
## ----------- ##

configure:1984: checking for a BSD-compatible install
configure:2040: result: /usr/bin/install -c
configure:2051: checking whether build environment is sane
configure:2094: result: yes
configure:2122: checking for a thread-safe mkdir -p
configure:2161: result: /bin/mkdir -p
configure:2174: checking for gawk
configure:2204: result: no
configure:2174: checking for mawk
configure:2190: found /usr/bin/mawk
configure:2201: result: mawk
configure:2212: checking whether make sets $(MAKE)
configure:2233: result: yes
configure:2474: checking for gcc
configure:2490: found /usr/bin/gcc
configure:2501: result: gcc
configure:2739: checking for C compiler version
configure:2746: gcc --version >&5
gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2749: $? = 0
configure:2756: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
configure:2759: $? = 0
configure:2766: gcc -V >&5
gcc: '-V' option must have argument
configure:2769: $? = 1
configure:2792: checking for C compiler default output file name
configure:2819: gcc    conftest.c  >&5
configure:2822: $? = 0
configure:2860: result: a.out
configure:2877: checking whether the C compiler works
configure:2887: ./a.out
configure:2890: $? = 0
configure:2907: result: yes
configure:2914: checking whether we are cross compiling
configure:2916: result: no
configure:2919: checking for suffix of executables
configure:2926: gcc -o conftest    conftest.c  >&5
configure:2929: $? = 0
configure:2953: result: 
configure:2959: checking for suffix of object files
configure:2985: gcc -c   conftest.c >&5
configure:2988: $? = 0
configure:3011: result: o
configure:3015: checking whether we are using the GNU C compiler
configure:3044: gcc -c   conftest.c >&5
configure:3050: $? = 0
configure:3067: result: yes
configure:3072: checking whether gcc accepts -g
configure:3102: gcc -c -g  conftest.c >&5
configure:3108: $? = 0
configure:3207: result: yes
configure:3224: checking for gcc option to accept ISO C89
configure:3298: gcc  -c -g -O2  conftest.c >&5
configure:3304: $? = 0
configure:3327: result: none needed
configure:3356: checking for style of include used by make
configure:3384: result: GNU
configure:3409: checking dependency style of gcc
configure:3500: result: gcc3
configure:3516: checking for library containing strerror
configure:3557: gcc -o conftest -g -O2   conftest.c  >&5
configure:3563: $? = 0
configure:3591: result: none required
configure:3675: error: cannot run /bin/bash ./config.sub










possibly relavent output:

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_c_compiler_gnu=yes
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_objext=o
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_make_make_set=yes
ac_cv_search_strerror='none required'
am_cv_CC_dependencies_compiler_type=gcc3

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/matt/jpilot-picsnvideos-0.2/missing --run aclocal-1.10'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/matt/jpilot-picsnvideos-0.2/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/matt/jpilot-picsnvideos-0.2/missing --run autoconf'
AUTOHEADER='${SHELL} /home/matt/jpilot-picsnvideos-0.2/missing --run autoheader'
AUTOMAKE='${SHELL} /home/matt/jpilot-picsnvideos-0.2/missing --run automake-1.10'
AWK='mawk'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2'
CPP=''
CPPFLAGS=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR='.deps'
DSYMUTIL=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
F77=''
FFLAGS=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LN_S=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/matt/jpilot-picsnvideos-0.2/missing --run makeinfo'
NMEDIT=''
OBJEXT='o'
PACKAGE='picsnvideos'
PACKAGE_BUGREPORT=''
PACKAGE_NAME='picsnvideos'
PACKAGE_STRING='picsnvideos 0.2'
PACKAGE_TARNAME='picsnvideos'
PACKAGE_VERSION='0.2'
PATH_SEPARATOR=':'
PILOT_FLAGS=''
PILOT_LIBS=''
PROGNAME=''
RANLIB=''
SED=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='0.2'
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_ct_F77=''
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build=''
build_alias=''
build_cpu=''
build_os=''
build_vendor=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host=''
host_alias=''
host_cpu=''
host_os=''
host_vendor=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/matt/jpilot-picsnvideos-0.2/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

---

