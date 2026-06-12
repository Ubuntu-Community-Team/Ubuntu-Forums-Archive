---
title: "TCL installation problems"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by theguruvenkat on 2010-09-04
Hi everybody...

I have an ubuntu 10.04 system. I have been trying to install tcl with non-thread enabled for some other software. If I install tcl from synatptic or use activetcl, then it gets installed with thread enabled option. 

So I thought that I have to compile tcl from source. So i downloaded tcl8.5.8-src.tar.gz file of tcl and extracted it in a folder.I then entered the /unix folder and i ran ./configure --disable-threads and got this output:

checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for inline... inline
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking dirent.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking if the compiler understands -pipe... yes
checking for building with threads... no (default)
checking for sin... no
checking for main in -lieee... yes
checking for main in -linet... no
checking net/errno.h usability... no
checking net/errno.h presence... no
checking for net/errno.h... no
checking for connect... yes
checking for gethostbyname... yes
checking how to build libraries... shared
checking for ranlib... ranlib
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking if compiler supports visibility "hidden"... yes
checking if rpath support is requested... yes
checking system version... Linux-2.6.32-24-generic
checking for dlopen in -ldl... yes
checking for ar... ar
checking for build with symbols... no
checking for required early compiler flags...  _LARGEFILE64_SOURCE
checking for 64-bit integer type... long long
checking for struct dirent64... no
checking for struct stat64... yes
checking for open64... yes
checking for lseek64... yes
checking for off64_t... yes
checking whether byte ordering is bigendian... no
checking for getcwd... yes
checking for opendir... yes
checking for strtol... yes
checking for waitpid... yes
checking for strerror... yes
checking for getwd... yes
checking for wait3... yes
checking for uname... yes
checking for realpath... yes
checking for getaddrinfo... yes
checking for working getaddrinfo... yes
checking sys/modem.h usability... no
checking sys/modem.h presence... no
checking for sys/modem.h... no
checking termios vs. termio vs. sgtty... termios
checking for fd_set in sys/types... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for struct tm.tm_zone... yes
checking for gmtime_r... yes
checking for localtime_r... yes
checking for mktime... yes
checking tm_tzadj in struct tm... no
checking tm_gmtoff in struct tm... yes
checking long timezone variable... yes
checking for struct stat.st_blksize... yes
checking for fstatfs... yes
checking for working memcmp... yes
checking for memmove... yes
checking for strstr... yes
checking proper strstr implementation... ok
checking for strtoul... yes
checking proper strtoul implementation... ok
checking for strtod... yes
checking proper strtod implementation... ok
checking for strtod... (cached) yes
checking for Solaris2.4/Tru64 strtod bugs... ok
checking for mode_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for socklen_t... yes
checking for intptr_t... yes
checking for uintptr_t... yes
checking for opendir... (cached) yes
checking union wait... yes
checking for strncasecmp... yes
checking for BSDgettimeofday... no
checking for gettimeofday... yes
checking for gettimeofday declaration... present
checking whether char is unsigned... no
checking signed char declarations... yes
checking for a putenv() that copies the buffer... no
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking whether to use nl_langinfo... yes
checking for chflags... no
checking isnan... yes
checking for fts... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking system version... (cached) Linux-2.6.32-24-generic
checking FIONBIO vs. O_NONBLOCK for nonblocking I/O... O_NONBLOCK
checking whether to use dll unloading... yes
checking for timezone data... /usr/share/zoneinfo
checking whether to enable DTrace support... no
checking if the C stack grows upwards in memory... no
configure: creating ./config.status
./config.status: line 305: stuff/IIT_M/tcl8.5.8/unix: No such file or directory
config.status: creating Makefile
config.status: creating dltest/Makefile
config.status: creating tclConfig.sh


I then did sudo make and got:

make: *** No rule to make target `/../unix/Makefile.in', needed by `Makefile'.  Stop.


Please Help!!!!!

---

### Post by theguruvenkat on 2010-09-04
Some help is very much needed guys...please reply

Thanks in advance

---

