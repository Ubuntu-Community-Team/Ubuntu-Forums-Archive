---
title: "[SOLVED] can't get madwifi to install"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by dodgeman79 on 2007-08-26
trying to get madwifi to install but am getting a few errors.
```
baker@ubuntu:~/Desktop/madwifi-0.9.3.2$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/baker/Desktop/madwifi-0.9.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/baker/Desktop/madwifi-0.9.3.2/ath/if_ath.o
  CC [M]  /home/baker/Desktop/madwifi-0.9.3.2/ath/if_ath_pci.o
  LD [M]  /home/baker/Desktop/madwifi-0.9.3.2/ath/ath_pci.o
  CC [M]  /home/baker/Desktop/madwifi-0.9.3.2/ath_hal/ah_os.o
  HOSTCC  /home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c: At top level:
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c: In function 'main':
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/baker/Desktop/madwifi-0.9.3.2/ath_hal/uudecode] Error 1
make[2]: *** [/home/baker/Desktop/madwifi-0.9.3.2/ath_hal] Error 2
make[1]: *** [_module_/home/baker/Desktop/madwifi-0.9.3.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2
baker@ubuntu:~/Desktop/madwifi-0.9.3.2$ 

```

---

### Post by dodgeman79 on 2007-08-27
anyone?  I've tried google and did a search here, but nothing beneficial comes up.

---

### Post by dodgeman79 on 2007-08-27
i got it to install from this thread [http://ubuntuforums.org/showthread.php?t=536514](http://ubuntuforums.org/showthread.php?t=536514)

I was missing this
```
sudo aptitude install build-essential
```

---

### Post by DaNgLe666 on 2007-11-22
I have got version 7.10 of Ubuntu, its fully updated, and has the build essentials But still comes up with same error as above when trying to " sudo make"

This is really frustrating..lol

anyone have any other suggestions?

---

### Post by DaNgLe666 on 2007-11-22
nvm I recovered then updated its fine now, ust gotta learn how to use airodump

---

