---
title: "fatal error: X11/Xaw/StripChart.h"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by vevin1986 on 2012-09-21
Hi Guys,
I need to install a software called Advanced FullScreen Debugger for Assembly code debugging but while installation I am getting this error..Please help me..I checked online but couldn't find any information related to this error.When I run make, I get this error


gcc -DHAVE_CONFIG_H -I. -I../../../.. -I../../.. -I../../common -I../common -I../../../init_afd -I../../../statistics -I../mafd_ctrl    -g -O2 -DLINUX -MT afd_load.o -MD -MP -MF .deps/afd_load.Tpo -c -o afd_load.o afd_load.c
afd_load.c:61:32: fatal error: X11/Xaw/StripChart.h: No such file or directory
compilation terminated.
make[5]: *** [afd_load.o] Error 1
make[5]: Leaving directory `/home/vevin1986/Downloads/afd-1.4.4-2/src/UI/Motif/afd_load'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/vevin1986/Downloads/afd-1.4.4-2/src/UI/Motif'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/vevin1986/Downloads/afd-1.4.4-2/src/UI'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/vevin1986/Downloads/afd-1.4.4-2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vevin1986/Downloads/afd-1.4.4-2'
make: *** [all] Error 2

---

### Post by dino99 on 2012-09-21
you already know what is wrong : 

X11/Xaw/StripChart.h: No such file or directory

i does not know what you have not installed to get that header, or if only the path is wrong, or if lower/uppercase have not been respected, or if you does not have read the app's doc. But it seems to me like a basic error.

---

