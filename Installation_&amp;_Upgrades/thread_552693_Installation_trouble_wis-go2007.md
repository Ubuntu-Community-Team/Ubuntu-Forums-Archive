---
title: "Installation trouble: wis-go2007"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by tipdrinker on 2007-09-16
Ok ive been trying to install  wis-go2007 all night and my latest problem is that when i go to make it says this...

kev@89-125-52-231:~/Desktop/vpnclient$ cd /home/kev/wis-go7007-linux-0.9.8
kev@89-125-52-231:~/wis-go7007-linux-0.9.8$ make

***** Using kernel source in /usr/src/linux-headers-2.6.20-16-lowlatency *****

make modules -C /usr/src/linux-headers-2.6.20-16-lowlatency M=/home/kev/wis-go7007-linux-0.9.8/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-lowlatency'
  CC [M]  /home/kev/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o
/home/kev/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:20:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/kev/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o] Error 1
make[1]: *** [_module_/home/kev/wis-go7007-linux-0.9.8/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-lowlatency'
make: *** [all] Error 2
kev@89-125-52-231:~/wis-go7007-linux-0.9.8$ 



?????????????????????????????????:confused:

---

### Post by tipdrinker on 2007-09-17
bump

---

