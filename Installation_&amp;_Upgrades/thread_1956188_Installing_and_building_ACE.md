---
title: "Installing and building ACE"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by tanvi123 on 2012-04-10
I have run the autoconf  -f command and automake command too..../conig also gave the message that ACE has been configured.
no errors were given..
however on running the make command the following errors were obtained..
make[2]: Entering directory `/home/tanvi/Desktop/ACE_wrappers/build/examples/Threads'
g++ -DHAVE_CONFIG_H   -I../../.. -I../..   -W -Wall -Wpointer-arith  -g -O2 -pthread -pipe -O3 -I. -I.. -MT auto_event-auto_event.o -MD -MP -MF .deps/auto_event-auto_event.Tpo -c -o auto_event-auto_event.o `test -f 'auto_event.cpp' || echo '../../../examples/Threads/'`auto_event.cpp
../../../examples/Threads/auto_event.cpp:28:72: fatal error: /home/tanvi/Desktop/ACE_ROOT/ACE_wrappers/ace/OS_NS_unistd.h: No such file or directory
compilation terminated.
make[2]: *** [auto_event-auto_event.o] Error 1
make[2]: Leaving directory `/home/tanvi/Desktop/ACE_wrappers/build/examples/Threads'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tanvi/Desktop/ACE_wrappers/build/examples'
make: *** [all-recursive] Error 1
 Any solution??

---

