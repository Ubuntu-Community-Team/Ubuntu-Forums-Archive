---
title: "timer_list has no member named ‘data’"
date: 2018-03-08
forum: Installation &amp; Upgrades
---

### Post by magudelo58 on 2018-03-08
Unable to compile driver rtl8812au after upgrade to 4.15.0-10-generic.

This is the result of the make:[INDENT][/INDENT]
[INDENT=2]magudelo58@lubuntu:~/rtl8812au$ make[/INDENT]
[INDENT=2]make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.15.0-10-generic/build M=/home/magudelo58/rtl8812au  modules[/INDENT]
[INDENT=2]make[1]: Entering directory '/usr/src/linux-headers-4.15.0-10-generic'[/INDENT]
[INDENT=2]  CC [M]  /home/magudelo58/rtl8812au/core/rtw_cmd.o[/INDENT]
[INDENT=2]In file included from /home/magudelo58/rtl8812au/include/osdep_service.h:41:0,[/INDENT]
[INDENT=2]                 from /home/magudelo58/rtl8812au/include/drv_types.h:32,[/INDENT]
[INDENT=2]                 from /home/magudelo58/rtl8812au/core/rtw_cmd.c:22:[/INDENT]
[INDENT=2]/home/magudelo58/rtl8812au/include/osdep_service_linux.h: In function ‘_init_timer’:[/INDENT]
[INDENT=2]/home/magudelo58/rtl8812au/include/osdep_service_linux.h:257:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’[/INDENT]
[INDENT=2]  ptimer->data = (unsigned long)cntx;[/INDENT]
[INDENT=2]        ^~[/INDENT]
[INDENT=2]/home/magudelo58/rtl8812au/include/osdep_service_linux.h:258:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration][/INDENT]
[INDENT=2]  init_timer(ptimer);[/INDENT]
[INDENT=2]  ^~~~~~~~~~[/INDENT]
[INDENT=2]  _init_timer[/INDENT]
[INDENT=2]cc1: some warnings being treated as errors[/INDENT]
[INDENT=2]scripts/Makefile.build:316: recipe for target '/home/magudelo58/rtl8812au/core/rtw_cmd.o' failed[/INDENT]
[INDENT=2]make[2]: *** [/home/magudelo58/rtl8812au/core/rtw_cmd.o] Error 1[/INDENT]
[INDENT=2]Makefile:1537: recipe for target '_module_/home/magudelo58/rtl8812au' failed[/INDENT]
[INDENT=2]make[1]: *** [_module_/home/magudelo58/rtl8812au] Error 2[/INDENT]
[INDENT=2]make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-10-generic'[/INDENT]
[INDENT=2]Makefile:1052: recipe for target 'modules' failed[/INDENT]
[INDENT=2]make: *** [modules] Error 2[/INDENT]

lsb_release -a
[INDENT=2]No LSB modules are available.[/INDENT]
[INDENT=2]Distributor ID:	Ubuntu[/INDENT]
[INDENT=2]Description:	Ubuntu Bionic Beaver (development branch)[/INDENT]
[INDENT=2]Release:	18.04[/INDENT]
[INDENT=2]Codename:	bionic[/INDENT]



uname -r
[INDENT=2]4.15.0-10-generic[/INDENT]

---

