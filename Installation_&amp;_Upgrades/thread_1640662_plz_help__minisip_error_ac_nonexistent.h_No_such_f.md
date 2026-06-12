---
title: "plz help : minisip :error: ac_nonexistent.h: No such file or directory"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by sohail_linux on 2010-12-08
Hi everyone ,
I am trying to install minisip on ubuntu-9 server ,but when I run  configure error occurs ,as shown by the config.log, please help me ,  what am i missing ? I 'd be grateful.
 
  $ ./configure 
 
## --------- ##
## Platform. ##
## --------- ##
 
hostname = ubuntu
uname -m = x86_64
uname -r = 2.6.24-19-server
uname -s = Linux
uname -v = #1 SMP Wed Jun 18 14:44:47 UTC 2008
...
configure:3387: checking how to run the C preprocessor
configure:3427: gcc -E  conftest.c
configure:3433: $? = 0
configure:3464: gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:3470: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "libmutil"
| #define PACKAGE_TARNAME "libmutil"
| #define PACKAGE_VERSION "0.8.0"
| #define PACKAGE_STRING "libmutil 0.8.0"
| #define PACKAGE_BUGREPORT "Erik Eliasson "
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>

---

### Post by karthick87 on 2010-12-08
What is your gcc version?

```
gcc --v
```

---

### Post by sohail_linux on 2010-12-08
thanks karthik ,
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4) , and some more erros in log are :

./configure: line 7521: conftest.cpp: command not found
configure:7526: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "libmutil"
| #define PACKAGE_TARNAME "libmutil"
| #define PACKAGE_VERSION "0.8.0"
| #define PACKAGE_STRING "libmutil 0.8.0"
| #define PACKAGE_BUGREPORT "Erik Eliasson <eliasson@imit.kth.se>"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define PACKAGE "libmutil"
| #define VERSION "0.8.0"
| #define USE_STL
| #define HAVE_VERSION_H 1
| #define VERSION PACKAGE_VERSION_FULL
| #define PACKAGE_VERSION PACKAGE_VERSION_FULL
| #define PACKAGE_STRING PACKAGE_STRING_FULL
| /* end confdefs.h.  */
| #include <dlfcn.h>
.....

opt/minisip/trunk/libmutil/conftest.c:60: undefined reference to `shl_load'
collect2: ld returned 1 exit status
configure:11731: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "libmutil"
| #define PACKAGE_TARNAME "libmutil"
| #define PACKAGE_VERSION "0.8.0"
| #define PACKAGE_STRING "libmutil 0.8.0"
| #define PACKAGE_BUGREPORT "Erik Eliasson <eliasson@imit.kth.se>"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define PACKAGE "libmutil"
| #define VERSION "0.8.0"
| #define USE_STL
| #define HAVE_VERSION_H 1
| #define VERSION PACKAGE_VERSION_FULL
| #define PACKAGE_VERSION PACKAGE_VERSION_FULL
| #define PACKAGE_STRING PACKAGE_STRING_FULL
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| /* Define shl_load to an innocuous variant, in case <limits.h> declares shl_load.
|    For example, HP-UX 11i <limits.h> declares gettimeofday.  */
| #define shl_load innocuous_shl_load
| 
| /* System header to define __stub macros and hopefully few prototypes,
|     which can conflict with char shl_load (); below.
|     Prefer <limits.h> to <assert.h> if __STDC__ is defined, since
|     <limits.h> exists even on freestanding compilers.  */
| 
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 
| #undef shl_load
| 
| /* Override any GCC internal prototype to avoid an error.
|    Use char because int might match the return type of a GCC
|    builtin and then its argument prototype would still apply.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| char shl_load ();
| /* The GNU C library defines this for functions which it implements
|     to always fail with ENOSYS.  Some functions are actually named
|     something starting with __ and the normal name is an alias.  */
| #if defined __stub_shl_load || defined __stub___shl_load
| choke me
| #endif
| 
| int
| main ()
| {
| return shl_load ();
|   ;
|   return 0;
| }
..........................
I need your suggestion , i would be grateful

---

