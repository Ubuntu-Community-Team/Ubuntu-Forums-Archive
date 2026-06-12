---
title: "C Compiler can't create executables"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by zzzakattack on 2010-10-04
Right now, I'm trying to make my own linux system, but i ran into a problem when I tried to install GCC on it.  I'm using my ubuntu system to configure and install it, but whenever I do this, I always get a "c compiler can't create executables".  I tried running commands to install build-essentials, gcc, g++, and other things, as well as updating my system.

Here is the config.log file I have:

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /tools/bin
PATH: /bin
PATH: /usr/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2429: checking build system type
configure:2443: result: i686-pc-linux-gnu
configure:2490: checking host system type
configure:2503: result: i686-pc-linux-gnu
configure:2523: checking target system type
configure:2536: result: i686-pc-linux-gnu
configure:2590: checking for a BSD-compatible install
configure:2658: result: /usr/bin/install -c
configure:2669: checking whether ln works
configure:2691: result: yes
configure:2695: checking whether ln -s works
configure:2699: result: yes
configure:2706: checking for a sed that does not truncate output
configure:2770: result: /bin/sed
configure:2779: checking for gawk
configure:2795: found /usr/bin/gawk
configure:2806: result: gawk
configure:4039: checking for gcc
configure:4066: result: i686-lfs-linux-gnu-gcc -B/tools/lib/
configure:4295: checking for C compiler version
configure:4304: i686-lfs-linux-gnu-gcc -B/tools/lib/ --version >&5
../gcc-4.5.1/configure: line 4306: i686-lfs-linux-gnu-gcc: command not found
configure:4315: $? = 127
configure:4304: i686-lfs-linux-gnu-gcc -B/tools/lib/ -v >&5
../gcc-4.5.1/configure: line 4306: i686-lfs-linux-gnu-gcc: command not found
configure:4315: $? = 127
configure:4304: i686-lfs-linux-gnu-gcc -B/tools/lib/ -V >&5
../gcc-4.5.1/configure: line 4306: i686-lfs-linux-gnu-gcc: command not found
configure:4315: $? = 127
configure:4304: i686-lfs-linux-gnu-gcc -B/tools/lib/ -qversion >&5
../gcc-4.5.1/configure: line 4306: i686-lfs-linux-gnu-gcc: command not found
configure:4315: $? = 127
configure:4335: checking for C compiler default output file name
configure:4357: i686-lfs-linux-gnu-gcc -B/tools/lib/    conftest.c  >&5
../gcc-4.5.1/configure: line 4359: i686-lfs-linux-gnu-gcc: command not found
configure:4361: $? = 127
configure:4398: result: 
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:4404: error: in `/mnt/lfs/sources/gcc-build':
configure:4408: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_env_AR_FOR_TARGET_set=
ac_cv_env_AR_FOR_TARGET_value=
ac_cv_env_AR_set=set
ac_cv_env_AR_value=i686-lfs-linux-gnu-ar
ac_cv_env_AS_FOR_TARGET_set=
ac_cv_env_AS_FOR_TARGET_value=
ac_cv_env_AS_set=
ac_cv_env_AS_value=
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_FOR_TARGET_set=
ac_cv_env_CC_FOR_TARGET_value=
ac_cv_env_CC_set=set
ac_cv_env_CC_value='i686-lfs-linux-gnu-gcc -B/tools/lib/'
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_FOR_TARGET_set=
ac_cv_env_CXX_FOR_TARGET_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DLLTOOL_FOR_TARGET_set=
ac_cv_env_DLLTOOL_FOR_TARGET_value=
ac_cv_env_DLLTOOL_set=
ac_cv_env_DLLTOOL_value=
ac_cv_env_GCC_FOR_TARGET_set=
ac_cv_env_GCC_FOR_TARGET_value=
ac_cv_env_GCJ_FOR_TARGET_set=
ac_cv_env_GCJ_FOR_TARGET_value=
ac_cv_env_GFORTRAN_FOR_TARGET_set=
ac_cv_env_GFORTRAN_FOR_TARGET_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LD_FOR_TARGET_set=
ac_cv_env_LD_FOR_TARGET_value=
ac_cv_env_LD_set=
ac_cv_env_LD_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_LIPO_FOR_TARGET_set=
ac_cv_env_LIPO_FOR_TARGET_value=
ac_cv_env_LIPO_set=
ac_cv_env_LIPO_value=
ac_cv_env_NM_FOR_TARGET_set=
ac_cv_env_NM_FOR_TARGET_value=
ac_cv_env_NM_set=
ac_cv_env_NM_value=
ac_cv_env_OBJCOPY_set=
ac_cv_env_OBJCOPY_value=
ac_cv_env_OBJDUMP_FOR_TARGET_set=
ac_cv_env_OBJDUMP_FOR_TARGET_value=
ac_cv_env_OBJDUMP_set=
ac_cv_env_OBJDUMP_value=
ac_cv_env_RANLIB_FOR_TARGET_set=
ac_cv_env_RANLIB_FOR_TARGET_value=
ac_cv_env_RANLIB_set=set
ac_cv_env_RANLIB_value=i686-lfs-linux-gnu-ranlib
ac_cv_env_STRIP_FOR_TARGET_set=
ac_cv_env_STRIP_FOR_TARGET_value=
ac_cv_env_STRIP_set=
ac_cv_env_STRIP_value=
ac_cv_env_WINDMC_FOR_TARGET_set=
ac_cv_env_WINDMC_FOR_TARGET_value=
ac_cv_env_WINDMC_set=
ac_cv_env_WINDMC_value=
ac_cv_env_WINDRES_FOR_TARGET_set=
ac_cv_env_WINDRES_FOR_TARGET_value=
ac_cv_env_WINDRES_set=
ac_cv_env_WINDRES_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnu
ac_cv_path_SED=/bin/sed
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=gawk
ac_cv_prog_ac_ct_CC='i686-lfs-linux-gnu-gcc -B/tools/lib/'
ac_cv_target=i686-pc-linux-gnu
acx_cv_prog_LN=ln

## ----------------- ##
## Output variables. ##
## ----------------- ##

AR='i686-lfs-linux-gnu-ar'
AR_FOR_BUILD='$(AR)'
AR_FOR_TARGET=''
AS=''
AS_FOR_BUILD='$(AS)'
AS_FOR_TARGET=''
AWK='gawk'
BISON=''
BUILD_CONFIG=''
CC='i686-lfs-linux-gnu-gcc -B/tools/lib/'
CC_FOR_BUILD='$(CC)'
CC_FOR_TARGET=''
CFLAGS=''
CFLAGS_FOR_BUILD=''
CFLAGS_FOR_TARGET=''
COMPILER_AS_FOR_TARGET=''
COMPILER_LD_FOR_TARGET=''
COMPILER_NM_FOR_TARGET=''
CONFIGURE_GDB_TK=''
CPP=''
CPPFLAGS=''
CXX=''
CXXFLAGS=''
CXXFLAGS_FOR_BUILD=''
CXXFLAGS_FOR_TARGET=''
CXX_FOR_BUILD='$(CXX)'
CXX_FOR_TARGET=''
DEBUG_PREFIX_CFLAGS_FOR_TARGET=''
DEFS=''
DLLTOOL=''
DLLTOOL_FOR_BUILD='$(DLLTOOL)'
DLLTOOL_FOR_TARGET=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
EXPECT=''
FLAGS_FOR_TARGET=''
FLEX=''
GCC_FOR_TARGET=''
GCC_SHLIB_SUBDIR=''
GCJ_FOR_BUILD='$(GCJ)'
GCJ_FOR_TARGET=''
GDB_TK=''
GFORTRAN_FOR_BUILD='$(GFORTRAN)'
GFORTRAN_FOR_TARGET=''
GNATBIND=''
GNATMAKE=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_GDB_TK=''
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
LD=''
LDFLAGS=''
LDFLAGS_FOR_BUILD=''
LD_FOR_BUILD='$(LD)'
LD_FOR_TARGET=''
LEX=''
LIBOBJS=''
LIBS=''
LIPO=''
LIPO_FOR_TARGET=''
LN='ln'
LN_S='ln -s'
LTLIBOBJS=''
M4=''
MAINT=''
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE=''
MAKEINFO=''
NM=''
NM_FOR_BUILD='$(NM)'
NM_FOR_TARGET=''
OBJCOPY=''
OBJDUMP=''
OBJDUMP_FOR_TARGET=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_URL=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
RANLIB='i686-lfs-linux-gnu-ranlib'
RANLIB_FOR_BUILD='$(RANLIB)'
RANLIB_FOR_TARGET=''
RAW_CXX_FOR_TARGET=''
RPATH_ENVVAR=''
RUNTEST=''
SED='/bin/sed'
SHELL='/bin/bash'
STRIP=''
STRIP_FOR_TARGET=''
SYSROOT_CFLAGS_FOR_TARGET=''
TOPLEVEL_CONFIGURE_ARGUMENTS='../gcc-4.5.1/configure --prefix=/tools --with-local-prefix=/tools --enable-clocale=gnu --enable-shared --enable-threads=posix --enable-__cxa_atexit --enable-languages=c,c++ --disable-libstdcxx-pch --disable-multilib --disable-bootstrap --disable-libgomp --with-gmp-include=/mnt/lfs/sources/gcc-build/gmp --with-gmp-lib=/mnt/lfs/sources/gcc-build/gmp/.libs --without-ppl --without-cloog'
WINDMC=''
WINDMC_FOR_BUILD='$(WINDMC)'
WINDMC_FOR_TARGET=''
WINDRES=''
WINDRES_FOR_BUILD='$(WINDRES)'
WINDRES_FOR_TARGET=''
YACC=''
ac_ct_CC='i686-lfs-linux-gnu-gcc -B/tools/lib/'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_configargs=''
build_configdirs='build-libiberty build-texinfo build-byacc build-flex build-bison build-m4 build-fixincludes'
build_cpu='i686'
build_libsubdir='build-i686-pc-linux-gnu'
build_noncanonical='i686-pc-linux-gnu'
build_os='linux-gnu'
build_subdir='build-i686-pc-linux-gnu'
build_tooldir=''
build_vendor='pc'
clooginc=''
clooglibs=''
compare_exclusions=''
config_shell='/bin/bash'
configdirs='intl mmalloc libiberty opcodes bfd readline tcl tk itcl libgui zlib libcpp libdecnumber gmp mpfr mpc ppl cloog libelf libiconv texinfo byacc flex bison binutils gas ld fixincludes gcc cgen sid sim gdb make patch prms send-pr gprof etc expect dejagnu ash bash bzip2 m4 autoconf automake libtool diff rcs fileutils shellutils time textutils wdiff find uudecode hello tar gzip indent recode release sed utils guile perl gawk findutils gettext zip fastjar gnattools'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
do_compare=''
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
extra_host_libiberty_configure_flags=''
extra_mpc_gmp_configure_flags=''
extra_mpc_mpfr_configure_flags=''
extra_mpfr_configure_flags=''
gmpinc=''
gmplibs=''
host='i686-pc-linux-gnu'
host_alias=''
host_configargs=''
host_cpu='i686'
host_noncanonical='i686-pc-linux-gnu'
host_os='linux-gnu'
host_subdir='.'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libelfinc=''
libelflibs=''
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
poststage1_ldflags=''
poststage1_libs=''
pplinc=''
ppllibs=''
prefix='/tools'
program_transform_name='s,y,y,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
stage1_cflags=''
stage1_checking=''
stage1_languages=''
stage1_ldflags=''
stage1_libs=''
stage2_werror_flag=''
sysconfdir='${prefix}/etc'
target='i686-pc-linux-gnu'
target_alias=''
target_configargs=''
target_configdirs='target-libgcc target-libiberty target-libgloss target-newlib target-libgomp target-libstdc++-v3 target-libmudflap target-libssp target-libgfortran target-boehm-gc target-libffi target-zlib target-qthreads target-libjava target-libobjc target-libada target-examples target-groff target-gperf target-rda'
target_cpu='i686'
target_noncanonical='i686-pc-linux-gnu'
target_os='linux-gnu'
target_subdir='i686-pc-linux-gnu'
target_vendor='pc'
tooldir=''

## ------------------- ##
## File substitutions. ##
## ------------------- ##

alphaieee_frag=''
host_makefile_frag='config/mh-x86omitfp'
ospace_frag=''
serialization_dependencies=''
target_makefile_frag=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PACKAGE_URL ""

configure: exit 77

Any suggestions on how to fix this?
Thanks.

---

### Post by andrewthomas on 2010-10-04
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by zzzakattack on 2010-10-04
> **andrewthomas said:**
> [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

This is how I'm attempting to make the linux, but even while thoroughly following the directions (more than once), I'm still have troubles.

The config.log that I posted was actually created using the instructions from Linux From Scratch.

---

### Post by andrewthomas on 2010-10-04
You will probably have better luck here.

[http://www.linuxquestions.org/questions/linux-from-scratch-13/](http://www.linuxquestions.org/questions/linux-from-scratch-13/)


Build-essential is a debian meta-package which is not something that is relevant to LFS.

---

### Post by zzzakattack on 2010-10-07
I couldn't figure out what I was doing wrong (probably some messed up configuration I did after messing with my computer so much!), but I found a solution:
I just downloaded the Linux From Scratch Live CD and ran it in Virtual Box.  So far, it seems to be working really well, and I'm surprised I didn't think of this before!

Thanks again for the help!

---

