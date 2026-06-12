---
title: "Kernel compile error"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by digitalpirate on 2008-08-01
I am trying to compile a custom kernel but i get the following error

```
<built-in>:0: fatal error: when writing output to /tmp/ccpMLFJO.s: No space left on device
compilation terminated.
make[1]: *** [.tmp_kallsyms1.o] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.26'
make: *** [debian/stamp-build-kernel] Error 2
```

Which probably means that I don't have enough free diskspace, so I remove some crap and I now have 3.5gb of free space on / but I still get the same error.

```
df -l 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             17425512  11787100   4753232  72% /
varrun                  516980       120    516860   1% /var/run
varlock                 516980         0    516980   0% /var/lock
udev                    516980        56    516924   1% /dev
devshm                  516980        24    516956   1% /dev/shm
lrm                     516980     39776    477204   8% /lib/modules/2.6.24-20-generic/volatile
/dev/sda1             18426520  13345720   5080800  73% /media/sda1
/dev/sda4             20474808  15651072   4823736  77% /media/sda4
overflow                  1024       136       888  14% /tmp
```

---

### Post by logos34 on 2008-08-01
if you're using the make-kpkg command, try prefacing it with this:

[B]INSTALL_MOD_STRIP=1
[/B]
[http://ubuntuforums.org/showpost.php?p=5293754&postcount=2](http://ubuntuforums.org/showpost.php?p=5293754&postcount=2)
[http://ubuntuforums.org/showpost.php?p=5479449&postcount=16](http://ubuntuforums.org/showpost.php?p=5479449&postcount=16)

I went from a 2.4 GB 'linux-2.6.26' folder down to ~ half a gig when I re-ran the build

---

