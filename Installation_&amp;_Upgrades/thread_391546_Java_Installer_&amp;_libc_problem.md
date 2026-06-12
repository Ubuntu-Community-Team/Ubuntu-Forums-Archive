---
title: "Java Installer &amp; libc problem"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by io78 on 2007-03-23
Hi,

I have some problem when i run some my applications installer (InstallAnywhere).

When i run i receive this error

```

luca@luca-laptop:~/babv$ ./setup.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6169/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

I looking for these file and i find into /lib directory :confused:
```

luca@luca-laptop:/lib$ ls -l | egrep "(libc.so.*|librt.so.*|libm.so.*|libpthread.so.*)"
lrwxrwxrwx  1 root root      11 2007-03-22 23:17 libc.so.6 -> libc-2.4.so
lrwxrwxrwx  1 root root      11 2007-03-22 23:17 libm.so.6 -> libm-2.4.so
lrwxrwxrwx  1 root root      17 2007-03-22 23:17 libpthread.so.0 -> libpthread-2.4.so
lrwxrwxrwx  1 root root      12 2007-03-22 23:17 librt.so.1 -> librt-2.4.so

```

Somebody have some solution??

Best regards
Luca

sorry for bad english ;)

---

### Post by io78 on 2007-03-23
Ok i run these istructions and all work

luca@luca-laptop:~/babv$ cp setup.bin setup.bin.bak
luca@luca-laptop:~/babv$ cat setup.bin.bak  | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > setup.bin


Tks :)

---

