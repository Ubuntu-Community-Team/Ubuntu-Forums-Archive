---
title: "autoconf.sh missing"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by think_tough on 2010-12-04
Hi All,

I have installed Ubuntu 10.10 recently, and the kernel version is 2.6.35-23-generic. I am not able to locate autoconf.h file in my /usr/src/linux/headers-2.6.35-23-generic/include/linux folder. 

I tried installing autoconf package using "apt-get install autoconf" command too, but I did not see that file in the above location after the install. Can someone please tell me where I can find this file?


Thanks!

---

### Post by dino99 on 2010-12-04
hm,
i never wondered about that :)

what is your goal/target

---

### Post by think_tough on 2010-12-04
I was trying to compile one program which has dependency on the existence of this file. Its giving me the following error coz this file is not present -


> 
Making module
make -C /lib/modules/2.6.35-23-generic/build SUBDIRS=/home/preethi/Downloads/testvpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/preethi/Downloads/testvpn/vpnclient/linuxcniapi.o
/home/preethi/Downloads/testvpn/vpnclient/linuxcniapi.c:14: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/preethi/Downloads/testvpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/preethi/Downloads/testvpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [default] Error 2


---

### Post by Rebootkid on 2010-12-14
What worked for me:
[http://www.uluga.ubuntuforums.org/showthread.php?t=772692&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=772692&page=2)

Scroll to post 13.

---

