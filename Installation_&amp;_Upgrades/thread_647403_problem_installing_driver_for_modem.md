---
title: "problem installing driver for modem"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by ismailsrt4400 on 2007-12-22
hi all 
im new in this forum and i have install ubuntu but i have a problem in installing driver for the dialup modems this is the error:
ismailsrt4400@ismailsrt4400-laptop:~/m/slmodem-2.9.10$ make
make -C modem all
make[1]: entrant dans le répertoire « /home/ismailsrt4400/m/slmodem-2.9.10/modem »
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
modem_main.c:45:20: erreur: unistd.h : Aucun fichier ou répertoire de ce type
modem_main.c:46:20: erreur: stdlib.h : Aucun fichier ou répertoire de ce type
modem_main.c:47:19: erreur: stdio.h : Aucun fichier ou répertoire de ce type
modem_main.c:48:20: erreur: string.h : Aucun fichier ou répertoire de ce type
modem_main.c:49:19: erreur: errno.h : Aucun fichier ou répertoire de ce type
modem_main.c:50:21: erreur: termios.h : Aucun fichier ou répertoire de ce type
modem_main.c:51:19: erreur: fcntl.h : Aucun fichier ou répertoire de ce type
modem_main.c:52:23: erreur: sys/types.h : Aucun fichier ou répertoire de ce type
modem_main.c:53:22: erreur: sys/stat.h : Aucun fichier ou répertoire de ce type
modem_main.c:54:23: erreur: sys/ioctl.h : Aucun fichier ou répertoire de ce type
modem_main.c:55:22: erreur: sys/mman.h : Aucun fichier ou répertoire de ce type
modem_main.c:56:19: erreur: sched.h : Aucun fichier ou répertoire de ce type
modem_main.c:57:20: erreur: signal.h : Aucun fichier ou répertoire de ce type
Dans le fichier inclus à partir de /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
          à partir de /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
          à partir de modem_main.c:58:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: erreur: limits.h : Aucun fichier ou répertoire de ce type
modem_main.c:59:17: erreur: grp.h : Aucun fichier ou répertoire de ce type
In file included from ./modem.h:49,
                 from modem_main.c:67:
./modem_defs.h:50: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «u8"
./modem_defs.h:51: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «u16"
./modem_defs.h:52: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «u32"
./modem_defs.h:54: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «s8"
./modem_defs.h:55: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «s16"
./modem_defs.h:56: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «s32"
In file included from ./modem.h:50,
                 from modem_main.c:67:
./modem_homolog.h:53: erreur: expected specifier-qualifier-list before «u8"
./modem_homolog.h:103: erreur: expected «:", «,", «;", «}" or «__attribute__" before «id"
In file included from ./modem.h:51,
                 from modem_main.c:67:
