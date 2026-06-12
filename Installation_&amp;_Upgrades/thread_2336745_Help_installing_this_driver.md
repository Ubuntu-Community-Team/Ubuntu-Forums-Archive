---
title: "Help installing this driver"
date: 2016-09-10
forum: Installation &amp; Upgrades
---

### Post by DrRus on 2016-09-10
Hi guys,

i'm trying to install an USB-to-Serial driver located here: [https://www.tripplite.com/support/U209000R](https://www.tripplite.com/support/U209000R) 

The file comes with 3 Linux folders, each for a RedHat version. regardless of which one I run I always get error. According to the Readme.txt file, all I have to do is run ```
make inst
```, but when I do - this is what I get:

```

gcc -D__KERNEL__ -I/usr/src/linux-2.4/include -I/usr/src/linux-2.4/drivers/usb/serial   -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -Wno-unused  -DMODULE -c pl2303.c
pl2303.c:33:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
Makefile:45: recipe for target 'pl2303.o' failed
make: *** [pl2303.o] Error 1

```

Any and all help would be greatly appreciated!

---

### Post by yancek on 2016-09-10
Did you look in the extracted folders and see that this software is for use with three VERY old versions of Red Hat Linux?  The software is dated/written in 2002.  

Also the command would be:  make install  maybe that was a typo?  I wouldn't hold out much hope for it working on a current Ubuntu or any current Linux but maybe someone else will have some ideas.

---

### Post by DrRus on 2016-09-11
yancek - "make install" doesn't work, it gives me the following:

```
make: *** No rule to make target 'install'.  Stop.
```

I realize the drivers are old, but are the only ones available. I had no problem installing the old Windows 2000 drivers on a Win 10 machine :P

Very frustrating...

---

### Post by wildmanne39 on 2016-09-11
This is not windows it is way to old to work on a modern linux machine.

The driver would have to be completely rewritten for a new ubuntu version to be able to work.

---

