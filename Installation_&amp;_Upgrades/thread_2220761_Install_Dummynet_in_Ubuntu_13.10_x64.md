---
title: "Install Dummynet in Ubuntu 13.10 x64"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by tiena2cva on 2014-04-29
[COLOR=#000000][FONT=Arial]Hi all,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am new to Ubuntu and Linux.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I try install Dummynet on my laptop. My laptop use Ubuntu 13.10 x64.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am folowing this post: [/FONT][/COLOR][http://ubuntuforums.org/showthread.php?t=1337587](http://ubuntuforums.org/showthread.php?t=1337587)
[COLOR=#000000][FONT=Arial]But when I compile it, it have some error:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```


```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Consolas]tiena2cva@tiena2cva-linux:~/Downloads/ipfw3-2012$ make
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[1]: Entering directory `/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod'
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]Makefile:282:  
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[1]: Leaving directory `/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod'
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[1]: Entering directory `/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod'
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]Makefile:282:  
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make -C /lib/modules/3.11.0-20-generic/build V= M=`pwd` modules
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[2]: Entering directory `/usr/src/linux-headers-3.11.0-20-generic'
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/Makefile:282:  
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_fw2.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_fw_pfil.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_fw_sockopt.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_fw_dynamic.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_fw_table.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_fw_log.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/radix.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/in_cksum.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]CC [M]  /home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_dummynet.o
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]In file included from <command-line>:0:0:
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_dummynet.c: In function ‘fsk_detach’:
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_dummynet.c:638:19: error: argument to     ‘sizeof’ in ‘memset’ call is the same expression as the destination; did you mean to    dereference it? [-Werror=sizeof-pointer-memaccess]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]bzero(fs, sizeof(fs)); /* safety */
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]              ^
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/missing.h:138:34: note: in definition of macro ‘bzero’
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]#define bzero(s, n) memset(s, 0, n)
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]                             ^
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]cc1: all warnings being treated as errors
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[3]: *** [/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod/ip_dummynet.o] Error 1
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[2]: *** [_module_/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod] Error 2
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[2]: Leaving directory `/usr/src/linux-headers-3.11.0-20-generic'
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[1]: *** [kipfw] Error 2
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make[1]: Leaving directory `/home/tiena2cva/Downloads/ipfw3-2012/kipfw-mod' 
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]make: *** [kipfw] Error 2[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]I need you help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thank you.[/FONT][/COLOR]

---