./modem_dp.h:82: erreur: expected declaration specifiers or «..." before «u8"
./modem_dp.h:83: erreur: expected declaration specifiers or «..." before «u8"
In file included from modem_main.c:67:
./modem.h:138: erreur: expected specifier-qualifier-list before «u16"
./modem.h:174: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:175: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:191: erreur: expected specifier-qualifier-list before «u16"
./modem.h:219: erreur: expected specifier-qualifier-list before «u8"
./modem.h:263: erreur: field «termios" has incomplete type
./modem.h:319: erreur: expected specifier-qualifier-list before «u8"
./modem.h:340: erreur: expected specifier-qualifier-list before «u32"
./modem.h:342: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:343: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:354: erreur: expected specifier-qualifier-list before «u8"
./modem.h:371: erreur: expected specifier-qualifier-list before «u8"
./modem.h:436: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:437: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:439: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:440: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:442: erreur: expected declaration specifiers or «..." before «u8"
./modem.h:443: erreur: expected declaration specifiers or «..." before «u8"
modem_main.c:94: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «modem_perm"
modem_main.c: In function «modemap_start":
modem_main.c:470: attention : implicit declaration of function «ioctl"
modem_main.c:474: attention : implicit declaration of function «memset"
modem_main.c:474: attention : incompatible implicit declaration of built-in function «memset"
modem_main.c:475: attention : implicit declaration of function «write"
modem_main.c: In function «mdm_device_read":
modem_main.c:517: attention : implicit declaration of function «read"
modem_main.c: In function «mdm_device_setup":
modem_main.c:531: erreur: storage size of «stbuf" isn"t known
modem_main.c:533: attention : incompatible implicit declaration of built-in function «memset"
modem_main.c:534: attention : implicit declaration of function «stat"
modem_main.c:536: attention : implicit declaration of function «fprintf"
modem_main.c:536: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:536: erreur: «stderr" undeclared (first use in this function)
modem_main.c:536: erreur: (Each undeclared identifier is reported only once
modem_main.c:536: erreur: for each function it appears in.)
modem_main.c:536: attention : implicit declaration of function «strerror"
modem_main.c:536: erreur: «errno" undeclared (first use in this function)
modem_main.c:536: attention : format «%s" expects type «char *", but argument 4 has type «int"
modem_main.c:539: attention : implicit declaration of function «S_ISCHR"
modem_main.c:540: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:544: attention : implicit declaration of function «open"
modem_main.c:544: erreur: «O_RDWR" undeclared (first use in this function)
modem_main.c:546: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:546: attention : format «%s" expects type «char *", but argument 4 has type «int"
modem_main.c:550: attention : implicit declaration of function «minor"
modem_main.c:531: attention : unused variable «stbuf"
modem_main.c: In function «mdm_device_release":
modem_main.c:556: attention : implicit declaration of function «close"
modem_main.c: Hors de toute fonction :
modem_main.c:566: erreur: «PATH_MAX" undeclared here (not in a function)
modem_main.c: In function «create_pty":
modem_main.c:570: erreur: storage size of «termios" isn"t known
modem_main.c:577: attention : implicit declaration of function «getpt"
modem_main.c:578: attention : implicit declaration of function «grantpt"
modem_main.c:578: attention : implicit declaration of function «unlockpt"
modem_main.c:579: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:579: erreur: «stderr" undeclared (first use in this function)
modem_main.c:579: erreur: «errno" undeclared (first use in this function)
modem_main.c:579: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:587: attention : implicit declaration of function «tcgetattr"
modem_main.c:589: attention : implicit declaration of function «cfmakeraw"
modem_main.c:590: attention : implicit declaration of function «cfsetispeed"
modem_main.c:590: erreur: «B115200" undeclared (first use in this function)
modem_main.c:591: attention : implicit declaration of function «cfsetospeed"
modem_main.c:594: attention : implicit declaration of function «tcsetattr"
modem_main.c:594: erreur: «TCSANOW" undeclared (first use in this function)
modem_main.c:596: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:596: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:600: attention : implicit declaration of function «fcntl"
modem_main.c:600: erreur: «F_SETFL" undeclared (first use in this function)
modem_main.c:600: erreur: «O_NONBLOCK" undeclared (first use in this function)
modem_main.c:602: attention : implicit declaration of function «ptsname"
modem_main.c:602: attention : assignment makes pointer from integer without a cast
modem_main.c:610: attention : implicit declaration of function «getgrnam"
modem_main.c:610: attention : initialization makes pointer from integer without a cast
modem_main.c:612: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:612: attention : format «%s" expects type «char *", but argument 4 has type «int"
modem_main.c:616: attention : implicit declaration of function «chown"
modem_main.c:616: erreur: déréférencement d'un pointeur de type incomplet
modem_main.c:618: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:618: attention : format «%s" expects type «char *", but argument 5 has type «int"
modem_main.c:624: attention : implicit declaration of function «chmod"
modem_main.c:624: erreur: «modem_perm" undeclared (first use in this function)
modem_main.c:626: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:626: attention : format «%s" expects type «char *", but argument 5 has type «int"
modem_main.c:631: attention : implicit declaration of function «unlink"
modem_main.c:632: attention : implicit declaration of function «symlink"
modem_main.c:633: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:633: attention : format «%s" expects type «char *", but argument 5 has type «int"
modem_main.c:638: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:570: attention : unused variable «termios"
modem_main.c: Hors de toute fonction :
modem_main.c:658: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «keep_running"
modem_main.c: In function «mark_termination":
modem_main.c:663: erreur: «keep_running" undeclared (first use in this function)
modem_main.c: In function «modem_run":
modem_main.c:669: erreur: storage size of «tmo" isn"t known
modem_main.c:670: erreur: «fd_set" undeclared (first use in this function)
modem_main.c:670: erreur: expected «;" before «rset"
modem_main.c:671: erreur: storage size of «termios" isn"t known
modem_main.c:677: erreur: «keep_running" undeclared (first use in this function)
modem_main.c:691: attention : implicit declaration of function «FD_ZERO"
modem_main.c:691: erreur: «rset" undeclared (first use in this function)
modem_main.c:692: erreur: «eset" undeclared (first use in this function)
modem_main.c:694: attention : implicit declaration of function «FD_SET"
modem_main.c:709: attention : implicit declaration of function «select"
modem_main.c:709: erreur: «NULL" undeclared (first use in this function)
modem_main.c:712: erreur: «errno" undeclared (first use in this function)
modem_main.c:712: erreur: «EINTR" undeclared (first use in this function)
modem_main.c:714: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:714: erreur: «stderr" undeclared (first use in this function)
modem_main.c:714: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:721: attention : implicit declaration of function «FD_ISSET"
modem_main.c:732: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:732: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:742: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:742: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:767: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:767: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:776: attention : incompatible implicit declaration of built-in function «memset"
modem_main.c:779: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:779: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:783: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:794: attention : implicit declaration of function «memcmp"
modem_main.c:806: erreur: «EAGAIN" undeclared (first use in this function)
modem_main.c:810: erreur: «EIO" undeclared (first use in this function)
modem_main.c:813: erreur: «HUPCL" undeclared (first use in this function)
modem_main.c:818: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:830: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:830: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:839: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:671: attention : unused variable «termios"
modem_main.c:669: attention : unused variable «tmo"
modem_main.c: In function «modem_main":
modem_main.c:857: attention : implicit declaration of function «basename"
modem_main.c:857: attention : passing argument 1 of «modem_debug_init" makes pointer from integer without a cast
modem_main.c:861: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:861: erreur: «stderr" undeclared (first use in this function)
modem_main.c:862: attention : implicit declaration of function «exit"
modem_main.c:862: attention : incompatible implicit declaration of built-in function «exit"
modem_main.c:870: attention : implicit declaration of function «sprintf"
modem_main.c:870: attention : incompatible implicit declaration of built-in function «sprintf"
modem_main.c:872: attention : passing argument 2 of «modem_create" makes pointer from integer without a cast
modem_main.c:873: attention : assignment makes pointer from integer without a cast
modem_main.c:879: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:880: attention : incompatible implicit declaration of built-in function «exit"
modem_main.c:883: attention : incompatible implicit declaration of built-in function «fprintf"
modem_main.c:886: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:890: erreur: storage size of «prm" isn"t known
modem_main.c:891: attention : implicit declaration of function «mlockall"
modem_main.c:891: erreur: «MCL_CURRENT" undeclared (first use in this function)
modem_main.c:891: erreur: «MCL_FUTURE" undeclared (first use in this function)
modem_main.c:892: erreur: «errno" undeclared (first use in this function)
modem_main.c:892: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:894: attention : implicit declaration of function «sched_get_priority_max"
modem_main.c:894: erreur: «SCHED_FIFO" undeclared (first use in this function)
modem_main.c:895: attention : implicit declaration of function «sched_setscheduler"
modem_main.c:896: attention : format «%s" expects type «char *", but argument 3 has type «int"
modem_main.c:890: attention : unused variable «prm"
modem_main.c:901: attention : implicit declaration of function «signal"
modem_main.c:901: erreur: «SIGINT" undeclared (first use in this function)
modem_main.c:902: erreur: «SIGTERM" undeclared (first use in this function)
modem_main.c:915: attention : implicit declaration of function «usleep"
modem_main.c:928: attention : incompatible implicit declaration of built-in function «exit"
modem_main.c:851: attention : unused variable «path_name"
make[1]: *** [modem_main.o] Erreur 1
make[1]: quittant le répertoire « /home/ismailsrt4400/m/slmodem-2.9.10/modem »
make: *** [modem] Erreur 2
ismailsrt4400@ismailsrt4400-laptop:~/m/slmodem-2.9.10$ 
im waiting for ur reply as soon as possible

---

### Post by oldsoundguy on 2007-12-22
brand of modem and type?  External/internal?   Lots of WinModems have NO support, and rightfully so as they use both memory and processor space.  I have been using some form of Linux for about 6 years and the first thing I did was buy an external modem (com port).  I STILL am using that modem as a back up to my cable! (even though their service SUX, USRobotics makes an excellent external that is built like a tank!)

---

### Post by ismailsrt4400 on 2007-12-23
Thank u for ur reply
the modem is internel and in laptop
type smart link 56k modem HAMR5600
thnx a lot

---

