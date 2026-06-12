---
title: "compiler errors from anyremote 4.4"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by dogscoff on 2008-04-02
Hi,

Having trouble compiling anyremote4.4 ( [http://anyremote.sourceforge.net/](http://anyremote.sourceforge.net/) ) on my gutsy64 system. the "configure" command works fine. The make command then kept throwing missing file errors at me until I downloaded lots of libraries from synaptic. Now however I have come across an error that google can't help me with. Here's the text:

**************************************************

matt@ubuntu:/tmp/anyremote-4.4$ make
Making all in src
make[1]: Entering directory `/tmp/anyremote-4.4/src'
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT atsend.o -MD -MP -MF .deps/atsend.Tpo -c -o atsend.o atsend.c
mv -f .deps/atsend.Tpo .deps/atsend.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT btio.o -MD -MP -MF .deps/btio.Tpo -c -o btio.o btio.c
mv -f .deps/btio.Tpo .deps/btio.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT cmds.o -MD -MP -MF .deps/cmds.Tpo -c -o cmds.o cmds.c
mv -f .deps/cmds.Tpo .deps/cmds.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT parse.o -MD -MP -MF .deps/parse.Tpo -c -o parse.o parse.c
mv -f .deps/parse.Tpo .deps/parse.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT utils.o -MD -MP -MF .deps/utils.Tpo -c -o utils.o utils.c
mv -f .deps/utils.Tpo .deps/utils.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT xemulate.o -MD -MP -MF .deps/xemulate.Tpo -c -o xemulate.o xemulate.c
mv -f .deps/xemulate.Tpo .deps/xemulate.Po
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.4\" -DPACKAGE_STRING=\"anyremote\ 4.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT conf.o -MD -MP -MF .deps/conf.Tpo -c -o conf.o conf.c
mv -f .deps/conf.Tpo .deps/conf.Po
gcc -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g   -o anyremote atsend.o btio.o main.o cmds.o parse.o utils.o xemulate.o conf.o -lbluetooth -lXtst 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[1]: *** [anyremote] Error 1
make[1]: Leaving directory `/tmp/anyremote-4.4/src'
make: *** [all-recursive] Error 1

**************************************************

All this is meaningless jargon to me. Can anyone help? What do I need to do to move forward?
I have to say this anyremote looks like great software but is a pig to get working...

---

### Post by dstew on 2008-04-02
Looks like there is a [Gnome anyremote Debian package here]("http://downloads.sourceforge.net/anyremote/ganyremote_2.7-2_all.deb?modtime=1205357988&big_mirror=0"). Did you try that, instead of compiling from source? Is anyremote available from synaptic?

---

### Post by liquid circuit on 2008-04-02
> gcc -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g   -o anyremote atsend.o btio.o main.o cmds.o parse.o utils.o xemulate.o conf.o -lbluetooth -**lXtst** 
/usr/bin/ld: cannot find -**lXtst**

Maybe you need lXtst?  A quick google search brought me to [http://ubuntuforums.org/showthread.php?t=161330]("http://ubuntuforums.org/showthread.php?t=161330").  Their suggestion was...
```
sudo aptitude install libxtst-dev
```

---

### Post by dogscoff on 2008-04-02
dstew: Thanks. I have that deb installed,I believe it's a gnome front end for anyremote that needs anyremote iteslf for it all to work.

 liquid: I'll try that and report back, thanks.

---

### Post by dogscoff on 2008-04-02
liquid: That got it, compiled and working. Well, compiled and doing _something_ ... The phone and PC are definitely talking via bluetooth.. .I just wish I knew what they were talking about.

---

