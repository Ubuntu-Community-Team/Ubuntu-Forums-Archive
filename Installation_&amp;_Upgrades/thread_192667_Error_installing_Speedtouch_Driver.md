---
title: "Error installing Speedtouch Driver"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by LinuxQ on 2006-06-09
Hello ,
I tried to install speedtouch driver on UBUNTU but when I type **make** in the Terminal I get :
```
cd src && make
make[1]: Entering directory `/home/abd/speedtouch-1.3/src'
gcc -Wall -I. -I/usr/local/include -I/usr/include -O2 -DUSE_SYSLOG -DVERSION=\"1.3\" -c modem_run.c
modem_run.c:94: error: static declaration of â&#8364;&#1705;verboseâ&#8364;&#8482; follows non-static declaration
modem.h:42: error: previous declaration of â&#8364;&#1705;verboseâ&#8364;&#8482; was here
modem_run.c: In function â&#8364;&#1705;get_referenceâ&#8364;&#8482;:
modem_run.c:787: warning: pointer targets in passing argument 6 of â&#8364;&#1705;pusb_control_msgâ&#8364;&#8482; differ in signedness
modem_run.c: In function â&#8364;&#1705;reportâ&#8364;&#8482;:
modem_run.c:1226: warning: pointer targets in passing argument 1 of â&#8364;&#1705;dumpâ&#8364;&#8482; differ in signedness
modem_run.c: In function â&#8364;&#1705;dumpâ&#8364;&#8482;:
modem_run.c:1287: warning: pointer targets in passing argument 1 of â&#8364;&#1705;sprintfâ&#8364;&#8482; differ in signedness
modem_run.c:1296: warning: pointer targets in passing argument 1 of â&#8364;&#1705;sprintfâ&#8364;&#8482; differ in signedness
modem_run.c:1305: warning: pointer targets in passing argument 1 of â&#8364;&#1705;sprintfâ&#8364;&#8482; differ in signedness
modem_run.c:1314: warning: pointer targets in passing argument 2 of â&#8364;&#1705;syslogâ&#8364;&#8482; differ in signedness
make[1]: *** [modem_run.o] Error 1
make[1]: Leaving directory `/home/abd/speedtouch-1.3/src'
make: *** [modem] Error 2

```

---

